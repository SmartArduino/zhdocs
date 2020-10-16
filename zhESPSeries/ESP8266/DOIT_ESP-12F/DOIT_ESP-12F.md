<center><font size=10> ESP-12F模块数据手册</center></font>
<center> From SZDOIT</center> 

# 一、概述 

ESP-12F WiFi 模块是一款低功耗高性价比的嵌入式无线网络控制模块。可满足智能电网、楼宇自动化、安防、智能家居、远程医疗等物联网应用的需求。 

该模块核心处理器 ESP8266 在较小尺寸封装中集成了业界领先的 Tensilica L106 超低功耗 32 位微型 MCU，带有 16 位精简模式，主频⽀持 80 MHz 和 160 MHz，支持 RTOS，集成 Wi-Fi MAC/ BB/RF/PA/LNA，板载天线。 

该模块支持标准的 IEEE802.11 b/g/n 协议，完整的 TCP/IP 协议栈。用户可以使用该模块为现有的设备添加联网功能，也可以构建独立的网络控制器。 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps3.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps4.jpg) 

图-1  对比图（立体图）

# 二、主要特性 

## 2.1 系统架构

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps5.png)

## 2.2 硬件参数 

• 工作电压：3.3V （3.0 ~ 3.6V） 

• 工作环境温度：-40 - 85°C 

• CPU Tensilica L106 

o RAM 	50KB（可用） 

o Flash 	32Mbit 

• 系统 

o 802.11 b/g/n  

o 频率范围 2.4 GHz ~ 2.5 GHz（2400 MHz ~ 2483.5 MHz） 

o 内置 Tensilica L106 超低功耗 32 位微型 MCU，带有 16 位精简模式，主频支持 80 MHz 和 160 

MHz，支持 RTOS

o WIFI @2.4 GHz，支持 WPA/WPA2 安全模式 

o 支持 UART、I2C、GPIO、PWM、SDIO、SPI、ADC、PWM、IR 

o 内置 10 bit 高精度 ADC 

o 支持 TCP、UDP、HTTP、FTP 

o 内置 TR 开关、 balun、 LNA、功率放大器和匹配网络 

o 内置 PLL、稳压器和电源管理组件 802.11b 模式下+ 20 dBm 的输出功率 

o 平均工作电流 80mA，深度睡眠保持电流为 20uA，关断电流小于 5uA 

o 可以兼作应用处理器 SDIO 2.0、 SPI、 UART 

o 2ms 之内唤醒、连接并传递数据包 

o 待机状态消耗功率小于 1.0mW (DTIM3) 

o 支持本地串口烧录、云端升级、主机下载烧录 

o 支持 Station / SoftAP / SoftAP + Station 无线网络模式

o 模组尺寸 24mm  16mm  3mm 

# 三、引脚描述 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps6.jpg) 

图-3 管脚图（正视图）

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps7.png) 

​	图-4 模块尺寸（侧视图） 

表-1 引脚定义及描述 

| 引脚 	名称 | 描述 |                                                              |
| ------------- | ---- | ------------------------------------------------------------ |
| 1             | RST  | 复位模组                                                     |
| 2             | ADC  | ADC 转换结果，输入电压范围：0 - 1V，取值范围：0 - 1024       |
| 3             | EN   | 芯片使能端 高电平：有效，模块正常工作；低电平：芯片关闭，电流很小； |
| 4             | IO16 | GPIO16；接到 RST 管脚时可做 deep sleep 的唤醒                |
| 5             | IO14 | GPIO14；HSPI_CLK                                             |
| 6             | IO12 | GPIO12；HSPI_MISO                                            |
| 7             | IO13 | GPIO13； HSPI_MOSI；UART0_CTS                                |
| 8             | VCC  | 3.3V 供电（VDD） 注意：外部供电电源的最大输出电流建议在 500mA 以上； |
| 9             | CS0  | 片选                                                         |
| 10            | MISO | 从机输出主机注入                                             |
| 11            | IO9  | GPIO9                                                        |
| 12            | IO10 | GPIO10                                                       |
| 13            | MOSI | 主机输出从机输入                                             |
| 14            | SCLK | 时钟                                                         |
| 15            | GND  | 接地                                                         |
| 16            | IO15 | GPIO15；MTDO；HSPICS；UART0_RTS                              |
| 17            | IO2  | GPIO2；UART1_TXD                                             |
| 18            | IO0  | GPIO0                                                        |
| 19            | IO4  | GPIO4                                                        |
| 20            | IO5  | GPIO5                                                        |
| 21            | RXD  | UART0_RXD； GPIO3                                            |
| 22            | TXD  | UART0_TXD；GPIO1                                             |

