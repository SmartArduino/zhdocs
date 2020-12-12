<center><font size=10> 月球灯使用说明 </center></font>
<center> From SZDOIT</center>

## 1.简介

​	月球灯不仅支持苹果手机Siri 1600万真彩色调光，而且还支持安卓手机DoHome控制。

![wps1](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps1.png)

## 2.硬件说明

(1) 参数说明：

![wps2](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps2.png)

(2) IO口说明

|   功能    |  GPIO  |
| :-------: | :----: |
| 红色（r） | GPIO12 |
| 绿色（g） | GPIO14 |
| 蓝色（b） | GPIO5  |
| 白色（w） | GPIO4  |

## 3. 客户如何更新自己的程序

本产品自带串口下载芯片，支持用户下载自己的程序，详细见：https://github.com/SmartArduino/DoHome/tree/master/DoHome_HomeKit_Moon_Light

## 4. 如何使用

### 4.1 苹果手机

第一步：请打开苹果手机WiFi列表（如图1），找到Homekit_xxxx 的WIFI 热点并连接。大约等待3秒钟，手机将自动跳转到配网界面。

注意：如果手机没有自动跳转到配网界面，请打开手机浏览器输入：htt://192.168.4.1。等待进入配网界面。

![wps3](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps3.png)

第二步：请在跳网面页中选择您的家庭WiFi名称，且请在password中输入密码，点击join （如图2）。等待手机配网页跳转到WIFI列表页面（如图3）。（图中WIF 账号仅供参考）

![wps4](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps4.png)

![wps5](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps5.png)

第三步：检查您是否安装Home APP,系统默认安装，除非人为卸载。

如果没有Home  APP请在App Store商城下载一个Home  APP（如图4）。

![wps6](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps6.png)

图4  安装Home

第四步：请再次核对手机连接到你的家庭WiFi网络（如图5）

注意：苹果手机和智能插座必须是在同一个家庭WiFi网络下。

![wps7](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps7.png)

第五步：打开苹果手机Home APP 点击添加配件，请点击“没有代码或无法扫描”点击刷新出来的设备，仍然添加，等待加密校验（大约50S），添加设备成功。为以后方便的操做请重新命名

![wps8](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps8.png)![wps9](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps9.png)

![wps10](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps10.png)

![wps11](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps11.png)![wps12](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps12.png)

注意：如果没有刷新设备，请确认手机和智能插座是否在同一个局域网络。请确认指示灯是否在常亮状态，如果添加失败，请查看常见问题。

第六步：如果您要用alexa 、谷歌助手、天猫精灵、小爱同学、等智能音响设备或是需要定时等更多功能请见常见问题1。

### 4.2 安卓手机

第一步：请给智能月球灯上电，

1)给智能灯供电。

2)给智能灯断电。

3)如此重复操作三次，LED灯白光闪烁三次，然后常亮，LED灯发出DoHome_XXXXXX热点。

第二步：打开手机扫描下面二维码并且下载DoHome  APP。

![wps13](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps13.png)

第三步：打开DoHome APP 注册DoHome APP账号，并登录DoHome APP。

![wps14](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps14.png)

第四步：点击右上角“+”添加设备，按照提示操作即可。

注意：如有疑问，请点击左上角菜单栏，查看帮助并点击使用说明。

![wps15](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps15.png)

![wps16](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps16.png)

![wps17](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps17.png)

## 5. 常见问题

Q1:Homekit用户如何使用alexa 、谷歌助手、天猫精灵、小爱同学等智能音响设备？如何通过DoHome使用定时等更多功能

A1:扫描下面二维码。下载DoHome  APP，注册、登录，然后点击左上角帮助，查看相应的音箱操作。

![wps18](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartProduct/MoonLight/wps18.png)

Q2：在添加设备的时候，如果弹窗提示“是否允许APP获取您的定位”，如何处理？

A2：这个问题非常重要，请一定点击“同意”或“允许”。

Q3：为什么设备名称需要简短？

A3：因为这对语音控制功能来说比较方便，例如DoHome。

Q4:如何把智能月球灯恢复出厂设置

1)给智能灯供电。

2)给智能灯断电。

3)如此重复操作3次，LED灯循环慢闪，颜色没有从红、绿、蓝、白，然后常亮。

Q5:配网过程中要注意哪些事项

1.配网过程中请确保设备，手机，路由器三者靠近；

2.配网过程中请确保输入的路由器的密码正确；

3.配网过程中请确保路由器工作在2.4G频段，并且使能广播功能，并且工作在 非11n only 模式；

4.配网过程中请确保路由器无线设置加密方式为WPA2-PSK类型，认证类型为AES，或者两者皆设置为自动。

5.配网过程中若路由器开启无线MAC地址过滤，请将设备移除路由器的MAC过滤列表；请确认路由器是否有防火墙功能。若有，请关闭防火墙功能后，再尝试让设备连接路由器；

6.如果是双频路由器，请将2.4G信号和5G信号分别设置不同的密码，或者关闭5G信号，请勿打开双频合一的功能；

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