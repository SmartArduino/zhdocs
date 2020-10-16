 <center> <font size=10> W5G1模块数据手册</font></center>

<center> from SZDOIT </center> 

# 一. 产品概述

DT-W5G1模块核心处理器采用超低功耗处理器、2G&5G双频芯片。该芯片在较小尺寸封装中集成了业界领先的32位微型MCU，带有16位精简模式，主频⽀持160 MHz。DT-W5G1拥有完整的Wi-Fi网络功能，既能够独⽴应⽤，也可以作为从机搭载于其他主机MCU运⾏。当DT-W5G1独⽴应⽤时，能够直接从外接Flash中启动。内置的⾼速缓冲存储器有利于提高系统性能，并且优化存储系统。此外DT-W5G1只需通过SPI/SDIO 接⼝或I2C/UART⼝即可作为Wi-Fi适配器，应⽤到基于任何微控制器的设计中。



![DT-W5G13](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G13.png)

DT-W5G1模块支持标准的IEEE802.11 a/b/g/n协议以及完整的TCP/IP协议栈。用户可以使用该模块为现有设备添加联网功能，也可以构建独立的网络控制器。

DT-W5G1模块供最大实用性，为Wi-Fi功能嵌入其他系统提供无限可能。

DT-W5G1模块具有大带宽远距离通信特性，可以用于无线图传。

![DT-W5G11](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G11.png)

<center>图1. 1 模块结构图</center>

模块主要技术参数如下：

<center>表1. 1模块主要参数</center>

![DT-W5G110](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G110.png)

# 二. 接口定义

DT-W5G1接口定义如下图所示。

![DT-W5G12](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G12.png)

<center>图2. 1模块管脚图</center>

模块的工作模式选择和每个管脚定义如下表所示。

<center>表2. 2 模块管脚功能定义</center>

| 序 号 | Pin脚名称 | 类型 | 功能说明                                      |
| :---: | :-------: | :--: | --------------------------------------------- |
|   1   |    GND    |  P   | GND                                           |
|   2   |    GND    |  P   | GND                                           |
|   3   |    D14    |  P   | DIO14，红外接收功能，PWM1                     |
|   4   |    D15    | I/O  | DIO15，RX1                                    |
|   5   |    D10    | I/O  | DIO10                                         |
|   6   |    D11    | I/O  | DIO11                                         |
|   7   |    D12    | I/O  | DIO12，TX1                                    |
|   8   |    D13    | I/O  | DIO13，IIC时钟，红外输出引脚，TX2             |
|   9   |   CLK_S   | I/O  | DIO18，睡眠时钟引脚                           |
|  10   |    D23    | I/O  | DIO1; 可⽤作烧写Flash时UART Tx                |
|  11   |    D24    | I/O  | DIO24,红外输入引脚                            |
|  12   |    EN     |  I   | 芯片使能引脚，内置上拉电阻，低电平有效        |
|  13   |    VCC    |  P   | 电源，3.3V                                    |
|  14   |    VCC    |  P   | 电源，3.3V                                    |
|  15   |    RX0    | I/O  | DIO8，下载串口RX                              |
|  16   |    TX0    | I/O  | DIO9，下载串口TX                              |
|  17   |    D0     | I/O  | DIO0，I2S，RX1                                |
|  18   |    D1     | I/O  | DIO1，TX1                                     |
|  19   |    D2     | I/O  | DIO2，RX2                                     |
|  20   |    D3     | I/O  | DIO3，TX2                                     |
|  21   |    D25    | I/O  | DIO25，上拉：外部中断使能；下拉：内部中断使能 |
|  22   |    RST    |  I   | 复位功能，低电平有效                          |
|  23   |    GND    |  P   | GND                                           |
|  24   |    D22    | I/O  | DIO22，上拉：Flash启动；下拉：ROM启动         |
|  25   |    AD2    | I/O  | DIO16，AD2，模拟IO                            |
|  26   |    AD1    | I/O  | AD1，模拟IO                                   |
|  27   |    AD0    | I/O  | AD0，模拟IO                                   |
|  28   |    D20    | I/O  | DIO20                                         |
|  29   |    D19    | I/O  | DIO19                                         |
|  30   |    D5     | I/O  | DIO5，RX1                                     |
|  31   |    D4     | I/O  | DIO4，TX1                                     |
|  32   |    D21    | I/O  | DIO21，PWM2，I2S，唤醒功能                    |
|  33   |    GND    |  P   | GND                                           |
|  34   |    GND    |  P   | GND                                           |