# 四、功能描述 

## 4.1 MCU 

ESP8266EX 内置 Tensilica L106 超低功耗 32 位微型 MCU，带有 16 位精简模式，主频支持 80MHz 和 160MHz，支持 RTOS。目前 WiFi 协议栈只用了 20%的处理能力，其余可以用来做应用开发。MCU 可通过以下接口和芯片其他部分协同工作： 

• 连接存储控制器、也可以用来访问外界 Flash 的编码 RAM/ROM 接口（iBus）； 

• 连接存储控制器的数据 RAM 接口（dBus）; 

• 访问控制器的 AHB 接口； 

## 4.2 存储 

### 4.2.1 内置 SRAM 与 ROM 

基于 Demo SDK 的使用 SRAM 情况，用户可用剩余 SRAM 空间为： 

• RAM < 50 kB（Station 模式下，连上路由后，Heap + Data 区大致可有 50kB 左右）。 

• 目前 ESP8266EX 片上没有可编程 ROM，用户程序存放在 SPI Flash 中。 

### 4.2.2 SPI Flash 

• ESP8266EX 芯片支持使用 SPI 接口的外置 FLASH，理论最大支持 16MB 的 SPI Flash。 

• ESP-12F 模块配置了 32Mbit 的 SPI Flash，可满足一般客户的使用需求。 

## 4.3 接口定义及描述 

表-2 接口定义及描述 

| 接口      | 引脚                                                         | 描述                                                         |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| SPI 接口  | IO12(MISO),IO13(MOSI), IO14(CLK),IO15(CS)                    | 可以作为主机读写 SPI 从设备，也可以作为从机与外部单片机通信。在 overlap 模式下，可以与 Flash 共用 SPI 引脚，通过不同的 CS 进行切换 |
| PWM 接口  | IO12(R),IO15(G),IO13(B)                                      | 官方 demo 中提供 4 路 PWM (用户可扩展 8 路)，可用来控制彩灯，蜂鸣器，继电器及电机等 |
| IR 接口   | IO14(IR_T), IO5(IR_R)                                        | IR Remote Control 接口由软件实现，接口使用 NEC 编码及调制解调，采用 38KHz 的调制载波。 |
| ADC 接口  | TOUT                                                         | 可用于检测 VDD3P3 (Pin3,Pin4) 电源电压和 TOUT (Pin6)的输入电压 (二者不可同时使用)。可用于传感器等应用 |
| I2C 接口  | IO14(SCL), IO2(SDA)                                          | 可外接传感器及显示屏等                                       |
| UART 接口 | UART0: TXD(U0TXD),RXD(U0RXD),IO15(RTS),IO13(CTS)             | 可外接 UART 接口的设备 下载：U0TXD+U0RXD 或者 GPIO2+U0RXD 通信(UART0):U0TXD,U0RXD,MTDO(U0RTS),MTCK(U0CTS) Debug：UART1_TXD(GPIO2)可作为 debug 信息的打印 |
|           | UART1: IO2(TXD)                                              | UART0 在 ESP8266-12S 上电默认会输出一些打印信息。对此敏感的应用，可以使用 UART 的内部引脚交换功能，在初始化的时候，将 U0TXD,U0RXD 分别与 U0RTS;U0CTS 交换。硬件上将 MTDOMTCK 连接到对应的外部 MCU 的串口进口通信 |
| I2S 接口  | I2S 输入： IO12 (I2SI_DATA); IO13 (I2SI_BCK ); IO14 (I2SI_WS); ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps8.png)I2S 输出: IO15 (I2SO_BCK ); IO3 (I2SO_DATA); IO2 (I2SO_WS ); | 主要用于音频采集、 处理和传输                                |

