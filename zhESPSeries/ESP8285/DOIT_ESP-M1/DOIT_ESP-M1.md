<center><font size=10> ESP-M1模块数据手册</center></font>
<center> From SZDOIT</center>

## 一. 产品概述

ESP-M1模块核心处理器采用高性价比芯片ESP8285。该芯片在较小尺寸封装中集成了增强版的Tensilica’s L106钻石系列32-bit内核处理器，带片上SRAM。ESP8285拥有完整的Wi-Fi网络功能，既能够独⽴应⽤，也可以作为从机搭载于其他主机MCU运⾏。当ESP8285托管应用时，能够直接从外接Flash中启动。内置的⾼速缓冲存储器有利于提⾼系统性能，并且优化存储系统。此外ESP8285只需通过SPI/SDIO接⼝或I2C/UART⼝即可作为Wi-Fi适配器，应⽤到基于任何微控制器的设计中。

![wps11](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps11.png)

ESP-M1模块支持标准的IEEE802.11 b/g/n/e/i协议以及完整的TCP/IP协议栈。用户可以使用该模块为现有设备添加联网功能，也可以构建独立的网络控制器。

ESP-M1模块以最低成本提供最大实用性，为Wi-Fi功能嵌入其他系统提供无限可能。

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps1.png)

 

图1.1 模块结构图



模块主要技术参数如下：

表1.1 模块主要参数

| 分类                       | 项目                                   | 参数                          |
| -------------------------- | -------------------------------------- | ----------------------------- |
| Wi-Fi                      | 频率范围                               | 2.4G~2.5G(2400M~2483.5M)      |
| 发射功率                   | 802.11b: +20 dBm                       |                               |
| 802.11g: +17 dBm           |                                        |                               |
| 802.11n: +14 dBm           |                                        |                               |
| 接收灵敏度                 | 802.11b: -91 dbm (11Mbps)              |                               |
| 802.11g: -75 dbm（54Mbps） |                                        |                               |
| 802.11n: -72 dbm（MCS7）   |                                        |                               |
| 天线                       | PCB板载天线                            |                               |
| 硬件                       | CPU                                    | Tensilica L106 32 bit微控制器 |
| 外设                       | UART/SDIO/SPI/I2C/I2S/IR遥控           |                               |
| GPIO/ADC/PWM/SPI/I2C/I2S   |                                        |                               |
| 工作电压                   | 2.5V ~ 3.6V                            |                               |
| 工作电流                   | 平均电流：80 mA                        |                               |
| 工作温度                   | -40°C ~ 85°C                           |                               |
| 环境温度范围               | -40°C ~ 125°C                          |                               |
| 封装大小                   | 16mm x 24mm x 3mm                      |                               |
| 软件                       | Wi-Fi 模式                             | Station/SoftAP/SoftAP+Station |
| 安全机制                   | WPA/WPA2                               |                               |
| 加密类型                   | WEP/TKIP/AES                           |                               |
| 升级固件                   | UART Download/OTA（通过网络）          |                               |
| 软件开发                   | Non-RTOS/RTOS/Arduino IDE等            |                               |
| 网络协议                   | IPv4、TCP/UDP/HTTP/FTP/MQTT            |                               |
| 用户配置                   | AT+ 指令集/云端服务器/ Android/iOS APP |                               |

## 二. 接口定义

ESP-M1接口定义如下图所示。

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps2.png)

图2.1 ESP-M1管脚定义

模块的工作模式选择和每个管脚定义如下表所示。

表2.1 引脚模式

| 模式           | GPIO15（模块内部已对地接电阻） | GPIO0 | GPIO2 |
| -------------- | ------------------------------ | ----- | ----- |
| UART下载模式   | 低                             | 低    | 高    |
| Flash Boot模式 | 低                             | 高    | 高    |

表2.2 模块管脚功能定义

