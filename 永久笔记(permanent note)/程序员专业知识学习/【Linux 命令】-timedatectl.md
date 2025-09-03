#Linux/linux命令笔记 #Linux/系统时间设置
## 修改时区方法一：

**timedatectl set-timezone Asia/Shanghai     >>>服务器时区设置**

**date -s "2020-12-20 16:34:50"    >>>服务器时间设置**

**时间格式显示12小时制，如何操作？**

**需要修改时间为24小时，可以修改/etc/default/locale，默认没有LC\_TIME这个变量，在文件中增加一行：**

****LC\_TIME=en\_DK.UTF-8****

保存退出，然后reboot重启服务器即可生效，date命令查看是24小时时间格式。

## 修改时区方法二：

1.使用命令：tzselect

在这里我们选择亚洲 Asia，确认之后选择中国（China)，最后选择北京(Beijing),选择1

2.复制文件到/etc目录下

```
root@ubuntu:/# cp /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime
```

3.再次查看时间date -R，已经修改为北京时间

![](https://img2020.cnblogs.com/blog/1459790/202111/1459790-20211109172617269-1426072650.png)

Linux中查看有关时间的命令是date \[选项\] +\[格式\]

首先我们先看看单纯的date的输出结果，其中CST表示东八区。

![](https://img2020.cnblogs.com/blog/1459790/202101/1459790-20210104161343206-1027573628.png)

使用 timedatectl命令可以查看时区

![](https://img2020.cnblogs.com/blog/1459790/202101/1459790-20210104161448367-1780322211.png)

 使用date -s "yyyy-MM-dd hh:mm:ss"，例如将当前系统时间设置为2021年1月4日12:00:00则使用date -s "2021-01-04 12:00:00"

![](https://img2020.cnblogs.com/blog/1459790/202101/1459790-20210104161822266-761488190.png)

以上修改的仅仅是系统时间，由操作系统控制。还有一个硬件时间。使用hwclock --systohc可以将系统时间同步到硬件时间。

在CentOS 6版本，时间设置有date、hwclock命令，

硬件时钟和系统时钟

(1) 硬件时钟

RTC(Real-Time Clock)或CMOS时钟，一般在主板上靠电池供电，服务器断电后也会继续运行。仅保存日期时间数值，无法保存时区和夏令时设置。

(2) 系统时钟

一般在服务器启动时复制RTC时间，之后独立运行，保存了时间、时区和夏令时设置。

**从CentOS 7开始，使用了一个新的命令timedatectl**

timedatectl 命令

(1) 读取时间

timedatectl //等同于 timedatectl status

(2) 设置时间

timedatectl set-time "YYYY-MM-DD HH:MM:SS"

(3) 列出所有时区

timedatectl list-timezones

(4) 设置时区

timedatectl set-timezone Asia/Shanghai

(5) 是否NTP服务器同步

timedatectl set-ntp yes //yes或者no

(6) 将硬件时钟调整为与本地时钟一致

timedatectl set-local-rtc 1  
hwclock --systohc --localtime //与上面命令效果一致

注意: 硬件时钟默认使用UTC时间，因为硬件时钟不能保存时区和夏令时调整，修改后就无法从硬件时钟中读取出准确标准时间，因此不建议修改。修改后系统会出现下面的警告。

GMT、UTC、CST、DST 时间

(1) UTC

整个地球分为二十四时区，每个时区都有自己的本地时间。在国际无线电通信场合，为了统一起见，使用一个统一的时间，称为通用协调时(UTC, Universal Time Coordinated)。

(2) GMT

格林威治标准时间 (Greenwich Mean Time)指位于英国伦敦郊区的皇家格林尼治天文台的标准时间，因为本初子午线被定义在通过那里的经线。(UTC与GMT时间基本相同，本文中不做区分)

(3) CST

中国标准时间 (China Standard Time)

(4) DST

夏令时(Daylight Saving Time) 指在夏天太阳升起的比较早时，将时钟拨快一小时，以提早日光的使用。（中国不使用）

GMT + 8 = UTC + 8 = CST

https://www.cnblogs.com/k98091518/p/6991614.html