# 五、电气特性 

## 5.1 功耗 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps9.png) 

| Deep Sleep                              | 20uA  |
| --------------------------------------- | ----- |
| Off                                     | 0.5uA |
| 正常工作（平均）                        | 80mA  |
| 传送 801.11b，CCK 11Mbps，Pout=+17 dBm  | 170mA |
| 传送 801.11g，OFDM 54Mbps，Pout=+15 dBm | 140mA |
| 传送 801.11n，MCS7，Pout=+13 dBm        | 120mA |
| 接收 801.11b，包长 1024 字节，-80 dBm   | 50mA  |
| 接收 801.11g，包长 1024 字节，-70 dBm   | 56mA  |
| 接收 801.11n，包长 1024 字节，-65 dBm   | 56mA  |

​    注①： Modem-Sleep ⽤于需要 CPU⼀直 处于⼯作状态 如 PWM 或 I2S 应⽤等。在保持 WiFi 连接时，如

果没有数据传输，可根据 802.11 标准 (如 U-APSD)，关闭 WiFi Modem 电路来省电。例如，在 DTIM3 时，每 sleep 300mS，醒来 3mS 接收 AP 的 Beacon 包等，则整体平均电流约 15mA。 

​     注②： Light-Sleep ⽤于 CPU 可暂停的应⽤，如 WiFi 开关。在保持 WiFi 连接时，如果没有数据传输，可根据 802.11 标准 (如 U-APSD)，关闭 WiFi Modem 电路并 暂停 CPU 来省电。例如，在 DTIM3 时，每 sleep 

300 ms，醒来 3ms 接收 AP 的 Beacon 包等，则整体平均电流约 0.9 mA。 

注③： Deep-Sleep 不需⼀直保持 WiFi 连接，很长时间才发送⼀次数据包的应⽤，如每 100 秒测量⼀次温度的传感器。例如，每 300 s 醒来后需 0.3s - 1s 连上 AP 发送数据,则整体平均电流可远⼩于 1 mA。 

以上功耗数据是基于 3.3V 的电源、25°的环境温度下，并使用内部稳压器测得： 

• 所有发射数据是基于 90% 的占空比，在持续发射的模式下测得。 

• 所有测量数据是基于没有 SAW 滤波器的情况，在天线接口处测试。 

## 5.2 RF 特性 

表-4 射频参数 

| 描述                           | 最小值 | 典型值     | 最大值 | 单位 |
| ------------------------------ | ------ | ---------- | ------ | ---- |
| 输入频率                       | 2400   | /          | 2483.5 | MHz  |
| 输入阻抗值                     | /      | 50         | /      | ohm  |
| 输入反射值                     | /      | /          | -10    | dB   |
| PA 输出功率为 72.2 Mbps        | 15.5   | 16.5       | 17.5   | dBm  |
| 11b 模式下 PA 输出功率         | 19.5   | 20.5       | 21.5   | dBm  |
|                                |        | 接收灵敏度 |        |      |
| CCK，1Mbps                     | /      | -98        | /      | dBm  |
| CCK，11Mbps                    | /      | -91        | /      | dBm  |
| 6Mbps（1/2 BPSK）              | /      | -93        | /      | dBm  |
| 54Mbps（3/4 64-QAM）           | /      | -75        | /      | dBm  |
| HT20，MCS7（65Mbps，72.2Mbps） | /      | -72        | /      | dBm  |
|                                |        | 领频抑制   |        |      |
| OFDM，6Mbps                    | /      | 37         | /      | dB   |
| OFDM，54Mbps                   | /      | 21         | /      | dB   |
| HT20，MCS0                     | /      | 37         | /      | dB   |
| HT20，MCS7                     | /      | 20         | /      | dB   |

 