| 序 号 | Pin脚名称 | 类型 | 功能说明                                                     |
| ----- | --------- | ---- | ------------------------------------------------------------ |
| 1     | ADC       | I    | A/D转换管脚。输入电压范围0~1V，取值范围：0~1024              |
| 2     | EN        | I    | 芯⽚使能端，⾼电平：有效，芯⽚正常⼯作；低电平：芯⽚关闭，电流很⼩ |
| 3     | IO14      | I/O  | GPIO14; HSPI_CLK                                             |
| 4     | IO12      | I/O  | GPIO12;HSPI_MISO                                             |
| 5     | IO13      | I/O  | GPIO13;HSPI_MOSI; UART0_CTS                                  |
| 6     | IO15      | I/O  | GPIO15; MTDO;HSPICS;UART0_RTS; 模块内部已对地接电阻          |
| 7     | VCC       | P    | 模块电源：3.3V                                               |
| 8     | GND       | P    | GND                                                          |
| 9     | IO2       | I/O  | GPIO2; UART1_TXD;                                            |
| 10    | IO0       | I/O  | GPIO0; SPI_CS2;                                              |
| 11    | IO4       | I/O  | GPIO4                                                        |
| 12    | IO5       | I/O  | GPIO5                                                        |
| 13    | RXD       | I/O  | GPIO3; 可⽤作烧写 Flash 时 UART Rx                           |
| 14    | TXD       | I/O  | GPIO1; 可⽤作烧写 Flash 时 UART Tx                           |
| 15    | RST       | I    | 外部重置信号（低电平有效）, 复位模块; 模块内部已接上拉电阻   |
| 16    | GND       | P    | GND                                                          |

## 三. 外型与尺寸

模块的外观及尺寸如下所示。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps3.jpg) ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps4.jpg)

图3.1 ESP-M1模块外观

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps5.jpg) 

图3.2 ESP-M1尺寸图

表3.1 ESP-M1模块尺寸对照表

| 长     | 宽   | 高   | PAD  尺寸（底部） | Pin  脚间距 |
| ------ | ---- | ---- | ----------------- | ----------- |
| 12.3mm | 15mm | 3 mm | 0.9 mm x 1.7mm    | 1.5 mm      |

## 四. 电气特性

表4.1 电气特性

| 参数                   | 条件                | 最小值   | 典型值       | 最大值   | 单位        |      |
| ---------------------- | ------------------- | -------- | ------------ | -------- | ----------- | ---- |
| 存储温度范围           | -                   | -40      | 正常温度     | 125      | ℃           |      |
| 最大焊接温度           | IPC/JEDEC J-STD-020 | -        | -            | 260      | ℃           |      |
| 工作电压               | -                   | 2.5      | 3.3          | 3.6      | V           |      |
| I/O                    | VIL/VIH             | -        | -0.3/0.75VIO | -        | 0.25VIO/3.6 | V    |
| VOL/VOH                | -                   | N/0.8VIO | -            | 0.1VIO/N |             |      |
| IMAX                   | -                   | -        | -            | 12       | mA          |      |
| 静电释放量（人体模型） | TAMB=25℃            | -        | -            | 2        | KV          |      |
| 静电释放量（人体模型） | TAMB=25℃            | -        | -            | 0.5      | KV          |      |

## 五. 功耗

表5.1 功耗

| 参数                                  | 最小值 | 典型值 | 最大值 | 单位 |
| ------------------------------------- | ------ | ------ | ------ | ---- |
| Tx802.11b, CCK 11Mbps, POUT=+17dBm    | -      | 170    | -      | mA   |
| Tx802.11g, OFDM 54 Mbps, POUT =+15dBm | -      | 140    | -      | mA   |
| Tx802.11n,MCS7,POUT =+13dBm           | -      | 120    | -      | mA   |
| Rx 802.11b，1024 Bytes包⻓，-80dBm    | -      | 50     | -      | mA   |
| Rx 802.11g，1024 Bytes包⻓，-70dBm    | -      | 56     | -      | mA   |
| Rx 802.11n，1024 Bytes包⻓，-65dBm    | -      | 56     | -      | mA   |
| Modem-sleep①                          | -      | 15     | -      | mA   |
| Light-sleep②                          | -      | 0.9    | -      | mA   |
| Deep-sleep③                           | -      | 20     | -      | μA   |
| 关闭                                  | -      | 0.5    | -      | μA   |

