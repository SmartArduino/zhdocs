 <center> <font size=10> HomeKit DoHome温湿度采集器 </font></center>

<center> from SZDOIT </center>

# 1. 产品外观



![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps2.jpg) 

 

##  

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps3.jpg) 

# 2. 参数规格

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps4.jpg)

# 3. 如何使用

## Step1：配置设备联网

设备上电,开启一个Homekit-sensor_xxxx的热点,连接“Homekit-sensor_xxxx”的热点，其密码为:无，大约等待3秒钟，手机将自动跳转到配网界面，注：若有多台设备，请注意区分不同的热点名字。

如果手机没有自动跳转到配网界面，请打开手机浏览器输入：http://192.168.4.1，等待进入配网界面。请在跳网面页中选择您的家庭WiFi名称，且请在password中输入密码，点击join。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps5.jpg) ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps6.jpg)

## Step2：加入到HomeKit家庭

1）请把手机连接到你的家庭WiFi网络

注意：苹果手机和设备必须是在同一个家庭WiFi网络下，即配置网络是选择的WiFi网络（例如设备配置的是连接PB9这个路由器，那么苹果手机也要连接到PB9这个路由）。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps7.jpg) 

 

2)打开苹果手机Home APP 点击添加配件，请将图6中的设置 代码（123-45-678）放到取景框 内。选择任然添加，等待加密校验 （50s)，添加成功。

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps8.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps9.jpg) 

 

 

 

 

注意：如果无法识别代码，请点击“没有 代码或无法扫描”，选择刷新出来 的设备，点击仍然添加，输入设置 代码:12345678，等待加密校验 （50s），添加设备成功。

如果没有刷新到设备，请确认手机和设备是否在同一个局域网络。请确认指示灯是否在常亮状态，如果添加失败，请查看常见问题。

请点击“没有代码或无法扫描”点击刷新出来的设备，仍然添加，等待加密校验（大约50S），添加设备成功。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps10.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps11.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps12.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps13.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps14.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps15.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps16.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/wps17.jpg) 

如果没有刷新到设备，请确认手机和设备是否在同一个局域网络。请确认指示灯是否在常亮状态，如果添加失败，请查看常见问题。

常见问题：

Q1:若我已经配置过了，想要重新配置该怎么办？

A1:若以前已经配置过路由，想要重新配置新的路由器，连续开关三次以上，每次上电时间超过2S，小于10s，然后重复第一次配网的步骤即可。

Q2: 我想自己二次开发，更新设备里面的固件应该如何操作。

二次开发见：https://github.com/SmartArduino/DoHome/tree/master/DoHome_HomeKit_Temperature_Humidity_Sensor

# 支持与服务

| 四博智联资源                                                 |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 官网                                                         | [www.doit.am](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/http://www.doit.am/) |
| 教材                                                         | [ESPDuino智慧物联开发宝典](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-7420449993.9.Bgp1Ll&id=520583000610) |
| 购买                                                         | [官方淘宝店](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/https://szdoit.taobao.com/)(szdoit.am) |
| 讨论                                                         | [技术论坛](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/http://bbs.doit.am/forum.php)(bbs.doit.am) |
| 应用案例集锦                                                 | [智能建筑云](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/http://building.doit.am)(building.doit.am) |
| [光伏监控云](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/http://solar.doit.am)(solar.doit.am) |                                                              |
| [Doit玩家云](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/http://wechat.doit.am)(wechat.doit.am) |                                                              |
| [免费TCP公网调试服务](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/HomeKitTemAndHum/http://tcp.doit.am)(tcp.doit.am) |                                                              |
| 官方技术支持QQ群1/2/3群已满                                  |                                                              |
| 技术支持群4                                                  | 278888904                                                    |
| 技术支持群5                                                  | 278888905                                                    |
| 技术支持群6                                                  | 278888906                                                    |
| 技术支持群7                                                  | 278888907                                                    |
| 技术支持群8                                                  | 278888908                                                    |
| 技术支持群9                                                  | 278888909                                                    |
| 技术支持群10                                                 | 278888900                                                    |



# 免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。 

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明 

# 注 意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。

 