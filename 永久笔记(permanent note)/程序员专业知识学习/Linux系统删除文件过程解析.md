#Linux/ext文件系统 #Linux/linux文件系统 #linux #Linux/内核（Linux_Kernel）

摘录于“[Linux系统删除文件过程解析](https://cloud.tencent.com/developer/article/1143433)”
# 1. 概述

___

**当我们执行rm命令删除一个文件的时候，在操作系统底层究竟会发生些什么事情呢**，带着这个疑问，我们在Linux-3.10.104内核下对ext4文件系统下的rm操作进行分析。rm命令本身比较简单，但其在内核底层涉及到VFS操作、ext4块管理以及日志管理等诸多细节。

# 2. 源码分析

___

rm命令是GNU coreutils里的一个命令，在对一个文件进行删除时，**它实际上调用了Linux的*unlink*系统调用**，***unlink*系统调用**在内核中的定义如下：

```
SYSCALL_DEFINE1(unlink, const char __user *, pathname) 
{
  return do_unlinkat(AT_FDCWD, pathname); 
}
```

*do\_unlinkat*的第一个参数 fd值为*AT\_FDCWD*时，pathname就是相对路径，用于删除当前工作目录下的文件，若pathname为绝对路径，则fd直接被忽略。接下来我们将会对do\_unlinkat中一些重点函数做以详细分析。

```
static long do_unlinkat(int dfd, const char __user *pathname)
{
    int error;
    struct filename *name;
    struct dentry *dentry;
    struct nameidata nd;
    struct inode *inode = NULL;
    unsigned int lookup_flags = 0;
retry:
    name = user_path_parent(dfd, pathname, &nd, lookup_flags);
    if (IS_ERR(name))
        return PTR_ERR(name);

    error = -EISDIR;
    if (nd.last_type != LAST_NORM)
        goto exit1;

    nd.flags &= ~LOOKUP_PARENT;
    error = mnt_want_write(nd.path.mnt);
    if (error)
        goto exit1;

    mutex_lock_nested(&nd.path.dentry->d_inode->i_mutex, I_MUTEX_PARENT);
    dentry = lookup_hash(&nd);
    error = PTR_ERR(dentry); 
     if (!IS_ERR(dentry)) {
         /* Why not before? Because we want correct error value */ 
         if (nd.last.name[nd.last.len])
             goto slashes;
         inode = dentry->d_inode;
         if (!inode)
             goto slashes;
         ihold(inode);
         error = security_path_unlink(&nd.path, dentry);
         if (error)
             goto exit2;
         error = vfs_unlink(nd.path.dentry->d_inode, dentry);
exit2:
         dput(dentry); 
     }
     mutex_unlock(&nd.path.dentry->d_inode->i_mutex);
     if (inode)
         iput(inode);    /* truncate the inode here */        
     ... 
}
```

为了便于理解，这里简要介绍一下索引节点inode、目录项dentry以及目录项缓存dcache这几个重要概念，更具体的内容可参考Linux内核分析的相关书籍，如Robert Love的《Linux内核设计与实现》一书。

-   **inode** 包含了与文件本身相关的信息，如文件大小、访问权限、MAC time等。
-   **dentry(directory entry)** 包含了文件管理与组织的的信息，一方面它建立了文件名到inode的映射关系(有硬链接时为多对一关系)，另一方面依靠其d\_parent和d\_child成员形成文件系统的目录树结构。
-   dcache是为了加快VFS查找文件或目录建立的，如果内核每次查找文件都要逐层遍历目录，那么将会浪费很多时间，这时候如果在访问dentry时将其缓存起来，那么此后访问就会快很多。

回到正题，首先在lookup\_hash函数中，我们根据文件路径从目录项缓存dcache中查找对应的目录项dentry，然后根据dentry->d\_inode找到对应的inode。

接下来调用vfs\_unlink函数，这个函数实际干了两件事，一是调用inode->i\_op->unlink，i\_op是inode数据结构中定义的inode\_operations类型的成员，它描述了VFS操作inode的所有方法，在这个结构体中定义了一组函数指针，所以在ext4文件系统中,inode->i\_op->unlink实际上调用了ext4\_unlink这一函数。vfs\_unlink干的另一件事是调用d\_delete，这一函数的作用是当目录项的引用计数变为0即没有进程在使用该目录项时，将目录项从dcache中删除。 再往下走，dput函数将dentry->d\_count引用计数减1，如果不为0，则直接返回；否则接着判断dentry是否从dcache的哈希链上删除，如果是，则可以释放dentry对应的inode；如果不是，则表明dentry对应的inode没有被释放，此时可以将该dentry加入到detry\_unused这一LRU队列中。(注：dput函数以及vfs\_unlink这两个函数涉及到的操作较为繁杂，本文没有详细展开，具体内容可参考dentry inode引用计数）。

接下来的iput函数作用就是就是释放inode，其调用路径为：

```
iput()-->iput_final()-->generic_drop_inode()                     
                    |-->inode_lru_list_del()
                    |-->evict()
```

generic\_drop\_inode函数中，通过inode->i\_nlink硬链接计数的值来判断inode是否可以被删除。inode\_lru\_list\_del将inode从LRU链表中删除，而evict则是真正地释放inode的操作，其调用路径为：

```
evict()-->ext4_evict_inode()-->ext4_truncate()-->ext4_ext_truncate()-->ext4_ext_remove_space()-->ext4_ext_rm_leaf()-->ext4_free_blocks()
```

（注：本文对一些函数的调用路径没有全部展开，只对一些关键路径加以描述，要想获得内核调用链上的全部信息，推荐使用Brendangregg开源的perf-tool中的funcgraph工具）

我们可以看到ext4\_ext\_truncate、ext4\_ext4\_remove\_space以及ext4\_ext\_rm\_leaf这三个函数名中间都有一个ext，其实就是extent，也就是说这三个函数都是操作extent的函数，而真正释放块是在ext4\_free\_blocks中。

*EXT4文件系统*相比于*EXT2、EXT3*等文件系统的一个最大的区别就是，EXT4采用extent而非间接块指针(indirect block pointer)来管理磁盘块。EXT4的inode大小为256字节，40-99这60个字节在EXT2、EXT3文件系统中用来保存间接块指针(12个直接指针和3个间接指针)，而现在用来保存extent信息，其中40-51字节为extent头部信息，保存了魔数、extent个数以及深度等信息：

```
struct ext4_extent_header
{
    __le16 eh_magic; /* probably will support different formats */
    __le16 eh_entries; /* number of valid entries */
    __le16 eh_max; /* capacity of store in entries */
    __le16 eh_depth; /* has tree real underlying blocks? */
    __le32 eh_generation; /* generation of the tree */ 
};
```

52~99这48个字节用来保存extent或者extent index信息，extent和extent index结构均为12个字节:

```
struct ext4_extent
{
    __le32 ee_block;
    __le16 ee_len;
    __le16 ee_start_hi;
    __le32 ee_start_lo; 
};
struct ext4_extent_idx
{
    __le32 ei_block;
    __le32 ei_leaf_lo;
    __le16 ei_leaf_hi;
    __u16 ei_unused;
};
```

ext4\_extent代表一组连续的块，ee\_block为逻辑块号，ee\_len代表extent中有多少个块，其最高位与ext4的预分配策略特性有关，所以一个extent最多能存2^15个块，由于物理块大小为4k，即可以存储128M的数据，ee\_start\_hi和ee\_start\_lo组成了物理块地址。

当文件较小时(<512M，即4个extent能存储的数据大小)，完全可以用extent来保存块信息，但当文件较大时，就不得不借助ext4\_extent\_idx 这个中间结构来索引下一级结点，此时ext4\_extent\_header中保存的eh\_depth就不为0了。ei\_leaf\_lo与ei\_leaf\_hi组合起来构成下一级节点的物理块号。所以对于大文件来说，通过inode找到index结点，进而找到叶子结点，最终通过叶子结点中存储的extent来找到实际的磁盘物理块。整个extent tree的结构如下图所示：

回到evict函数的调用路径上，ext4\_ext\_rm\_leaf用来释放叶子结点中extent及其相关的物理块，start和end参数用来指定起始和终止的逻辑块号，例如start=1, end=4代表第一个到第四个extent。

```
static int
ext4_ext_rm_leaf(handle_t *handle, struct inode *inode,
                 struct ext4_ext_path *path,
                 ext4_fsblk_t *partial_cluster, 
                 ext4_lblk_t start, ext4_lblk_t end)
```

实际的释放块操作是在ext4\_free\_blocks中，block参数指定了要释放的起始物理块号，count指定要释放的块数目。

```
void ext4_free_blocks(handle_t *handle,
                      struct inode *inode,
                      struct buffer_head *bh,
                      ext4_fsblk_t block,
                      unsigned long count,
                      int flags)
```

值得注意的是，**释放块并不是真正地从介质中擦除数据，而是将这些块对应的位从块位图(block bitmap)中清除掉**。另外，ext4\_free\_blocks需要更新quota（磁盘配额）信息。其调用路径为：

```
ext4_free_blocks()-->mb_clear_bits()
                 |-->dquot_free_block()-->dquot_free_space_nodirty()-->__dquot_free_space()-->inode_sub_bytes()
                                      |-->mark_inode_dirty_sync()-->__mark_inode_dirty()
```

dquot\_free\_block里做的两件事情分别是：

1.  调用dquot\_free\_space\_nodirty，该函数内联展开为\_\_dquot\_free\_space并最终调用inode\_sub\_bytes更新inode的两个成员i\_blocks和i\_bytes。
2.  调用mark\_inode\_dirty\_sync将inode标记为脏(因为第一步对inode做了修改)，在ext4中执行该函数将会对日志进行更新。该函数内联展开为\_\_mark\_inode\_dirty(inode, I\_DIRTY\_SYNC)，I\_DIRTY\_SYNC表示要进行同步操作。

```
void __mark_inode_dirty(struct inode *inode, int flags)
{
    struct super_block *sb = inode->i_sb; 
    struct backing_dev_info *bdi = NULL;    
    if (flags & (I_DIRTY_SYNC | I_DIRTY_DATASYNC)) {     
        trace_writeback_dirty_inode_start(inode, flags);      
        if (sb->s_op->dirty_inode)       
            sb->s_op->dirty_inode(inode, flags);      
        trace_writeback_dirty_inode(inode, flags);   
    }   
    ...
```

如果设置了I\_DIRTY\_SYNC标志，则在\_\_mark\_inode\_dirty函数中会通过函数指针dirty\_inode调用文件系统特有的操作，在EXT4文件系统下，相应的函数为ext4\_dirty\_inode，该函数会启动一个日志原子操作将应该同步的inode元数据向jdb2日志模块提交。

```
void ext4_dirty_inode(struct inode *inode, int flags) 
{   
    handle_t *handle;    
    handle = ext4_journal_start(inode, EXT4_HT_INODE, 2);   
    if (IS_ERR(handle))     
        goto out;  
    ext4_mark_inode_dirty(handle, inode);   
    ext4_journal_stop(handle); 
out:
    return;  
}
```

ext4\_dirty\_inode函数中做了三件事：

1.  ext4\_journal\_start判断日志执行状态并调用jbd2\_\_journal\_start来启用日志handle;
2.  ext4\_mark\_inode\_dirty会调用ext4\_get\_inode\_loc函数来根据指定的inode获取inode在磁盘和内存中的位置，然后调用jbd2\_journal\_get\_write\_access获取写日志的权限，接着对inode在磁盘上对应的raw\_inode进行更新，最后调用jbd2\_journal\_dirty\_metadata设置元数据为脏并添加到日志transaction的对应链表中;
3.  ext4\_journal\_stop用来结束此日志handle，这样的话日志的commit进程在被唤醒时将会对这个日志进行提交。

回到\_\_mark\_inode\_dirty函数，该函数接下来会对inode的状态i\_state添加flag标记，如上文所述，此处的flag为I\_DIRTY\_SYNC。

当inode尚未dirty时，还会进行如下操作：

```
     ...
     if (!was_dirty) {
         bool wakeup_bdi = false;          
         bdi = inode_to_bdi(inode);            
         if (bdi_cap_writeback_dirty(bdi)) {              
             WARN(!test_bit(BDI_registered, &bdi->state),                   
                  "bdi-%s not registered\n", bdi->name);                
             if (!wb_has_dirty_io(&bdi->wb))                  
                 wakeup_bdi = true;          
         }            
         spin_unlock(&inode->i_lock);          
         spin_lock(&bdi->wb.list_lock);          
         inode->dirtied_when = jiffies;          
         list_move(&inode->i_wb_list, &bdi->wb.b_dirty);          
         spin_unlock(&bdi->wb.list_lock);            
         if (wakeup_bdi)              
             bdi_wakeup_thread_delayed(bdi);          
         return;     
     }
```

当没有对回写进行限制(bdi\_cap\_writeback\_dirty)，且通过wb\_has\_dirty\_io判断出inode对应的bdi没有正在处理的dirty io时（即dirty list, io list, more io list均为空），我们将wakeup\_bdi设置为true。接下来设置inode的dirty时间，并将inode的i\_wb\_list移到bdi\_writeback的dirty链表(wb.b\_dirty)中。如果wakeup\_bdi为真，则调用bdi\_wakeup\_thread\_delayed将bdi添加到后台的回写队列中，回写队列中的dirty inode会被回写线程定期刷到磁盘，时间间隔由dirty\_writeback\_interval参数决定，默认为5s。

# 3. rm对I/O影响

___

实际上，evict调用链上有诸多地方都包含设置元数据为脏并更新日志这个操作(ext4\_handle\_dirty\_metadata)，例如在ext4\_free\_blocks中还会对存放块位图(block bitmap)的block以及存放块组描述信息(group descriptor)的block进行元数据的dirty操作。由此可知，要删除的文件越大，涉及到的日志更新操作就越频繁，所以直接rm一个大文件时，大量的日志更新操作将会影响到其他进程的I/O性能。如果其他进程是I/O密集型的程序，以[MySQL](https://cloud.tencent.com/product/cdb?from=10680)为例，rm大文件与之同时运行将会使得其QPS降低，响应时间也会增加。 为了验证这点，本文用Sysbench对MySQL进行压测，使用的设备为NVMe接口的SSD，实验分两组：

(1) 只运行Sysbench，测得的平均QPS为205500；

(2) 运行Sysbench的同时对一个400GB的大文件进行rm操作，测得的平均QPS为40485。

由此可见，在对大文件进行删除时，为了避免对其他I/O密集型应用的影响，不应该直接用rm对其删除，而应该采用其他方法。例如，每次将大文件truncate一部分并sleep一段时间，这样的话就可以将删除的I/O负载分散到每次truncate操作，不会出现I/O负载在一段时间内突然增高的现象。

**参考文献**

\[1\] https://www.ibm.com/developerworks/cn/linux/l-cn-usagecounter/ \[2\] https://digital-forensics.sans.org/blog/2010/12/20/digital-forensics-understanding-ext4-part-1-extents \[3\] http://blog.csdn.net/luckyapple1028/article/details/61413724

文章分享自微信公众号：

![](https://open.weixin.qq.com/qr/code?username=gh_83eebc796d5d)

本文参与 [腾讯云自媒体分享计划](https://cloud.tencent.com/developer/support-plan) ，欢迎热爱写作的你一起参与！

如有侵权，请联系

cloudcommunity@tencent.com

删除。