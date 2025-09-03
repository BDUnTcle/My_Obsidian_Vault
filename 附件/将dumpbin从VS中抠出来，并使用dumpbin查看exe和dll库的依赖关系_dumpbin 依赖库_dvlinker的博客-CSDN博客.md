**目录**

[1、初步说明](https://blog.csdn.net/chenlycly/article/details/126401626#t0)

[2、在开发的机器上使用dumpbin工具查看dll库的依赖关系](https://blog.csdn.net/chenlycly/article/details/126401626#t1)

[3、将dumpbin.exe从Visual Studio中抠出来](https://blog.csdn.net/chenlycly/article/details/126401626#t2)

[3.1、找到dumpbin.exe文件及其依赖的dll文件](https://blog.csdn.net/chenlycly/article/details/126401626#t3)

[3.2、在cmd中运行dumpbin，提示找不到link.exe文件](https://blog.csdn.net/chenlycly/article/details/126401626#t4)

[3.3、再次运行dumpbin.exe提示找不到mspdb100.dll](https://blog.csdn.net/chenlycly/article/details/126401626#t5)

___

       最近，有个开发同时为了验证问题，需要将mediaxxx.dll从依赖该库的目标库中临时移除，在目标库中不再调用mediaxxx.dll库的导出接口，不再引入mediaxxx.dll对应的.lib文件，但启动exe主程序时还是报找不到mediaxxx.dll，代码中明明已经将对mediaxxx.dll库的引用都去掉了，为啥还会依赖mediaxxx.dll库呢？于是找到我帮忙分析一下，看一下到底还有哪个模块还依赖mediaxxx.dll库。

## 1、初步说明

       这个可以使用**Dependency Walker**去查看exe主程序与底层的dll库的依赖关系，但该工具只能查看静态依赖的dll库，对于代码中使用[LoadLibrary](https://so.csdn.net/so/search?q=LoadLibrary&spm=1001.2101.3001.7020)去动态加载的dll库，是查看不到的。我们的exe程序中确实有部分模块是动态加载的。

       其实还有个更好用的工具**dumpbin**，这个工具是微软Visual Studio（IDE开发环境）自带的工具，位于VS的安装目录中。使用该工具可以查看exe和[dll文件](https://so.csdn.net/so/search?q=dll%E6%96%87%E4%BB%B6&spm=1001.2101.3001.7020)的依赖关系，可以查看exe和dll导入接口和导出接口等信息。

## 2、在开发的机器上使用dumpbin工具查看dll库的依赖关系

        如何使用dumpbin工具呢？以Visual Studio 2010为例，可以到Windows开始菜单中找到Microsoft Visual Studio 2010节点，在该节点下找到如下截图中命令行入口：

![](https://img-blog.csdnimg.cn/1f6137e1861046e59108a82fca733f13.png)

点击菜单项弹出如下的命令行窗口，会自动切换到d:\\Program Files (x86)\\Microsoft Visual Studio 10.0\\VC路径中，然后可以在该命令行窗口中直接操作dumpbin.exe工具。

       可以输入dumpbin /?命令，查看dumpbin.exe支持的[命令行参数](https://so.csdn.net/so/search?q=%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%8F%82%E6%95%B0&spm=1001.2101.3001.7020)：

![](https://img-blog.csdnimg.cn/da4b75cbd66d4030b1915ff33ad96ebc.png)

在本问题中我们使用/DEPENDENTS参数，就能查看到目标exe和dll的依赖的库信息。具体可以分别执行如下的命令，将目标路径下的所有dll和exe的依赖关系输出：

```
dumpbin /DEPENDENTS C:\Users\Administrator\Desktop\Debug\*.dlldumpbin /DEPENDENTS C:\Users\Administrator\Desktop\Debug\*.exe
```

其中，/DEPENDENTS表示查看依赖关系。输出的结果如下所示：

![](https://img-blog.csdnimg.cn/07dcd66da030429c8f24d9e7523c8cae.png)

 直接在命令行中查看结果很不方便，我们**可以使用“>”重定向符将输出结果重定向到txt文件中**，方便查看搜索。命令如下：

```
dumpbin /DEPENDENTS C:\Users\Administrator\Desktop\Debug\*.dll > E:\0816-dll.txtdumpbin /DEPENDENTS C:\Users\Administrator\Desktop\Debug\*.exe > E:\0816-exe.txt
```

输出到文件中查看就方便了，可以随意的搜索了。到E盘中打开txt文件，直接搜索mediaxxx.dll，就看到了还有哪个库还依赖mediaxxx.dll了，如下所示：

![](https://img-blog.csdnimg.cn/1bb98d9ab2eb430e9db84ae9a8dceb57.png)

## 3、将dumpbin.exe从Visual Studio中抠出来

       上诉方法只能在安装Visual Studio的机器上使用，但有时我们可能需要在没安装VS的机器上使用，所以决定将dumpbin工具从VS中抠出来，方便大家使用。

### 3.1、找到dumpbin.exe文件及其依赖的dll文件

        启动Everything搜索工具，输入dumpbin.exe,看到如下的多个搜索结果：

![](https://img-blog.csdnimg.cn/edb605a4df24419990e46e4339a70942.png)

> Everything搜索工具是Windows平台上的文件搜索工具，可以搜索所有磁盘上的文件，比Windows系统自带的文件搜索要快很多，推荐大家使用。

其中D:\\Program Files (x86)\\Microsoft Visual Studio 10.0\\VC\\bin目录，就是VS的安装目录，将这个文件拷贝出来。

       然后使用Dependency walker打开dumpbin.exe，看看该exe还依赖哪些库，如下所示：

![](https://img-blog.csdnimg.cn/69e3feaf6d314021af89a79a14e897ed.png)

只依赖Kernel32.dll和msvcr100.dll，Kernel32.dll是系统库，是系统自带的，我们不需要带上该库。**msvcr100.dll是C运行时库，是安装VS时会拷贝到系统中的，需要带上的。**使用Everything搜索一下msvcr100.dll，拷贝过来就可以了。

### 3.2、在cmd中运行dumpbin，提示找不到link.exe文件

       我是将dumpbin工具的文件放置在C:\\Users\\Administrator\\Desktop\\dumpbin-2010目录中，打开cmd窗口，切换到该目录中，然后输入dumpbin /?命令，看看当前拷贝出来的dumpbin.exe能否正常运行。结果运行有问题，如下所示：

![](https://img-blog.csdnimg.cn/ab911bef4d514c29a73a4f2520bbb12d.png)

提示找不到link.exe。于是到dumpbin.exe所在路径D:\\Program Files (x86)\\Microsoft Visual Studio 10.0\\VC\\bin中，找到link.exe文件：

![](https://img-blog.csdnimg.cn/7515b0b8cbc64a309791b990f824506c.png)

拷贝过来。

### 3.3、再次运行dumpbin.exe提示找不到mspdb100.dll

       将link.exe文件拷贝过来后，再次在cmd窗口中运行dumpbin /?命令，结果还是有问题，如下所示：

![](https://img-blog.csdnimg.cn/960348f59b5a439fb6113a49b4712819.png)

提示找不到mspdb100.dll库。于是又用Everything搜索了一下mspdb100.dll：

![](https://img-blog.csdnimg.cn/39cd80e48c174bc580c11f6b9663003a.png)

 将mspdb100.dll拷贝过来。然后再次运行就正常，于是输入dumpbin /?命令，就能将dumpbin.exe命令行支持的参数打印出来，如下所示：

![](https://img-blog.csdnimg.cn/da4b75cbd66d4030b1915ff33ad96ebc.png)