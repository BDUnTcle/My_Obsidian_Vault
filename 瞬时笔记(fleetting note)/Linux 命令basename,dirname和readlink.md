#Linux/命令 #Linux/Shell脚本
# basename的使用--------------->与dirname相反

## 用处：获取文件名
## 格式：
1. **basename** \[pathname\]  \[*suffix*\]
2. **basename** \[string\]  \[*suffix*\]
*suffix*为后缀，若指定了*suffix*，basename会将pathname或string中的*suffix*去掉。

basename会将/即/之前的内容全都去掉，只保留最后的文件名，如果指定到了 suffix （要去掉的后缀）会将后缀也会去掉；

例1： basename  ~/TEST/file.sh                     ------------>得到file.sh
例2： basename ~/TEST/file.sh  .sh                ---------------->得到file
例3： basename $1

./test.sh aa         --------------------------------------->得到aa

---
# dirname的使用----->与basename相反
## 介绍：
dirname命令可以取给定路径的目录部分，如果给定的参数本身为一个目录，那就取当前目前的上一层目录。这个命令很少直接在shell命令行中使用，一般把它用在shell脚本中，用于取得脚本文件所在目录，然后将当前目录切换过去。

**获取文件的目录，去掉文件名和最后一个/**
**如果只有文件名，则输出.**
**如果没有文件，则去掉最后一个目录及/**

## 示例：
1） dirname /usr/bin/sort               -------------------->结果  /usr/bin
2） dirname stdio.h                 ------------------>结果 
3） dirname /usr/bin                 ---------------->结果 /usr  
4） dirname /usr/bin/               ------------------->结果 /usr                    ----------->比较特殊
5） 先cd到当前路径然后pwd，打印成绝对路径(打印绝对路径的方法1)


```

path=$(cd `dirname $0`;pwd)

```

  

 **dirname $0 只是获取的当前脚本的相对路径.--------------------结果为.**  

cd \`dirname $0\`;pwd  先cd到当前路径然后pwd，打印成绝对路径

6）当前路径的上一级路径
script\_path=\`readlink -f $0\`  
script\_dir=\`dirname $script\_path\` 

---
# readlink -f  /home/test/log

  

当 /home/test/log 是个连接的话，会指向连接的文件；如  /home/test/mylink

  

当 /home/test/log 不是连接的话，会显示本身的绝对路径  /home/test/log

  

**打印绝对路径的方法2----------->使用readlink -f**

  

```

=$(dirname $0)=$(readlink -f $path)

```

  

 echo path   ---------------->  打印结果为 **.**

  

**ehcho path2   --------------->打印结果为绝对路径**

  

**或者一下写法也行：**

  
## 在shell脚本中的实际使用例子
### 获取脚本文件的绝对路径
```shell

path=$(readlink -f $0)

```

### 获取脚本文件所在目录的绝对路径

```shell
path=$(dirname $(readlink -f $0))
```
