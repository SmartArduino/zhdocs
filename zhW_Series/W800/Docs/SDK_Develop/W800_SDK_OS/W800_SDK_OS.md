<center><font size=10> W800_SDK_OS移植指导 </center></font>
<center> From SZDOIT</center>

## 1 引言

### 1.1 编写目的

本文档描述指导 Winnermicro W800 芯片的 SDK 开发人员如何移植或切换到新的 OS。

### 1.2 预期读者

W800 SDK 的开发人员及工程实现人员

### 1.3 术语定义

![image-20201114152942431](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114152942431.png)

## 2 SDK Kernel 移植

如图 1 所示，SDK 的操作系统相关代码均放置在./Src/OS 目录下，目前已经移植了FreeRTOS 实时操作系统。如果用户有需要使用其他实时操作系统，可以在此目录下建立新的文件夹，添加自己需要的操作系统

![image-20201114153020345](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114153020345.png)

## 3 系统调度相关移植

相关函数参见 sdk_root_dir/src/os/rtos/ports/ck804/下的 cpu_task_sw.S 文件及port.c 文件。此处以 FreeRTOS 为例，用户使用此操作作系统时，需要实现这两个文件中用所到的相应接口。如果需要要使用其它操作系统，建议下载 xt804 的 sdk，找到其示例代码中已经移植好的操作系统直接使用；如果没有现有可用的，则需要根据所用操作系统的要求实现相应接口，这里可能会需要内核(XT804)原厂(平头哥)的技术支持。

![image-20201114153055992](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114153055992.png)

## 4 内存相关移植

在 wm_mem.c 文件可以看到 SDK 中为 FreeRTOS 提供的 malloc 内存申请方式。因为 FreeRTOS 系统有特殊的要求，中断函数和普通函数的内存申请方式不一样。

如果用户的操作系统有相关要求，则也需要做相关处理；如果没有相关要求，则关闭wm_os_config.h 中的 TLS_OS_FREERTOS 宏定义就是 C 库的 malloc 函数申请内存了。

## 5 printf 函数

在 retarget.c 文件里可以看到两个函数：

1）int wm_vprintf(const char *fmt, va_list arg_ptr)；

2）int wm_printf(const char *fmt,...)；

这是两个 Wi-Fi 里会使用的打印函数，用户可以依据编译环境自行实现此函数，也可以使用已实现的函数，以与 printf 函数区分。

## 6 OSAL 层移植

为了方便操作系统的移植，操作系统和 W80X SDK 应用程序之间封装了一层抽象层，即对程序中需要用到的操作系统的接口函数进行了重新封装，程序采用统一的接口调用操作系统相关函数。

需要实现的接口函数在./include/OS 目录下的 wm_osal.h 中定义

### 6.1 系统时钟

声明 HZ 为常量：

const unsigned int HZ = 500;

在 wm_osal.h 文件里引用

extern const unsigned int HZ;

操作系统时钟定义，此处表明 500 个系统时钟为 1HZ 的频率，即 2ms 产生一个 sysTick中断，用户可以根据需要自己需要修改，对于部分操作系统需要将操作系统中对应的时间配置设置与我们定义的一致，例如 FreeRTOS 中需要修改 freeRTOSConfig.h 中的设置

#define configTICK_RATE_HZ   ((portTickType)500u) //时间片中断的频率

### 6.2 操作系统类型

```
/**ENUMERATION of OS*/
enum TLS_OS_TYPE{
	OS_UCOSTI = 0,
	OS_FREETROS = 1,
	OS_MAX_NUM
};
```

操作系统类型定义，用于指示当前操作系统的类型，用户可以添加自己的操作系统类型。

主要是用于特殊场合的兼容性设计（暂时没有使用）。

### 6.3 OSAL 层接口函数

OSAL 层接口函数，用户可以参考现有 SDK 中支持的 FreeRTOS 里面的实现方法将自己的操作系统相关函数封装在这些接口里面。

FreeRTOS 的函数封装在 wm_osal_rtos.c 文件中。

#### 6.3.1 时钟相关函数

![image-20201114153924739](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114153924739.png)

#### 6.3.2 系统初始化函数

![image-20201114154832531](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114154832531.png)

#### 6.3.3 任务相关函数

![image-20201114154907932](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114154907932.png)

![image-20201114154917784](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114154917784.png)

#### 6.3.4 信号量相关函数

![image-20201114154951195](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114154951195.png)

![image1](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image1.png)

#### 6.3.5 队列相关函数

![image-20201114155928495](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114155928495.png)

#### 6.3.6 邮箱消息相关函数

![image2](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image2.png)

#### 6.3.7 临界区相关函数

![image-20201114160210037](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114160210037.png)

#### 6.3.8 系统定时器相关函数

![image3](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image3.png)

![image-20201114160337478](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114160337478.png)

#### 6.3.9 其他

![image-20201114160403064](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_SDK_OS/image-20201114160403064.png)

## 7 在工程中切换 Kernel

Keil 工程更换 Kernel，需要找到 wm_os_config.h 文件，选择当前要使用的操作系统。修改需要选用的 Kernel 后，在 keil 工程中将 OS 组下的 OS 操作系统相关.c 文件替换成用户移植的 kernel 文件。
GCC 更换操作系统，直接修改 wm_config_gcc.inc 文件即可，如果用户使用自己的操作系统还需要修改对应的 Makefile 文件，具体见《WM_W800_SDK 脚本编译指南》。



## 支持与服务

| 四博智联资源                                        |                                                              |
| --------------------------------------------------- | ------------------------------------------------------------ |
| 官网                                                | [www.doit.am](http://www.doit.am/)                           |
| 教材                                                | [ESPDuino智慧物联开发宝典](https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-7420449993.9.Bgp1Ll&id=520583000610) |
| 购买                                                | [官方淘宝店](https://szdoit.taobao.com/)(szdoit.am)          |
| 讨论                                                | [技术论坛](http://bbs.doit.am/forum.php)(bbs.doit.am)        |
| 应用案例集锦                                        |                                                              |
| [Doit玩家云](http://wechat.doit.am)(wechat.doit.am) | [免费TCP公网调试服务](http://tcp.doit.am)(tcp.doit.am)       |
| 官方技术支持QQ群1/2/3群已满                         |                                                              |
| 技术支持群4                                         | 278888904                                                    |
| 技术支持群5                                         | 278888905                                                    |
| 术支持群6                                           | 278888906                                                    |
| 技术支持群7                                         | 278888907                                                    |
| 技术支持群8                                         | 278888908                                                    |
| 技术支持群9                                         | 278888909                                                    |
| 技术支持群10                                        | 278888900                                                    |