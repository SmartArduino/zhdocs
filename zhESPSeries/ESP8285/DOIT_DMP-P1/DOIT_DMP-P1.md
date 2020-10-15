 <center> <font size=10> DMP-P1模块数据手册 </font></center>

<center> from SZDOIT </center> 

# 特点

##  模组特性

内置ESP WiFi芯片

支持多达四路继电器控制

支持本地局域网优先控制

支持云控制

支持Google Assistant、Amazon Alexa、天猫精灵、小度智能、京东叮咚、小爱同学等多种音箱

支持Android和iOS设备控制

##  Wi-Fi特性

支持802.11 b/g/n/e/i

支持ESP-Touch智能配网模式和AP配网模式

支持OTA远程升级

支持批量生产测试

# 模块信息

继电器控制引脚：4

工作温度范围：-40℃-105℃

模块尺寸：18mm19.6mm3mm

模块颜色：黑色

![DMP-P11](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P11.png)

# 应用场景

智能插座

墙壁开关

排插

其他智能开关设备

# 模块型号

| 名称   | 天线类型    |
| ------ | ----------- |
| DMP-P1 | 板载PCB天线 |

# 典型应用

![DMP-P12](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P12.png)

# 文档更新说明

| 日期      | 版本 | 更新内容 |
| --------- | ---- | -------- |
| 2018-7-15 | V1.0 | 初次发布 |

# 一.产品基本参数

DMP-P1模块核心处理器采用工业级芯片ESP8285。该芯片在较小尺寸封装中集成了增强版的Tensilica’s L106钻石系列32-bit内核处理器。ESP8285拥有完整的Wi-Fi网络功能，可以脱离控制器独立使用，其内置的高速缓冲存储器大大提供了CPU性能。

DMP-P1模块支持标准的IEEE802.11 b/g/n/e/i协议以及完整的TCP/IP协议栈。

DMP-P1模块采用内置Flash，可以使得芯片工作于-40℃-125℃。

DMP-P1模块内置继电器控制算法，可以使得其外部IO控制继电器。

DMP-P1模块内置DoHome云服务，可以使用DoHome系列APP控制开关。

DMP-P1模块内置厂测程序，可以使得工厂快速生产测试。

![DMP-P13](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P13.png)

<center>图1.1模块结构图</center>

模块主要技术参数如下：

<center>表1.1模块主要参数</center>

![DMP-P11](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P14.png)

# 二. 接口定义

## DMP-P1接口定义如下图所示。

 ![DMP-P15](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P15.png)

<center>图2.1DMP-P1管脚定义</center>

## 模块的引脚定义如下表所示。

<center>表2.1模块管脚功能定义</center>

| 序号  | Pin脚名称 | 类型 | 功能说明                                                     |
| ----- | --------- | ---- | ------------------------------------------------------------ |
| 1     | IO16      | I/O  | GPIO16                                                       |
| 2,15  | GND       | P    | GND                                                          |
| 3,18  | IO0       | O    | GPIO0; SPI_CS2;                                              |
| 4,14  | VCC       | P    | 模块电源：3.3V/250mA                                         |
| 5     | P3        | I/O  | 第三路开关控制IO                                             |
| 6     | NET       | I/O  | 配网开关按钮                                                 |
| 7     | P4        | I/O  | 第四路开关控制IO                                             |
| 8     | LED       | I/O  | 状态指示IO，快闪：等待配网；慢闪：无网络；常亮：打开；长灭：关闭 |
| 9,17  | RX0       | I/O  | GPIO3; 可⽤作烧写 Flash 时 UART Rx                           |
| 10    | P1        | I/O  | 第一路开关控制IO                                             |
| 11,16 | TX0       | I/O  | GPIO1; 可⽤作烧写 Flash 时 UART Tx                           |
| 12    | P2        | I/O  | 第二路开关控制IO                                             |
| 13    | RST       | I/O  | 外部重置信号（低电平有效）, 复位模块; 模块内部已接上拉电阻   |

## 模块的外观及尺寸如下所示。

![DMP-P16](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P16.jpg)

<center>图2.2 DMP-P1模块外观</center>

![DMP-P17](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P17.png)

<center>图2.3DMP-P1尺寸图</center>

# 三.应用说明

基于DMP-P1的硬件最小系统图为：

![DMP-P18](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P18.png)

DMP-P1支持的软件包括DoHome 系列APP，IOS市场和各大Android市场均可搜索获得。

![DMP-P19](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P19.png)

<center>图3.1 DoHome APPs 二维码</center>

DMP-P1目前已经支持的智能音箱包括Amazon Alexa、Google Assistant、天猫精灵、京东叮咚、小爱同学、小度智能等。其使用说明参见APP中详细说明。

# 四. 电气特性

<center>表4.1电气特性</center>

![DMP-P20](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P20.png)

# 五. 功耗

<center>表5.1功耗</center>

|                 参数                  | 最小值 | 典型值 | 最大值 | 单位 |
| :-----------------------------------: | ------ | ------ | ------ | ---- |
|  Tx802.11b, CCK 11Mbps, POUT=+17dBm   | -      | 170    | -      | mA   |
| Tx802.11g, OFDM 54 Mbps, POUT =+15dBm | -      | 140    | -      | mA   |
|      Tx802.11n,MCS7,POUT =+13dBm      | -      | 120    | -      | mA   |
|  Rx 802.11b，1024 Bytes包⻓，-80dBm   | -      | 50     | -      | mA   |
|  Rx 802.11g，1024 Bytes包⻓，-70dBm   | -      | 56     | -      | mA   |
|  Rx 802.11n，1024 Bytes包⻓，-65dBm   | -      | 56     | -      | mA   |
|              Modem-sleep              | -      | 15     | -      | mA   |
|              Light-sleep              | -      | 0.9    | -      | mA   |
|              Deep-sleep               | -      | 20     | -      | μA   |
|                 关闭                  | -      | 0.5    | -      | μA   |

# 六. Wi-Fi射频特征

下表中数据是在室内温度下，电压为3.3V和1.1V时分别测得。

<center>表6.1Wi-Fi射频特征</center>

![DMP-P21](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8285/DOIT_DMP-P1/DMP-P21.png)

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

# 免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。 

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明。

注意：由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。