注①：Modem-Sleep模式用于需要CPU一直处于工作的场景，如应用于PWM或I2S应用等。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路来省电。例如在DTIM3时，保持睡眠300ms，醒来3ms间隔唤醒来接收AP的Beacon包，则电流约15mA。

注②：Light-Sleep模式用于CPU可暂停的应用，如Wi-Fi开关。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路并暂停CPU来省电。例如，在DTIM3时，保持睡眠300ms，每3ms间隔唤醒来接收AP的Beacon包，则整体平均电流约0.9mA。

注③：Deep-Sleep模式应用于不需一直保持Wi-Fi连接的场景，很长时间才发送一次数据包的应用（如每100秒测量⼀次温度的传感器），每300s 醒来后需0.3s-1s连上AP，则整体平均电流可远小于1mA。

## 六. Wi-Fi射频特征

下表中数据是在室内温度下，电压为3.3V和1.1V时分别测得。

表6.1 Wi-Fi视频特征

| 参数                           | 最小值 | 典型值 | 最大值 | 单位 |
| ------------------------------ | ------ | ------ | ------ | ---- |
| 输入频率                       | 2412   | -      | 2484   | MHz  |
| 输入阻抗                       | -      | 50     | -      | Ω    |
| 输入反射                       | -      | -      | -10    | dB   |
| 72.2Mbps下，PA的输出功耗       | 15.5   | 16.5   | 17.5   | dBm  |
| 11b模式下，PA的输出功耗        | 19.5   | 20.5   | 21.5   | dBm  |
| 灵敏度                         | -      | -      | -      | -    |
| DSSS, 1Mbps                    | -      | -98    | -      | dBm  |
| CCK11, Mbps                    | -      | -91    | -      | dBm  |
| 6Mbps(1/2 BPSK)                | -      | -93    | -      | dBm  |
| 54Mbps(3/4 64-QAM)             | -      | -75    | -      | dBm  |
| HT20, MCS7(65 Mbps, 72.2 Mbps) | -      | -72    | -      | dBm  |
| 邻道抑制                       |        |        |        |      |
| OFDM, 6Mbps                    | -      | 37     | -      | dB   |
| OFDM, 54Mbps                   | -      | 21     | -      | dB   |
| HT20, MCS0                     | -      | 37     | -      | dB   |
| HT20, MCS7                     | -      | 20     | -      | dB   |

## 七. 推荐炉温曲线

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps6.jpg) 

图7.1 推荐炉温曲线

## 八. 模块最小系统

模块最小系统电路图如下：

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps7.jpg) 

图8.1 最小系统

注：

（1）模块供电电压为直流3.3V；

（2）Wi-Fi模块IO最大输出电流为12mA；

（2）Wi-Fi模块NRST管脚低电平有效；EN使能管脚高电平有效；

（4）Wi-Fi模块进入升级模式：GPIO0处于低电平，然后模块复位上电；Wi-Fi模块进入正常工作模式：GPIO0处于高电平，模块复位上电。

（5）Wi-Fi模块的RXD接外部MCU的TXD，Wi-Fi模块的TXD接外部MCU的RXD；

## 九 推荐PCB设计

Wi-Fi模块可以直接焊接到PCB板上。为了使您的终端产品获得最佳的射频性能，请注意根据本指南合理设计模块及天线在底板上的摆放位置。

针对PCB天线版本ESP-M2建议将模块沿PCB板边放置，天线在板框外或者沿板边放置且下方挖空，参考方案一及方案二；若必须将PCB天线放在底板上，则需要保证天线下方的PCB区域不可敷铜，参考方案三。

针对外置天线版本ESP-M1，由于天线外置，对模块摆放位置要求不高，可参考ESP-M2的布置建议酌情调整。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps8.png)

图9.1 方案一-天线在板框外

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps9.png)

图9.2 方案二-天线沿板边放置且下方挖空

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_ESP-M1/wps10.png)

图9.3 方案三-天线沿板边放置且下方均不铺铜

 

## 十. 外围走线建议

Wi-Fi模块集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和EMI特性要求较高，建议在数字I/O线上串联10 ~100欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳，同时这种做法也能在一定程度上防止静电释放（ESD）。 



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

## 免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明。

## 注意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。