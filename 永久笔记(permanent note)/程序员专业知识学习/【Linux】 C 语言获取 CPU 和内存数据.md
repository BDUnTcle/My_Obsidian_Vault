#linux #Linux/系统调用 #Linux/内核（Linux_Kernel） 
## Linux 中的 CPU 和[内存](https://so.csdn.net/so/search?q=%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)数据

  

有时候，在程序运行过程中需要考虑到 CPU 和内存的占用情况，也需要观察系统 CPU 和内存的使用情况，虽然 Linux 上有对应的指令可以很方便的获取这些数据，但这些指令毕竟不是接口，不能直接当 API 调用。本章通过 Linux C 语言实现获取进程 CPU 和内存占用的接口。

  

在 Linux 中，所有即时数据（如 CPU 和内存数据）都位于 **/proc/** 目录中，进程的即时数据位于 **/proc/{pid}/** 目录中。说白了，要获取 CPU 和内存的利用率，就是要去解析这些文件。

  

但 CPU 数据有所不同，**/proc/ 中保存的 CPU 数据都是自系统开机以来的时钟数** ，要得到 CPU 的利用率就需要做统计运算，计算公式如下  

平均 C P U 利用率 = C P U 工作时间 2 − C P U 工作时间 1 C P U 总时间 2 − C P U 总时间 1 平均CPU利用率 = \\frac{CPU工作时间2-CPU工作时间1}{CPU总时间2-CPU总时间1} 平均CPU利用率\=CPU总时间2−CPU总时间1CPU工作时间2−CPU工作时间1  

注意： C P U 工作时间 = C P U 总时间 − C P U 空闲时间 CPU工作时间=CPU总时间-CPU空闲时间 CPU工作时间\=CPU总时间−CPU空闲时间 。因为这里计算的是一个统计值，需要一段时间间隔，一般设置在 0~1s 之间，所以该过程会阻塞一段时间。当然，也可以使用一个单独线程去计算，将结果放入一个全局变量中。

  

  

## C 语言获取 CPU 和内存数据

  

介绍完 CPU 利用率的原理，就可以直接使用 C 语言获取这些数据了。若是还有不明白的地方也不要紧，代码中有详细的注释。代码分两部分：接口声明和接口实现，只依赖系统头文件，可在项目中直接使用。

  

接口声明代码：

  

```c

// CPU利用率，包含系统CPU和本进程CPU的利用率

struct CpuUsed {

    unsigned long sys_used;

    unsigned long proc_used;

};

  

// 获取CPU利用率，如CPU利用率为60%，则返回60。

// 系统CPU数据位于文件/proc/stat中，进程CPU数据位于/proc/{pid}/stat中，

// 文件中只有自系统启动以来的CPU时钟数，利用率需要手动进行统计和计算，

// 默认统计时间间隔为500ms（一般设置在0~1s之间），所以该函数会阻塞ms的时间。

CpuUsed GetCpuUsed(int ms = 500);

  

// 获取系统已使用的内存，单位MB。total为输出参数，表示总内存

// 系统内存数据位于文件/proc/meminfo中

int GetSystemMemUsed(int &total);

  

// 获取本进程已使用的内存，单位MB。若不足1MB，返回1

// 进程内存数据位于文件/proc/{pid}/statm中

int GetProcessMemUsed(void);

```

  

接口实现代码：

  

