<center><font size=10> W800 iOS_BleWiFi蓝牙配网 </center></font>
<center> From SZDOIT</center>



## 1 引言

### 1.1 概述

W800 作为集成 2.4 GHz Wi-Fi 和蓝牙双模的单芯片方案，支持 OneShotConfig 一键配网和蓝牙 BLE 配网两种模式，用户可以通过蓝牙 BLE 对使用了 W800 芯片的物联网设备进行安全配网。

联盛德提供蓝牙配网 IOS SDK 和示例 APP，供用户为设备进行配网。本文档将介绍 IOS版本示例 APP 的使用方法，供用户快速理解配网过程，为开发自己的 APP 提供指导。

## 2 蓝牙配网示例

### 2.1 硬件和软件环境

• W800 模组一个；

• PC 一台，安装串口工具，通过串口与 W800 模组相连；

• iPhone 手机一台，安装 WMBleWiFi APP;

### 2.2 APP 设置界面

1.打开 APP，显示下面界面，点击右上角 ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps1.png)；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps2.png)

2.进入设置界面，可以设置 BLE 扫描过滤 Organization ID，查看 APP 版本和 BleWiFi版本；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps3.png)

3.点 击 Organization ID 行 ， 弹 出 设 置 Organization ID 窗 口 ， 可 以 设 置Organization ID 继续扫描过滤，也可以清空它，不过滤扫描结果；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps4.png)

### 2.3 配置 Station 模式示例

1.PC 连接 W800 模组，串口工具发送 AT+ENADV 开启蓝牙配网过程；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps5.png)

2.手机打开 WMBleWiFi APP，在 APP 界面下拉刷新，可以发现周边的蓝牙设备，显示在界面列表中，每项分上下两行，上面是设备名称，下方是蓝牙 UUID，有的设备不广播名称，名称部分为空；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps6.png)

3.在扫描设备列表中，选择点击 W800 模组，进入到配置界面。点击![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps7.png) 按钮，弹出系统设置界面，连接需要配网的 AP，返回 WMBleWiFi 配置界面，输入密码，点击Config 按钮，开始配网过程；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps8.png)

4.配置界面下方是日志信息，显示配网进度。分别是连接设备、发现服务和特征、密钥交换和发配网信息，配网成功后，W800 模组加网成功后，返回 WiFi Mac 地址以及 IP 地址信息；

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/WiFi_Config/iOS/wps9.png)



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