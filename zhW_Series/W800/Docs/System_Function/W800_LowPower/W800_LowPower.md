<center><font size=10> W800_低功耗使用指导 </center></font>
<center> From SZDOIT</center>

## 1 引言

### 1.1 编写目的

介绍 W800 芯片低功耗配置和相应适用场景，并提供相应的测试示例。

### 1.2 预期读者

W800 所有使用者。

### 1.3 术语定义

AP：Access Point，类似于普通的无线路由器

Station：接入 AP 的无线客户端

RTC：Real Time Clock， 实时时钟

DTIM：Delivery Traffic Indication Message，AP 的广播帧暂存周期

PMU：power management unit，电源管理单元

GPIO：General-purpose input/output，通用型之输入输出

MCU：Micro Control Unit，单片机（上位机）

## 2 概述

目前 W800 系列芯片在 Station 模式下有 PS-Mode（Power Sleep）、Sleep 和 Standby 三种低功耗模式，针对这三种模式我们提供了多种配置方法，用户可以结合具体需求选择相应模式并进行配置。

这三种低功耗模式区别如下：

![image-20201114100739746](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114100739746.png)

说明：

1.DTIM 在部分 AP 上是可以配置的，该值设置越大 Station 可以睡眠更长时间来降低功耗。
2.PS-Mode 模式下未联网时 WiFi 是关闭的。

## 3 Wi-Fi OFF 模式

W800 启动后，不处于联网、扫描或配网状态时，WiFi 是关闭的。此时，只有 CPU 及部分外设处于工作状态。
Wi-Fi OFF 可以认为是 W800 仅作为 MCU 使用的一种工作模式。

## 4 PS-Mode 模式

W800 在连接 AP 以后，会在 AP 广播 Beacon 帧的两次 DTIM 间隔时间内，关闭 WiFi 以达到省电效果，在下次 Beacon 帧到来前自动唤醒并打开 WiFi，睡眠时间由 AP 的 DTIM 时间决定。

### 4.1 进入 PS-Mode

#### 4.1.1 SDK API

通过使用接口 void tls_wifi_set_psflag(bool enable, bool alwaysflag)来设置，接口说明请参阅API 说明。
该接口需要在芯片联网拿到 IP 之后设置效，睡眠之后由系统自行决定何时被唤醒。

#### 4.1.2 AT 指令

通过使用 AT 指令 AT+WPSM 来完成设置，指令说明请参阅 AT 指令手册。

联网模式下测试，如需保存节能标志，AT+WPSM=!1

指令：AT+WPSM（STA PS-POLL 功能使能/关闭）

功能：

打开/关闭自动节能模式。

格式（ASCII）：

![image-20201114100904521](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114100904521.png)

参数：
enable：使能标志，定义如下：

![image-20201114100936744](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114100936744.png)

### 4.2 使用场景

该模式适用于需要 CPU 一直工作的场景。

## 5 Sleep 模式

Sleep 模式是能够快速唤醒的一种低功耗工作模式。在此模式下，数字电路的电源仍将保持开启状态，因此内存，寄存器等内容将保持，在唤醒后能够快速连接。但起振电路与 DPLL 将关闭，整个系统时钟将停止，以减少电路内动态功耗。

唤醒可以通过 GPIO 唤醒，连接 W800 的 wakeup（GPIO_A4）引脚，把 wakeup 脚拉高即可完成唤醒。

唤醒也可以通过定时器（PMU-Timer 或 RTC 定时器）唤醒，定时器超时之后即可完成唤醒。

### 5.1 进入 Sleep

#### 5.1.1 SDK API

通过使用接口 void tls_pmu_sleep_start(void)来进入睡眠。

该模式下，只能通过 GPIO 和定时器唤醒：

GPIO 由 wakeup 引脚给予高电平唤醒；

PMU 定时器唤醒通过接口 void tls_pmu_timer0_start(u16 second) 或 voidtls_pmu_timer1_start(u16 msec)设置使用。

接口 void tls_pmu_timer0_start(u16 second)可以设置的时间单位为秒；

接口 void tls_pmu_timer1_start(u16 msec) 可以设置的时间单位为毫秒；

#### 5.1.2 AT 指令

通过使用 AT 指令 AT+ENTS 来完成设置，指令说明请参阅 AT 指令手册。

指令：AT+ENTS（低功耗测试）

功能：

设置系统进入节能模式（休眠/待机状态）。

格式（ASCII）：

![image-20201114101107959](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101107959.png)

参数：
ps_type：节能模式，定义如下：

![image-20201114101130680](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101130680.png)

wake_type： Standby/Sleep 唤醒模式，定义如下：

![image-20201114101152550](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101152550.png)

delay_time：进入 Standby/Sleep模式的延时时间，单位 10ms，有效值100 ～10000ms；

wake_time：在Standby/Sleep模式下的唤醒时间，仅当 Timer 方式唤醒时有效，单位ms，有效值1000 ～65535ms。

### 5.2 使用场景

该模式适用于保持 WiFi 连接时需要较低功耗的场景。设备可以每隔一段时间从 Sleep 状态唤醒向MCU 完成交互之后继续进入 Sleep 睡眠。

注意：在 Sleep 模式下联网时仍可以启用 PS-Mode 以降低联网通信时的功耗。

## 6 Standby 模式

Standby 模式为最低功耗工作模式，在此模式下，除了 PMU 电源域的电路工作以外，所有芯片内电路都将关闭。所以该模式下 W800 只有 RTC 还在工作，其他一切都是不可用的，每次唤醒之后W800 都会重启。

唤醒可以通过 GPIO 唤醒，连接 W800 的 wakeup（GPIO_A4）引脚，把 wakeup 脚拉高即可完成唤醒。