## 5.3 数字端口特征 

表-5 数字端口特征 

| 端口           | 典型值              | 最小值          |      | 最大值    | 单位 |
| -------------- | ------------------- | --------------- | ---- | --------- | ---- |
| 输入逻辑电平低 | VIL                 | -0.3            |      | 0.25 VDD  | V    |
| 输入逻辑电平高 | VIH                 | 0.75 VDD        |      | VDD + 0.3 | V    |
| 输出逻辑电平低 | VOL                 | N               |      | 0.1 VDD   | V    |
| 输出逻辑电平高 | VOH                 | 0.8 VDD         |      | N         | V    |
| 5.4 最大额定值 |                     | 表-6 最大额定值 |      |           |      |
| 额定值         | 条件                |                 | 值   |           | 单位 |
| 存储温度       | /                   | -40 to 125      | °C   |           |      |
| 最大焊接温度   | /                   | 260             | °C   |           |      |
| 供电电压       | IPC/JEDEC J-STD-020 | +3.0 to +3.6    | V    |           |      |

 

## 5.5 倾斜升温 

表-7 倾斜升温 

| 接口                                                         | 描述                          |
| ------------------------------------------------------------ | ----------------------------- |
| 倾斜升温速率（Ts Max. 至 TL）                                | 最大值 3°C/秒                 |
| 预热最小温度值（Ts Min.）典型温度值（Ts Typ.）最大温度值（Ts Max.）时间（Ts ） | 150°C 175°C 200°C 60 ~ 180 秒 |
| 倾斜升温速率（TL至Tp）                                       | 最大值 3°C/秒                 |
| 以上持续时间：温度（TL）/ 时间（TL）                         | 270°C / 60 ~ 150 秒           |
| 温度峰值（Tp）                                               | 最高温度值 260 °C，持续 10 秒 |
| 目标温度峰值（Tp 目标值）                                    | 260°C + 0 / -5°C              |
| 在持续峰值（Tp）5°C 以内持续的时间                           | 20 ~ 40 秒                    |
| 倾斜降温速率（TsMax.至 TL）                                  | 最大值 6°C / 秒               |
| 从 25°C 调制温度峰值所需时间（t）                            | 最长 8 分钟                   |

 

# 六、原理图 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps10.jpg) 

图-5 ESP-12F 原理图

# 七、最小系统 

 

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps11.jpg) 

图-6 ESP-12F 最小系统图 

 

说明 

1) 模块 IO 最大输出电流为 12 mA； 

2) 模块电源典型值为 3.3 V DC； 

3) 模块低电平复位有效； 

4) 模块固件在线升级需要在满足 3）的条件下，IO0 拉低，并复位模块；固件升级完成后，IO0 释放，

并复位模块； 

5) 模块的 RXD 接 MCU 的 TXD，模块的 TXD 接 MCU 的 RXD； 

# 八、推荐 PCB 设计 

ESP-12F模组可以焊接到 PCB 板上。为了使终端产品获得最佳的射频性能，请注意根据本指南合理设计模组及天线在底板上的摆放位置。 

建议将模组沿 PCB 板边放置，天线在板框外或者沿板边放置且下方挖空，参考方案 1 及方案 2；将

PCB 天线放在底板上也是允许的，只要天线下方不铺铜即可，参考方案 3。 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps12.jpg) 

 方案 1：天线在板框外 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps13.jpg) 

 方案 2：天线沿板边放置且下方挖空 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/DOIT_ESP-12F/wps14.jpg) 

 方案 3：天线沿板边放置且下方均不铺铜 

 

# 九、外围走线建议 

ESP-12F 集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和

EMI 特性要求较高，建议在数字 I/O 线上串联 10 ~ 100 欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳。串联电阻也能在一定程度上防止静电释放（ESD）。 

#  十、支持与服务

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

# 十一、免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明。

# 十二、注意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。