```c

#include <unistd.h>         // for getpid and usleep

#include <sys/sysinfo.h>    // for get_nprocs

  

// cpu信息的结构体，读文件/proc/stat

// see: https://man7.org/linux/man-pages/man5/proc.5.html

struct CpuStat {

    char name[8];               // 设备名，一般值为pu

    unsigned long user;         // 用户态的CPU时间（单位:0.01s）

    unsigned long nice;         // nice值为负的进程所占用的CPU时间（单位:0.01s）

    unsigned long system;       // 处于核心态的运行时间（单位:0.01s）

    unsigned long idle;         // 除IO等待时间意外其他等待时间（单位:0.01s）

};

  

// 内存信息的结构体，读文件/proc/meminfo

struct MemInfo {

    unsigned long total;        // MemTotal 总内存

    unsigned long free;         // MemFree  空闲内存

    unsigned long avaliable;    // MemAvailable 可用内存，约等于 MemFree + Buffer + Catch

};

  

// 解析/proc/stat文件，获取CPU信息

static void GetSystemCpuStat(CpuStat *s) {

    memset(s, 0, sizeof(CpuStat));

  

    char buf[256];

    FILE *fd = fopen("/proc/stat", "r");

    assert(fd != nullptr);

    fgets(buf, sizeof(buf), fd);

    sscanf(buf, "%s  %lu %lu %lu %lu", s->name, &s->user, &s->nice, &s->system, &s->idle);

    fclose(fd);

    // fprintf(stdout, "%s: %lu %lu %lu %lu\n", s->name, s->user, s->nice, s->system, s->idle);

}

  

// 向后偏移14项，正好是utime

#define PROCESS_ITEM 14

  

// 获取/proc/{pid}/stat中CPU的使用信息，主要是

// (14) utime  %lu

// (15) stime  %lu

// (16) cutime  %ld

// (17) cstime  %ld

static unsigned long GetProcessCpuTime(int pid) {

    // 计算当前进程对应的文件名

    char filename[64];

    snprintf(filename, sizeof(filename) - 1, "/proc/%d/stat", pid);

  

    char buf[1024];

    FILE *fd = fopen(filename, "r");

    assert(fd != nullptr);

    fgets(buf, sizeof(buf), fd);

    // fprintf(stdout, "%s: %s", filename, buf);

    fclose(fd);

  

    // 向后偏移，直至utime项

    int count = 1;

    const char *p = buf;

    while (*p != '\0') {

        if (*p++ == ' ') {

            count++;

            if (count == PROCESS_ITEM) break;

        }

    }

    if (*p == '\0') return 0;

  

    unsigned long utime = 0;    // user time

    unsigned long stime = 0;    // kernel time

    unsigned long cutime = 0;   // all user time

    unsigned long cstime = 0;   // all dead time

    sscanf(p, "%ld %ld %ld %ld", &utime, &stime, &cutime, &cstime);

    // fprintf(stdout, "proc[%d]: %lu %lu %lu %lu\n", pid, utime, stime, cutime, cstime);

    return (utime + stime + cutime + cstime);

}

  

// 获取CPU利用率，如CPU利用率为60%，则返回60

CpuUsed GetCpuUsed(int ms) {

    CpuUsed used;

    used.sys_used = used.proc_used = 0;

  

    int pid = getpid();

    CpuStat s1, s2;

    GetSystemCpuStat(&s1);

    unsigned long proc_time1 = GetProcessCpuTime(pid);

  

    usleep(ms * 1000);

  

    GetSystemCpuStat(&s2);

    unsigned long proc_time2 = GetProcessCpuTime(pid);

  

    // 计算CPU利用率：使用时间/总时间

    unsigned int sys_used1 = s1.user + s1.nice + s1.system;

    unsigned int sys_used2 = s2.user + s2.nice + s2.system;

    unsigned int sys_total1 = sys_used1 + s1.idle;

    unsigned int sys_total2 = sys_used2 + s2.idle;

    if (sys_total1 < sys_total2) {

        used.sys_used = 100 * (sys_used2 - sys_used1) / (sys_total2 - sys_total1);

        // 多线程，需要乘CPU core数量

        used.proc_used = get_nprocs() * 100 * (proc_time2 - proc_time1) / (sys_total2 - sys_total1);

    }

    return used;

}

  

// 解析/proc/meminfo文件，获取内存信息

// MemTotal %lu

// MemFree %lu

// MemAvailable %lu (since Linux 3.14)

static void GetSystemMeminfo(MemInfo *info) {

    memset(info, 0, sizeof(MemInfo));

  

    char buf[128];

    char name[64];

    char unit[64];

    FILE *fd = fopen("/proc/meminfo", "r");

    assert(fd != nullptr);

    fgets(buf, sizeof(buf), fd);

    sscanf(buf, "%s %u %s", name, &info->total, unit);

    fgets(buf, sizeof(buf), fd);

    sscanf(buf, "%s %u %s", name, &info->free, unit);

    fgets(buf, sizeof(buf), fd);

    sscanf(buf, "%s %u %s", name, &info->avaliable, unit);

    fclose(fd);

    // fprintf(stdout, "mem: %u %u %u\n", info->total, info->free, info->avaliable);

}

  

// 解析/proc/{pid}/statm文件，获取内存信息，前两项为

// size (pages) 任务虚拟地址空间的大小 VmSize/4，单位 KB

// resident(pages) 应用程序正在使用的物理内存的大小 VmRSS/4，单位 KB

static unsigned long GetProcessMeminfo(int pid) {

    // 计算当前进程对应的文件名

    char filename[64];

    snprintf(filename, sizeof(filename) - 1, "/proc/%d/statm", pid);

  

    char buf[256];

    FILE *fd = fopen(filename, "r");

    assert(fd != nullptr);

    fgets(buf, sizeof(buf), fd);

    fclose(fd);

  

    unsigned long size = 0;

    unsigned long resident = 0;

    sscanf(buf, "%lu %lu", &size, &resident);

    // fprintf(stdout, "proc mem: %u %u\n", size, resident);

    return resident * 4;

}

  

// 获取系统已使用的内存，单位MB。total为输出参数，表示总内存

int GetSystemMemUsed(int &total) {

    MemInfo info;

    GetSystemMeminfo(&info);

    total = info.total / 1024;

    return (total - info.avaliable / 1024);

}

  

// 获取本进程已使用的内存，单位MB

int GetProcessMemUsed(void) {

    unsigned long mem_used = GetProcessMeminfo(getpid());

    return ((mem_used < 1024) ? 1 : mem_used / 1024);

}

```

  

其中，在获取系统内存时，文件 /proc/stat/meminfo 中有如下三项：

  

-   **MemTotal**

    系统总内存数，可简单理解为系统的物理内存。

-   **MemFree**

    系统空闲内存数，即系统中尚未被使用的内存。

-   **MemAvailable**

    系统可用内存数，之所以有这个概念是因为 Linux 中有些内存虽已被使用，但仍可以回收，比如 Cache/Buffer、Slab 中都有一部分是能被回收的，所以 MemFree 不能代表全部可用的内存。可以简单的理解为：**MemAvailable ≈ MemFree + Buffers + Cached**，当然这是一个估值。

  

在网上看见过一个描述，个人感觉比较准确，在此分享一下：

  

> MemAvailable 与 MemFree 的关键区别在于：MemAvailable 是应用程序层面的内存大小，而 MemFree 是系统层面的内存大小。

  

  

## 参考资料

  

1.  [proc(5) — Linux manual page](https://man7.org/linux/man-pages/man5/proc.5.html)

2.  [C++获取对应进程的cpu和内存使用情况（支持linux和windows）](https://zhuanlan.zhihu.com/p/266839249)

3.  [LINUX C语言 定时查看CPU，内存和磁盘利用率](https://zhuanlan.zhihu.com/p/337083938)