# 三. 外型与尺寸

模组的外观尺寸为 17.5mm x 34.5mm x 3mm（如图所示）。该模组默认采用的Flash容量为16Mbits（2M Bytes）。

![DT-W5G13](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G13.png)

<center>图3. 1 模组外观</center>

![DT-W5G14](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G14.png)

<center>(a) 俯视图</center>

![DT-W5G15](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G15.png)

<center>(b) 侧视图</center>

<center>图3. 2模组尺寸图</center>

<center>表3. 1模组尺寸对照表</center>

| 长     | 宽     | 高   | PAD  尺寸（底部） | Pin  脚间距 |
| ------ | ------ | ---- | ----------------- | ----------- |
| 34.5mm | 17.5mm | 3 mm | 0.9mm x 1.7 mm    | 1.5mm       |

# 四. 电气特性

<center>表4. 1电气特性</center>

![DT-W5G111](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G111.png)

# 五. 功耗

<center>表5. 1功耗</center>

|          参数          | 最小值 | 典型值 | 最大值 | 单位 |
| :--------------------: | :----: | :----: | :----: | :--: |
| 2.4 GHz, Rx 11n Active |        |        |        |      |
|  5 GHz, Rx 11n Active  |   -    |  190   |   -    |  mW  |
|  2.4 GHz, Tx 11b, CCK  |   -    |  220   |   -    |  mW  |
| 2.4 GHz, Tx 11n, MCS7  |   -    |  908   |   -    |  mW  |
|  5 GHz, Tx 11n, MCS7   |   -    |  750   |   -    |  mW  |
|         Sleep          |   -    |  220   |   -    |  μA  |

# 六. Wi-Fi射频特征

下表中数据是在室内温度(25℃)下，电压为3.3V时测得。

<center>表6. 1 Wi-Fi射频特征（2G）</center>

![DT-W5G112](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G112.png)

<center>表6. 2 Wi-Fi射频特征（5G）</center>

![DT-W5G113](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G113.png)

# 七. 推荐炉温曲线

推荐炉温曲线如下：

![DT-W5G16](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G16.png)

<center>图7. 1 推荐炉温曲线</center>

# 八. 模块最小系统

模块最小系统电路图如下：

![DT-W5G17](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G17.png)

<center>图8. 1最小系统</center>

注：

（1）模块供电电压为直流3.3V；

（2）Wi-Fi模块IO最大输出电流为12mA；

（3）Wi-Fi模块NRST管脚低电平有效；EN使能管脚高电平有效；

（4）Wi-Fi模块的RXD接外部MCU的TXD，Wi-Fi模块的TXD接外部MCU的RXD。

# 九. 推荐PCB设计

Wi-Fi模块可以直接焊接到PCB板上。为了使您的终端产品获得最佳的射频性能，请注意根据本指南合理设计模块及天线在底板上的摆放位置。

![DT-W5G18](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G18.png)

<center>推荐放置方式</center>

![DT-W5G19](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/DOIT_DT-W5G1/DT-W5G19.png)

<center>次优放置方式（天线下面不可铺铜、不可有金属物体）</center>

# 十. 外围走线建议

Wi-Fi模块集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和EMI特性要求较高，建议在数字I/O线上串联10~100欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳，同时这种做法也能在一定程度上防止静电释放（ESD）。

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

注 意：由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。