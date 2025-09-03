#linux #Linux/内核（Linux_Kernel） #GNU软件
# 升级事前准备
1. glibc安装源码，下载于[GNU官方FTP](https://ftp.gnu.org/gnu/glibc/)

# 解压glibc-2.23源码并根据INSTALL文件指示编译

## 编译期间遇到的问题
### 软件版本依赖
遇到了gawk，gcc版本过低的问题，于是去ftp下载了高版本的对应软件并安装，Glibc编译具体的依赖在INSTALL文件里都有详细说明 

```shell
tar -xvf 
```
### 执行configure时提示LD_LIBRARY_PATH 不能包含当前目录
![[glibc_waring.png]]
打印LD_LIBRARY_PATH值发现如下

```shell
echo $LD_LIBRARY_PATH
/usr/local/lib:/usr/lib:/lib:

```
一开始觉得不解：这个里面并没有我的当前目录，为什么会报错呢？然后在网上查询类似问题的时候看到一位说到：
“It turns out that an empty entry in LD_LIBRARY_PATH is converted into the current directory. Good to know!”[链接地址](https://blog.joshumax.me/general/2017/06/08/how-torch-broke-ls.html)
我意识到原来是最后带上的：导致了LD_LIBRARY_PATH中带有一个空值，从而包含到了当前目录，于是我将LD_LIBRARY_PATH修改为/usr/local/lib:/usr/lib:/lib，再次configure就通过了，没有出问题