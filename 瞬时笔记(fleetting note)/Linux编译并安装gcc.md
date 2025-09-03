#linux #Linux/内核（Linux_Kernel） #GNU软件
# 解压gcc源码并根据INSTALL文件指示编译
[Install GCC](https://gcc.gnu.org/install/)
[gcc configuration DOC](https://gcc.gnu.org/install/configure.html)
## 编译和安装gcc的步骤
根据GNU官方的指引教程[Installing GCC](https://gcc.gnu.org/install/)，在自己的主机上安装gcc分为以下几步：
1.  [Prerequisites](https://gcc.gnu.org/install/prerequisites.html)
2.  [Downloading the source](https://gcc.gnu.org/install/download.html)
3.  [Configuration](https://gcc.gnu.org/install/configure.html)
4.  [Building](https://gcc.gnu.org/install/build.html)
5.  [Testing](https://gcc.gnu.org/install/test.html) (optional)
6.  [Final install](https://gcc.gnu.org/install/finalinstall.html)
### 1. 下载gcc源码并解压
### 2. 配置GCC（Configuration）
### 3. 编译GCC源码（make）
### 4.运行测试示例
### 5.安装GCC
## 编译期间遇到的问题
### 软件版本依赖
需要更高版本的*gmp* *mpfr* 和 *mpc*

### 编译时Failed 
#### 编译依赖库未找到
make 编译时报出 “configure error cannot compute suffix of object files : cannot compile”和相关库未找到的问题。
对应未找到的库，发现和最新升级的gmp，mpfr，mpc相关。其根本原因为Makefile中对应库的目录未指定。
解决方法为：
1. 在configure中使用对应选项指定其目录名即可

```shell
 --with-gmp=pathname
--with-gmp-include=pathname
--with-gmp-lib=pathname
--with-mpfr=pathname
--with-mpfr-include=pathname
--with-mpfr-lib=pathname
--with-mpc=pathname
--with-mpc-include=pathname
--with-mpc-lib=pathname
```

2. 在进行了步骤1后，发现仍然未解决问题，于是重新安装了gmp，mpfr和mpc这三个库，并更换了较高的版本。并且在安装步骤中的“*make check*”时发现了Fail。检查对应test/log文件发现也是一样的依赖库没找到的问题。其中mpc是依赖于mpfr和gmp的。我在安装是没有指定安装目录，因此它们被安装到了默认的 */usr/local* 的对应目录中。并且在这个目录里可以看到我安装的这些库和对应链接文件。`最后的解决方法为：将LD_LIBRARY_PATH增加/usr/local的目录路径，make distclean之后重新执行configure ，make 。就可以找到对应库了。`

```shell
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
```
3. 重新安装gmp等库后，再次configure
