#Linux/内核（Linux_Kernel） #CS/c语言 #程序员 #Linux/系统调用
# 介绍
> 在计算机中，**ioctl**(input/output control)是一个专用于设备输入输出操作的系统调用,该调用传入一个跟设备有关的请求码，系统调用的功能完全取决于请求码。举个例子，CD-ROM驱动程序可以弹出光驱，它就提供了一个对应的**Ioctl**请求码。设备无关的请求码则提供了内核调用权限。ioctl这名字第一次出现在Unix第七版中，他在很多类[unix](https://baike.baidu.com/item/unix?fromModule=lemma_inlink)系统（比如[Linux](https://baike.baidu.com/item/Linux?fromModule=lemma_inlink)、Mac OSX等）都有提供，不过不同系统的请求码对应的设备有所不同。[Microsoft Windows](https://baike.baidu.com/item/Microsoft%20Windows?fromModule=lemma_inlink)在Win32 API里提供了相似的函数，叫做[DeviceIoControl](https://baike.baidu.com/item/DeviceIoControl?fromModule=lemma_inlink)。

---
# Linux Man Page
[Linux官方文档](https://man7.org/linux/man-pages/man2/ioctl.2.html)
[WIKI百科页面](https://zh.wikipedia.org/wiki/Ioctl)

---
# 参数介绍

---

# 示例用法

**获取fd文件描述符中串口IO缓存中可读取的数据字节大小**
```c
//获取fd文件描述符中IO缓存中可读取的数据字节大小
/*
参数二中的 TIOCINQ 为系统定义宏，和 FIONREAD 宏为同一定义，定义于<sys/ioctl.h>相关头文件中
Linux官方文档对其描述如下：
FIONREAD
              Argument: int* _argp_

              Get the number of bytes in the input buffer.
*/
int cnt = 0;
if(ioctl(_fd,TIOCINQ,&cnt) == -1)
{
	throw Exception("Error");
}
```
