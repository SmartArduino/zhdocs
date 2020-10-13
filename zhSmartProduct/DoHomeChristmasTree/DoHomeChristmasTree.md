 <center> <font size=10> DoHome圣诞灯的使用说明 </font></center>

<center> from SZDOIT </center>

#  一、产品概论

该产品软硬件都是由本公司自主研发的，支持语音、硬件、软件等多种控制模式，有56种固定灯效和麦克风悦动灯效，外观绚丽多彩，而且使用NodeMcu做为产品的控制模块，非常适合电子爱好者入门学习，简单适用。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps2.jpg)

# 二、烧写程序

程序的烧写是通过官方的下载工具flash_download_tool_v3.8.5进行下载，工具下载链接：https://pan.baidu.com/s/1V5Xszf7SBMLd8UQjwpF-dw 提取码：doit，下载好之后解压出来即可适用，如果不清楚怎么下载的朋友可根据一下内容进行烧写：

①　双击打开flash_download_tool_v3.8.5.exe

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps3.jpg) 

②　选择Developer Mode

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps4.jpg) 

③　在弹出窗口中选择对应的模块，NodeMCU选择ESP8266 DownloadTool

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps5.jpg) 

④　设置设置好参数以及端口号，点击STAR接口下载

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps6.jpg) 

 

# 三、控制

## 3.1 硬件配置使用说明

硬件控制是通过按NodeMCU上面的Flash按键来进行控制，包含有56种灯光切换模式，具体的操作方法如下：

(1)当短按按键一次将切换固定灯效，若在上一次按下按键5秒再次按下按键则继续切换模式，如5秒后点击按键这是将圣诞灯关闭。

(2)如长按按键则进入麦克风悦动灯效模式，进入麦克风模式则无法使用短按切换固定灯效，如要退出麦克风模式，请再次长按按键。

## 3.2 软件控制使用说明

软件控制是通过DoHome APP来控制的，它是有本司研发的，支持Apple、Android系统，可以通过手机扫描二维码，或在App Store、应用市场搜索“DoHome”下载安装。并注册登录“DoHome ”APP。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps7.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps8.jpg) 

 

### 3.2.1 添加设备

1、确保手机连接上家庭WiFi（仅支持2.4G WiFi网络），点击主页右上角“+”图标。

2、选择点击的产品图标。

3、输入路由器密码。

4、请给圣诞灯供电(5V)，请确认圣诞灯在出厂模式（红-绿-蓝-白-闪烁）。

5、打开手机WiFi设置。连接“DoHome_XXXX”WiFi热点。

6、返回“DoHome APP”，等待配网完成。

提示：如何把圣诞灯恢复出厂模式

给圣诞灯断电-上电三次，并且查看圣诞灯的闪烁状态（红-绿-蓝-白-闪烁），此状态为出厂模式

### 3.2.2 将设备配置到Apple

1.开启HomeKit模式

(1)确保已将设备绑定到DoHome APP

(2)进入属性界面，点击开启HomeKit模式。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps9.png) 

2.绑定到Apple

(1)打开苹果手机Home APP， 点击添加配件。

(2)请将图6中的设置 代码（123-45-678）放到取景框内，选择仍然添加。

(3)等待加密校验 (50s)，添加成功。

  ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps10.png)   ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps11.png)  ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps12.jpg)

注意：如果无法识别代码，点击“没有代码或无法扫描”，选择设备，点击仍然添加，输入设置代码：12345678，等待加密校验（50s），添加设备成功。如果苹果手机没有显示设备，请确认手机和设备是否在同一个WiFi网络下。如果添加失败，请查看后面常见问题，如有疑问请联系技术支持。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps13.png)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps14.png)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps15.png)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps16.png)    ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps17.png)   ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps18.png)

 

## 3.3 语音控制使用说明

请点击左上角菜单栏.请在菜单栏中选择对应音箱图标，并查看用户手册。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps19.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/wps20.jpg) 

注意：使用音箱之前，请在Alexa 、谷歌助手、天猫精灵、小爱同学等智能音箱设备平台登录你的平台账号。

# 四、程序更新和问题解答

可到本司GitHub网站下载程序自行更新：https://github.com/SmartArduino/DoHome/tree/master/DoHome_HomeKit_Christmas_Light

售后技术论坛：

https://github.com/SmartArduino/DoHome/tree/master/DoHome_HomeKit_Moon_Light

常见问题：https://support.doiting.com/

# 五、支持与服务

 

| 四博智联资源                                                 |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 官网                                                         | [www.doit.am](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/http://www.doit.am/) |
| 教材                                                         | [ESPDuino智慧物联开发宝典](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-7420449993.9.Bgp1Ll&id=520583000610) |
| 购买                                                         | [官方淘宝店](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/https://szdoit.taobao.com/)(szdoit.am) |
| 讨论                                                         | [技术论坛](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/http://bbs.doit.am/forum.php)(bbs.doit.am) |
| 应用案例集锦                                                 | [智能建筑云](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/http://building.doit.am)(building.doit.am) |
| [光伏监控云](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/http://solar.doit.am)(solar.doit.am) |                                                              |
| [Doit玩家云](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/http://wechat.doit.am)(wechat.doit.am) |                                                              |
| [免费TCP公网调试服务](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/DoHomeChristmasTree/http://tcp.doit.am)(tcp.doit.am) |                                                              |
| 官方技术支持QQ群1/2/3群已满                                  |                                                              |
| 技术支持群4                                                  | 278888904                                                    |
| 技术支持群5                                                  | 278888905                                                    |
| 技术支持群6                                                  | 278888906                                                    |
| 技术支持群7                                                  | 278888907                                                    |
| 技术支持群8                                                  | 278888908                                                    |
| 技术支持群9                                                  | 278888909                                                    |
| 技术支持群10                                                 | 278888900                                                    |

 

 

# 六、免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。 

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明

# 七、注 意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示