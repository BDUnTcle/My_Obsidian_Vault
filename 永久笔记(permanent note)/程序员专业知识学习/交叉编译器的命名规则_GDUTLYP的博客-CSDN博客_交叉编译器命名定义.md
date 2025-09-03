#程序员/交叉编译
转载链接：http://blog.csdn.net/zqixiao\_09/article/details/51823165

\===============================================================

在折腾[嵌入式开发](http://lib.csdn.net/base/embeddeddevelopment "嵌入式开发知识库")，用到[交叉编译](https://so.csdn.net/so/search?q=%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91&spm=1001.2101.3001.7020)器的时候，常常会看到这样的名字：

**arm-xscale-[Linux](http://lib.csdn.net/base/linux "Linux知识库")\-gnueabi-gcc**

**arm-liunx-gnu-gcc**

等等

       其中，对应的交叉编译器的前缀为：

**arm-xscale-[linux](http://lib.csdn.net/base/linux "Linux知识库")\-gnueabi-**

**arm-liunx-gnu-**

     下面以编译crosstool-ng中：通过ct-ng list-samples中得到的输出为例，当做交叉编译器的名字的例子，供参考：

![](https://img-blog.csdn.net/20160704203024236?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

交叉编译工具链的命名规则为：

**arch \[-vendor\] \[-os\] \[-(gnu)eabi\]**

arch – 体系[架构](http://lib.csdn.net/base/architecture "大型网站架构知识库")，如ARM，MIPS

vendor – 工具链提供商

os – 目标[操作系统](http://lib.csdn.net/base/operatingsystem "操作系统知识库")

eabi – [嵌入式](http://lib.csdn.net/base/embeddeddevelopment "嵌入式开发知识库")应用二进制接口（Embedded Application Binary Interface）

    根据对操作系统的支持与否，ARM GCC可分为支持和不支持操作系统，如

arm-none-eabi：这个是没有操作系统的，自然不可能支持那些跟操作系统关系密切的函数，比如fork(2)。他使用的是newlib这个专用于[嵌入式](https://so.csdn.net/so/search?q=%E5%B5%8C%E5%85%A5%E5%BC%8F&spm=1001.2101.3001.7020)系统的C库。

arm-none-linux-eabi：用于Linux的，使用Glibc  

下面是详细解析

**一、交叉编译器的命名规则**

**1、交叉编译器名字中的arch部分**

          **arch，即系统架构**

          表示交叉编译器，是用于哪个目标系统架构中，用于那个平台中的。即，用此交叉编译器编译出来的程序，是运行在哪种CPU上面的。

          arch的值，常见的有很多种，比如**arm，x86，mips**等等。

```
举例：交叉编译器中的arch的值

arm-cortex_a8-linux-gnueabi中的arm

mips-ar2315-linux-gnu中的mips

powerpc-e500v2-linux-gnuspe中的powerpc

x86_64-unknown-mingw32中的x86_64

```

**1.1 crosstool-ng中arch的值**

       crosstool-ng中，和arch对应的值，应该就是"Target options"中的"Target Architecture"的值了。

       比如常见的，配置为arm的话，就是：  

![](https://img-blog.csdn.net/20160704203134628?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)  

      对应的配置参数是：ARCH\_arm  

**2、交叉编译器名字中的vendor部分**

          **vendor，即生成厂家，提供商**

          表示谁提供的，即谁制作出来这个交叉编译器的。vendor的值，貌似是可以自己随便填写的。

          其他常见写法，还有写成编译交叉编译器的作者的自己的名字的。比如，我叫crifan，那么就可以写成crifan，然后生成的交叉编译器，就是xxx-crifan-xxx-xxx了。

          更加通用的做法，好像是：把vendor写成，体系架构的值，比如我之前针对xscale的去配置crosstool-ng的时候，就写了个xscale。或者写成CPU的厂家的名字，或者是开发板的名字等等。

```
举例：交叉编译器中的vendor的值

arm-cortex_a8-linux-gnueabi中的cortex_a8，就属于CPU的名字

mips-ar2315-linux-gnu中的ar2315

powerpc-e500v2-linux-gnuspe中的e500v2，也是CPU的内核名

arm-buildroot-linux-uclibcgnueabi中的buildroot，是之前折腾Buildroot时，看到的，即Buildroot把自己视为当前自己制作出来的交叉编译器的vendor。

```

**2.1 crosstool-ng中vendor的值**

       crosstool-ng中，和vendor对应的值，应该就是"Toolchain options"中的"Tuple's vendor string"的值了。

       比如我之前配置为xscale的话，就是：  

![](https://img-blog.csdn.net/20160704203219472)  

对应的配置参数是：CT\_TARGET\_VENDOR

对应的help的解释是：

![](https://img-blog.csdn.net/20160704203245349)

**3、交叉编译器名字中的kernel部分**

          **kernel，直译为，内核**

         其实指的是，你用此交叉编译器，编译出来的程序，**所运行的目标系统。**即此交叉编译器，编译出来的程序，在什么系统中，什么环境中，运行。

         而对应的环境或系统，主要有两种：

**a -- Linux**

      表示：有OS（此处主要指的是Linux）操作系统的环境

      比如，我用交叉编译器，编译一个helloworld程序，然后下载到嵌入式开发中的嵌入式Linux中运行，就属于用此交叉编译器编译出来的程序，是要运行于带OS即嵌入式Linux系统环境中的。

     此处，简称为有OS的目标系统：Linux

**b -- bare-metal**

       bare-metal，直译为：裸金属

       表示**无（此处主要指的是Linux）操作系统的环境**，比如，用此交叉编译器，去编译一个Uboot，或者是其他一个小程序，是运行在，无嵌入式Linux的时候，单独运行的一个程序。

       比如，你购买的嵌入式系统开发版，常常附带一些小程序，比如点亮LED，跑马灯等程序，就是这种，运行在无OS的环境的

      此处，简称为**无OS系统的：bare-metal**

**3.1 crosstool-ng中kernel的值**

       crosstool-ng中，和kernel对应的值，应该就是"Operating System"中的"Target OS"的值了。

比如我之前配置为Linux的话，就是：  

![](https://img-blog.csdn.net/20160704203327366)  

对应的配置参数是：**GEN\_CHOICE\_KERNEL中的CT\_KERNEL\_linux**

对应的help的解释是：  

![](https://img-blog.csdn.net/20160704203353070)  

**4、交叉编译器名字中的system部分**

          **system，直译为，系统**

          其实主要表示的，**交叉编译器所选择的库函数和目标系统，**最常见的一些值有，**gnu，gnueabi，uclibcgnueabi**等等。

          其中，此处有几方面的值，表示了几方面的含义：  

**4.1 system中的gnu**

        好像都是gnu

        不是很明白，貌似是：

        **gnu == gnu libc == glibc**

        即，gnu，**就是表示用的是glibc的意思**。

**a -- crosstool-ng中system为gnu的情况**

       crosstool-ng中，和system中gnu对应的值，应该就是"C-library"中的"C library"的值设置为"glibc"了。

![](https://img-blog.csdn.net/20160704203455025)  

对应的配置参数是：**CT\_LIBC\_glibc**

对应的help的解释是：  

![](https://img-blog.csdn.net/20160704203532739)  

**4.2 system中的eabi**

       与此相对应的，之前早期的是oabi

**a -- crosstool-ng中system为eabi的情况**

      crosstool-ng中，和system中eabi对应的值，应该就是"Target options"中的"-\*- Use EABI"的值了。  

![](https://img-blog.csdn.net/20160704203656590)  

注意：此处是选择的ARM，EABI在此处，已经是默认，无法修改的值，只能是EABI了。

好像是因为，Linux内核等其他选择导致的，此处无法更改EABI。

对应的配置参数是：**CT\_ARCH\_ARM\_EABI**

对应的help的解释是：  

![](https://img-blog.csdn.net/20160704203718037)  

**4.3 system中的uclibc**

      uclibc，是c库中的一种

      crosstool-ng中，目前支持三种：**glibc,eglibc,uclibc**

**a -- crosstool-ng中system为uclibc的情况**

       crosstool-ng中，和system中uclibc对应的值，应该就是"C-library"中的"C library"的值设置为"uClibc"了。  

![](https://img-blog.csdn.net/20160704203746428)  

对应的配置参数是：CT\_LIBC\_uClibc

对应的help的解释是：  

![](https://img-blog.csdn.net/20160704203810053)  

  
所以，针对上述，gnu，eabi，uclibc等几个选项，对应的常见的一些组合的含义是：

gnu 等价于：glibc+oabi

gnueabi 等价于：glibc+eabi

uclibc 等价于：uclibc+oabi

```
举例：交叉编译器中的system的值

arm-cortex_a8-linux-gnueabi中的gnueabi，即glibc+eabi

mips-ar2315-linux-gnu中的gnu，即glibc+oabi

powerpc-e500v2-linux-gnuspe中的gnuspe，没搞懂啥意思。。

x86_64-unknown-mingw32中的mingw32，用的是Windows下的mingw32的库

```

**二、交叉编译工具链实例**

**1、arm-none-eabi-gcc**

       （ARM architecture，no vendor，not target an operating system，complies with the ARM EABI）

         用于编译 ARM 架构的裸机系统（包括 ARM Linux 的 boot、kernel，不适用编译 Linux 应用 Application），一般适合 ARM7、Cortex-M 和 Cortex-R 内核的芯片使用，所以不支持那些跟操作系统关系密切的函数，比如fork(2)，他使用的是 newlib 这个专用于嵌入式系统的C库。  
**  
2、arm-none-linux-gnueabi-gcc**

        **(ARM architecture, no vendor, creates binaries that run on the Linux operating system, and uses the GNU EABI)**

        主要用于基于ARM架构的Linux系统，可用于编译 ARM 架构的 u-boot、Linux内核、linux应用等。arm-none-linux-gnueabi基于GCC，使用Glibc库，经过 Codesourcery 公司优化过推出的编译器。arm-none-linux-gnueabi-xxx 交叉编译工具的浮点运算非常优秀。一般ARM9、ARM11、Cortex-A 内核，带有 Linux 操作系统的会用到。

**3、arm-eabi-gcc**

        [Android](http://lib.csdn.net/base/android "Android知识库") ARM 编译器。

**4、armcc**

       ARM 公司推出的编译工具，功能和 arm-none-eabi 类似，可以编译裸机程序（u-boot、kernel），但是不能编译 Linux 应用程序。armcc一般和ARM开发工具一起，Keil MDK、ADS、RVDS和DS-5中的编译器都是armcc，所以 armcc 编译器都是收费的（爱国版除外，呵呵~~）。  
**  
5、arm-none-uclinuxeabi-gcc 和 arm-none-symbianelf-gcc**

       arm-none-uclinuxeabi 用于uCLinux，使用Glibc。

       arm-none-symbianelf 用于symbian，没用过，不知道C库是什么 。

**Codesourcery**

     Codesourcery推出的产品叫Sourcery G++ Lite Edition，其中基于command-line的编译器是免费的，在官网上可以下载，而其中包含的IDE和debug 工具是收费的，当然也有30天试用版本的。

     目前CodeSourcery已经由明导国际(Mentor Graphics)收购，所以原本的网站风格已经全部变为 Mentor 样式，但是 Sourcery G++ Lite Edition 同样可以注册后免费下载

     Codesourcery一直是在做ARM目标 GCC 的开发和优化，它的ARM GCC在目前在市场上非常优秀，很多 patch 可能还没被gcc接受，所以还是应该直接用它的（而且他提供Windows下\[mingw交叉编译的\]和Linux下的二进制版本，比较方便；如果不是很有时间和兴趣，不建议下载 src 源码包自己编译，很麻烦，Codesourcery给的shell脚本很多时候根本没办法直接用，得自行提取关键的部分手工执行，又费精力又费时间，如果想知道细节，其实不用自己编译一遍，看看他是用什么步骤构建的即可，如果你对交叉编译器感兴趣的话。

**  
ABI 和 EABI**

**a -- ABI**

       二进制应用程序接口**(Application Binary Interface (ABI) for the ARM Architecture)**。在计算机中，应用二进制接口描述了应用程序（或者其他类型）和操作系统之间或其他应用程序的低级接口。

**b -- EABI**

       **嵌入式ABI**。嵌入式应用二进制接口指定了文件格式、数据类型、寄存器使用、堆积组织优化和在一个嵌入式软件中的参数的标准约定。开发者使用自己的汇编语言也可以使用 EABI 作为与兼容的编译器生成的汇编语言的接口。

     两者主要区别是，**ABI是计算机上的，EABI是嵌入式平台上（如ARM，MIPS等）**。

**arm-linux-gnueabi-gcc 和 arm-linux-gnueabihf-gcc**

       两个交叉编译器分别适用于 armel 和 armhf 两个不同的架构，armel 和 armhf 这两种架构在对待浮点运算采取了不同的策略（有 fpu 的 arm 才能支持这两种浮点运算策略）。

       其实这两个交叉编译器只不过是 gcc 的选项 -mfloat-abi 的默认值不同。gcc 的选项 -mfloat-abi 有三种值 soft、softfp、hard（其中后两者都要求 arm 里有 fpu 浮点运算单元，soft 与后两者是兼容的，但 softfp 和 hard 两种模式互不兼容）：

soft： 不用fpu进行浮点计算，即使有fpu浮点运算单元也不用，而是使用软件模式。

softfp： armel架构（对应的编译器为 arm-linux-gnueabi-gcc ）采用的默认值，用fpu计算，但是传参数用普通寄存器传，这样中断的时候，只需要保存普通寄存器，中断负荷小，但是参数需要转换成浮点的再计算。

hard： armhf架构（对应的编译器 arm-linux-gnueabihf-gcc ）采用的默认值，用fpu计算，传参数也用fpu中的浮点寄存器传，省去了转换，性能最好，但是中断负荷高。

把以下[测试](http://lib.csdn.net/base/softwaretest "软件测试知识库")使用的C文件内容保存成 mfloat.c：


```
1.  #include <stdio.h>  
2.  int main(void)  
3.  {  
4.      double a,b,c;  
5.      a = 23.543;  
6.      b = 323.234;  
7.      c = b/a;  
8.      printf(“the 13/2 = %f\\n”, c);  
9.      printf(“hello world !\\n”);  
10.      return 0;  
11.  }  
```


  
1、使用 arm-linux-gnueabihf-gcc 编译

使用“-v”选项以获取更详细的信息：

\# arm-linux-gnueabihf-gcc -v mfloat.c  
COLLECT\_GCC\_OPTIONS=’-v’ ‘-march=armv7-a’ ‘-mfloat-abi=hard’ ‘-mfpu=vfpv3-d16′ ‘-mthumb’  
\-mfloat-abi=hard

可看出使用hard硬件浮点模式。

**  
2、使用 arm-linux-gnueabi-gcc 编译**

\# arm-linux-gnueabi-gcc -v mfloat.c  
COLLECT\_GCC\_OPTIONS=’-v’ ‘-march=armv7-a’ ‘-mfloat-abi=softfp’ ‘-mfpu=vfpv3-d16′ ‘-mthumb’  
\-mfloat-abi=softfp