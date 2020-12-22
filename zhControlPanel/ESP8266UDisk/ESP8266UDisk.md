<center><font size=10> ESP8266 U盘开发板的基本使用手册 </center></font>
<center> From SZDOIT</center>

## 1. 简介

​	ESP8266 U盘开发板是深圳四博智联科技有限公司开发的一款USB接口的esp8266设备，可用来制作随身便携设备，可二次开发，常见应用有探针，客流统计，热点广告机，断网神器等。

![wps12](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps12.png)

## 2.安装驱动

​	ESP8266 U盘开发板使用的USB转TTL芯片为CP2102，首次使用时需要安装CP2102驱动。

安装步骤

打开附件中的CP2102驱动

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps1.jpg) 

选择对应的系统版本

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps2.jpg) 

一路NEXT安装下去

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps3.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps4.jpg) 

提示完成即可，打开window设备管理器可查看到设备驱动安装完成，已显示COM口

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps5.jpg) 

## 3 下载固件

​	ESP8266 U盘开发板可以使用ESPTOOL工具下载固件。推荐使用ESPFlashDownloadTool下载软件。

​	打开ESPFlashDownloadTool，选择ESP8266DownloadTool。

​	![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps6.jpg)

打开软件后选择固件，默认提供的固件是led闪烁，下载地址如下

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps7.jpg) 

下载地址以实际固件的下载地址为准。

其他配置如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps8.jpg) 

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

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps9.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps10.jpg) 

## 5 模块尺寸（mm）

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/ESP8266UDisk/wps11.jpg) 

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