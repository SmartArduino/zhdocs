<center><font size=10> ESP8266 U盘开发板的基本使用手册 </center></font>
<center> From SZDOIT</center>

## 1. 简介

​	ESP8266 U盘开发板是深圳四博智联科技有限公司开发的一款USB接口的esp8266设备，可用来制作随身便携设备，可二次开发，常见应用有探针，客流统计，热点广告机，断网神器等。

![wps12](wps12.png)

## 2.安装驱动

​	ESP8266 U盘开发板使用的USB转TTL芯片为CP2102，首次使用时需要安装CP2102驱动。

安装步骤

打开附件中的CP2102驱动

![img](wps1.jpg) 

选择对应的系统版本

![img](wps2.jpg) 

一路NEXT安装下去

![img](wps3.jpg) 

![img](wps4.jpg) 

提示完成即可，打开window设备管理器可查看到设备驱动安装完成，已显示COM口

![img](wps5.jpg) 

## 3 下载固件

​	ESP8266 U盘开发板可以使用ESPTOOL工具下载固件。推荐使用ESPFlashDownloadTool下载软件。

​	打开ESPFlashDownloadTool，选择ESP8266DownloadTool。

​	![img](wps6.jpg)

打开软件后选择固件，默认提供的固件是led闪烁，下载地址如下

![img](wps7.jpg) 

下载地址以实际固件的下载地址为准。

其他配置如下：

![img](wps8.jpg) 

选择对应的COM口，点击START下载即可

重新拔插设备即可观察到正反两面的led在闪烁。

### FQA：

下载失败：

1. 选择了过高的波特率，可尝试降低波特率。

2. 没有选择实际的COM口，设备管理器查看com

3. 驱动未安装完成，安装cp2102驱动

固件未能正常工作：

1. 错误的设置下载参数，下载参数需要选择上文中的参数。

2. 下载地址错误，注意下载地址。各个开发环境开发的固件下载地址有所区别。

## 4 硬件参数

| CPU          | ESP8266                           |
| ------------ | --------------------------------- |
| FLASH大小    | 4MByte                            |
| 无线协议     | 802.11 b/g/n                      |
| 工作频率     | 2412-2484MHz                      |
| 输出功率     | 802.11b模式下+19.5dBm的输出功率   |
| 待机功耗     | 待机状态消耗功率⼩于1.0mW (DTIM3) |
| 工作电压     | DC 5V                             |
| 工作温度     |                                   |
| USB转TTL芯片 | CP2102                            |
| 外观规格：   |                                   |
| 尺寸         | 44.2 x 22.0 x 6.8 mm              |
| 重量         | 5g                                |
| 指示灯引脚   |                                   |
| GPIO2        | 模块led，蓝色，低电平有效         |
| GPIO14       | 板载led，红色，高电平有效         |

![img](wps9.jpg)![img](wps10.jpg) 

## 5 模块尺寸（mm）

![img](wps11.jpg) 

## 更多资源，请关注公众号！

![wps101010](wps101010.png)