唤醒也可以通过定时器（PMU-Timer 或 RTC 定时器）唤醒，定时器超时之后即可完成唤醒。

### 6.1 进入 Standby

#### 6.1.1 SDK API

通过使用接口 void tls_pmu_standby_start(void)来进入睡眠。

该模式下，只能通过 GPIO 和定时器唤醒：

GPIO 由 wakeup 引脚给予高电平唤醒；

PMU 定时器唤醒通过接口 void tls_pmu_timer0_start(u16 second) 或 voidtls_pmu_timer1_start(u16 msec)设置使用。

接口 void tls_pmu_timer0_start(u16 second)可以设置的时间单位为秒；

接口 void tls_pmu_timer1_start(u16 msec) 可以设置的时间单位为毫秒；

#### 6.1.2 AT 指令

通过使用 AT 指令 AT+ENTS 来完成设置，指令说明请参阅 AT 指令手册。

指令：AT+ENTS（低功耗测试）

功能：

设置系统进入节能模式（休眠/待机状态）。

格式（ASCII）：

![image-20201114101348270](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101348270.png)

参数：
ps_type：节能模式，定义如下：

![image-20201114101407150](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101407150.png)

wake_type： Standby/Sleep 唤醒模式，定义如下：

![image-20201114101429742](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101429742.png)

delay_time：进入 Standby/Sleep模式的延时时间，单位 10ms，有效值100 ～10000ms；

wake_time：在Standby/Sleep模式下的唤醒时间，仅当 Timer 方式唤醒时有效，单位ms，有效值1000 ～65535ms。

### 6.2 使用场景

该模式适用于传感器应用或者大部分时间都不需要进行数据传输的场景。设备可以每隔一段时间从Standby 状态醒来测量数据并上传，之后继续进入 Standby。

## 7 低功耗其它配置

在联网时，我们还可以通过以下几种配置来降低使用功耗：

### 7.1 降低 cpu 主频

使用接口 void tls_sys_clk_set(u32 clk)将 CPU 设置为较低的频率，目前可用的频率有：

Wi-Fi 可用时，CPU 时钟：240MHz,160MHz，80MHz，40MHz

Wi-Fi 不可用时，CPU 时钟可配置为小于 40MHz 的时钟，最小可配置到 2MHz

### 7.2 关闭未用的外设时钟

使用接口 void tls_close_peripheral_clock(tls_peripheral_type_s devices)关闭未使用的外设时钟；

该接口中参数可以使用“|”同时关闭多个外设时钟，具体可关闭项目可查看 tls_peripheral_type_s定义的枚举类型。

## 8 各功耗模式测试示例

### 8.1 测试相关设备和说明

①W800 开发板

![image-20201114101558799](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101558799.png)

由于测试的是 W800 SOC 本身功耗，所以，在测试之前，将 W800 开发板本身对功耗存在影响的相关器件去除，具体如下：

A→ Reset 和 Wakeup 两个按键处的上拉电阻去除，如图 1 中标记序号 1 和 2；

B→ 为避免电容充放电过程对测试功耗的干扰，将 W800 开放板上相关电容去除，如图 1 中标记序号 3~9。
特别说明：

由于 Wakeup 按键的上拉电阻被拆除，造成该板无法通过 GPIO 方式将处于 Standby或 Sleep 状态的 W800 唤醒。

②电源输入设备

![image-20201114101651797](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101651797.png)

使用 Agilent 66319D 向 W800 提供 3.3V 稳定电源输入。
③电流计量设备

![image-20201114101711325](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101711325.png)

使用 Agilent 34401A 串入 66319D 向 W800 的供电电路中，以精确记录经过 W800的电流。

④Agilent 14565A DCS 软件

![image-20201114101747182](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101747182.png)

通过该软件对 66319D 设备的操控，可自动记录和计算 W800 的精确电流数据。

### 8.2 Standby 模式测试

该模式的测试连接图如下，即 34401A 串入 66319D 向 W800 的供电电路中，如下图：

![image-20201114101816262](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101816262.png)

#### 8.2.1 测试步骤

通过串口连入 W800，依次输入下列 AT 指令：

AT+RSTF ---将 W800 恢复出厂设置

AT+Z ---将 W800 复位

AT+ENTS=1, 1, 5000, 30000 ---设置 W800 在 5 秒后进入 Standby 状态并持续 30 秒

#### 8.2.2 测试结果

完成上述命令并等待 8 秒后，在 34401A 上将 RNAGE Level 调制 mA 档位，即可看到如图 5 中的 9uA。

### 8.3 Sleep 模式测试

该模式的测试连接图如下，即 66319D 直接向 W800 供电。

![image-20201114101916125](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114101916125.png)

8.3.1 测试步骤
* 66319D 上电后，依次按键 Recall 和 Enter；



* 打开 14565A DCS 软件，选择 IO type 并点击 Auto-Detect 键，进入操控界面。
按照图 7 内执行序号依次设置到 6，然后通过串口连接 W800，并依次输入如下 AT
指令：

AT+RSTF ---将 W800 恢复出厂设置

AT+Z        ---将 W800 复位

AT+ENTS=2, 1, 5000, 30000 ---设置 W800 在 5 秒后进入 Sleep 状态并持续30 秒。

完成上述命令，等待 8 秒后，按照图 7 中执行序号 7 和 8，即可获得 W800 在 sleep状态下的电流数据

![image-20201114102042318](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114102042318.png)

#### 8.3.2 测试结果

打开保存的数据文件预览如下：

![image-20201114102104796](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_LowPower/image-20201114102104796.png)

### 8.4 PS-Mode 模式测试

该模式开发调试中，稍后提供。

# 支持与服务

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