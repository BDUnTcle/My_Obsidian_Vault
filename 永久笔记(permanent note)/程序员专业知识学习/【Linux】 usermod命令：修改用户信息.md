#Linux/linux命令笔记 
前面章节介绍了如何利用 useradd 命令添加用户，但如果不小心添错用户信息，后期如何修改呢？

办法有两个，一个是使用 Vim 文本编辑器手动修改涉及用户信息的相关文件（/etc/passwd、/etc/shadow、/etc/group、/etc/gshadow），另一个方法就是使用本节介绍了 usermod 命令，该命令专门用于修改用户信息。

这里一定要分清 useradd 命令和 usermod 命令的区别，前者用于添加用户，当然，添加用户时可以对用户信息进行定制；后者针对与已存在的用户，使用该命令可以修改它们的信息。

usermod 命令的基本格式如下：


```shell
[root@localhost ~]# usermod [选项] 用户名
```


选项：

-   \-c 用户说明：修改用户的说明信息，即修改 /etc/passwd 文件目标用户信息的第 5 个字段；
-   \-d 主目录：修改用户的主目录，即修改 /etc/passwd 文件中目标用户信息的第 6 个字段，需要注意的是，主目录必须写绝对路径；
-   \-e 日期：修改用户的失效曰期，格式为 "YYYY-MM-DD"，即修改 /etc/shadow 文件目标用户密码信息的第 8 个字段；
-   \-g 组名：修改用户的初始组，即修改 /etc/passwd 文件目标用户信息的第 4 个字段（GID）；
-   \-u UID：修改用户的UID，即修改 /etc/passwd 文件目标用户信息的第 3 个字段（UID）；
-   \-G 组名：修改用户的附加组，其实就是把用户加入其他用户组，即修改 /etc/group 文件；
-   \-l 用户名：修改用户名称；
-   \-L：临时锁定用户（Lock）；
-   \-U：解锁用户（Unlock），和 -L 对应；
-   \-s shell：修改用户的登录 Shell，默认是 /bin/bash。

如果你仔细观察会发现，其实 usermod 命令提供的选项和 useradd 命令的选项相似，因为 usermod 命令就是用来调整使用 useradd 命令添加的用户信息的。

不过，相比 useradd 命令，usermod 命令还多出了几个选项，即 -L 和 -U，作用分别与 passwd 命令的 -l 和-u 相同。需要注意的是，并不是所有的 Linux 发行版都包含这个命令，因此，使用前可以使用 man usermod 命令确定系统是否支持。

此命令对用户的临时锁定，同 passwd 命令一样，都是在 /etc/passwd 文件目标用户的加密密码字段前添加 "!"，使密码失效；反之，解锁用户就是将添加的 "!" 去掉。

接下来，给大家分别讲解 usermod 命令几个选项的具体用法。

【例 1】

# 锁定用户  
\[root@localhost ~\]# usermod -L lamp  
\[root@localhost ~\]# grep "lamp" /etc/shadow  
lamp:!$6$YrPj8g0w$ChRVASybEncU24hkYFqxREH3NnzhAVDJSQLwRwTSbcA2N8UbPD9bBKVQSky xlaMGs/Eg5AQwO.UokOnKqaHFa/:15711:0:99999:7:::  
# 其实锁定就是在密码字段前加入"!"，这时lamp用户就暂时不能登录了

# 解锁用户  
\[root@localhost ~\]# usermod -U lamp  
\[root@localhost ~\]# grep "lamp" /etc/shadow  
lamp:$6$YrPj8g0w$ChRVASybEncU24hkYFqxREH3NnzhAVDJSQLwRwTSbcA2N8UbPD9bBKVQSkyx laMGs/Eg5AQwO.UokOnKqaHFa/:15711:0:99999:7:::  
# 取消了密码字段前的 "!"

【例 2】

# 把lamp用户加入root组  
\[root@localhost ~\]# usermod -G root lamp  
\[root@localhost ~\]# grep "lamp" /etc/group  
root:x:0:lamp  
# lamp用户已经加入了root组  
lamp:x:501:

【例 3】

# 修改用户说明  
\[root@localhost ~\]# usermod -c "test user" lamp   
\[root@localhost ~\]# grep "lamp" /etc/passwd  
lamp:x:501:501:test user:/home/lamp:/bin/bash  
# 查看一下，用户说明已经被修改了