<center><font size=10> WM_W800_SDK_DEMO使用指导 </center></font>
<center> From SZDOIT</center>

## 1 引言

### 1.1 编写目的

为基于 W80X 芯片 SDK 进行二次开发的软件开发工程师提供相关功能的代码示例。

### 1.2 预期读者

FAE，客户方软件开发工程师。

## 2 DEMO 概要

该文档中用到的所有 DEMO 相关的宏定义都在 wm_demo.h 中。运行 DEMO 时必须打开该 DEMO 对应的宏定义，建议关闭不相关宏定义。DEMO 演示需要在控制台下进行，打开 DEMO_CONSOLE 编译选项，即打开了控制台。

DEMO_CONSOLE 同时还控制了 AT 指令的启用，如果使能此宏，则 AT 指令失效；关闭此宏，AT 指令生效。

以下三节将分别以配网联网类示例，硬件驱动类示例以及应用类示例来分别介绍其测试使用方法。

## 3 配网联网类 DEMO 功能描述

### 3.1 DEMO_CONNECT_NET 操作步骤

注：此 DEMO 下有四个演示 DEMO。

#### 3.1.1 t-connect 加网

![image1](image1.png)

#### 3.1.2 t-oneshot(oneshot 配网)

![image-20201117135838360](image-20201117135838360.png)

#### 3.1.3 t-oneshot（airkiss 配网）

![image-20201117135911180](image-20201117135911180.png)

#### 3.1.4 t-webcfg(网页配网)

![image2](image2.png)

### 3.2 DEMO_APSTA 操作步骤

![image3](image3.png)

### 3.3 DEMO_SOFT_AP 操作步骤

![image4](image4.png)

### 3.4 DEMO_WPS 操作步骤

注：此 DEMO 下有两个演示 DEMO，需要路由器支持 wps

![image-20201117140613333](image-20201117140613333.png)

#### 3.4.1 t-wps-start-pbc

1. 打开宏定义 DEMO_WPS；
2. 编译，升级成功后，在 uart0 打印的控制台信息中能看到对应命令；
3. 通过 uart0 发送 t-wps-start-pbc，并在路由器上按 wps 按钮，稍候 uart0 打印
[CMD]t-wps-start-pbcStart WPS pbc mode ...
WiFi JOIN SUCCESS
NET UP OK,Local IP:192.168.1.101

![image5](image5.png)

#### 3.4.2 t-wps-start-pin

![image-20201117140825317](image-20201117140825317.png)

### 3.5 DEMO_SCAN 操作步骤

![image6](image6.png)

## 4 硬件驱动类 DEMO 功能描述

### 4.1 DEMO_UARTx 操作步骤

![image7](image7.png)

### 4.2 DEMO_GPIO 操作步骤

注：此 DEMO 下有两个演示 DEMO

#### 4.2.1 t-gpio

![image-20201117141234720](image-20201117141234720.png)

#### 4.2.2 t-gpioirq

![image-20201117141300221](image-20201117141300221.png)

### 4.3 DEMO_FLASH 操作步骤

![image-20201117141321349](image-20201117141321349.png)

### 4.4 DEMO_ENCRYPT 操作步骤

![image8](image8.png)

### 4.5 DEMO_RSA 操作步骤

![image9](image9.png)

### 4.6 DEMO_RTC 操作步骤

![image10](image10.png)

### 4.7 DEMO_TIMER 操作步骤

![image-20201117141922646](image-20201117141922646.png)

### 4.8 DEMO_PWM 操作步骤

![image11](image11.png)

### 4.9 DEMO_PMU 操作步骤

注：此 DEMO 下有两个演示示例。

#### 4.9.1 t-pmuT0

![image12](image12.png)

#### 4.9.2 t-pmuT1

![image-20201117142319143](image-20201117142319143.png)

### 4.10 DEMO_I2C 操作步骤

注：此 DEMO 需要 AT24CXX 芯片

![image-20201117142404741](image-20201117142404741.png)

![image13](image13.png)

### 4.11 DEMO_I2S 操作步骤

注：

![image14](image14.png)

### 4.12 DEMO_MASTER_SPI 操作步骤

![image15](image15.png)

## 5 应用类 DEMO 功能描述

### 5.1 DEMO_STD_SOCKET_CLIENT 操作步骤

注：通过 uart0 发送 demohelp 模块 uart0 会返回控制台信息。

![image16](image16.png)

### 5.2 DEMO_STD_SOCKET_SERVER 操作步骤

![image17](image17.png)

### 5.3 DEMO_SOCKET_CLIENT_SERVER 操作步骤

本测试宏开关下共有两个示例，分别是设备作为 tcp client 与设备作为 tcp server；以下是作为 client 时的测试步骤。

![image18](image18.png)

以下是设备作为 server 时的测试步骤。

![image19](image19.png)

### 5.4 DEMO_UDP 操作步骤

注：此 DEMO 下有四个演示 DEMO，需要使用抓包网卡

#### 5.4.1 UDP 广播

![image20](image20.png)

#### 5.4.2 UDP 单播

![image-20201117163331752](image-20201117163331752.png)

#### 5.4.3 UDP 组播

![image21](image21.png)

### 5.5 DEMO_NTP 操作步骤

注：此 DEMO 下有三个演示 DEMO

#### 5.5.1 t-ntp

![image22](image22.png)

#### 5.5.2 t-setntps

![image23](image23.png)

#### 5.5.3 t-queryntps

![image-20201117163836589](image-20201117163836589.png)

### 5.6 DEMO_HTTP 操作步骤

注：此 DEMO 下有四个演示 DEMO，需要下载 tomcat 服务器（需要放置所需脚本文件 ） 和 hfs 服 务 器 。 相 关 配 件 的 下 载 地 址 在 官 网http://www.winnermicro.com/html/1/156/158/497.html 的软件资料标签页下的”配套wmsdk demo 使用的工具代码:”处。

![image-20201117163907348](image-20201117163907348.png)

下图分别为 tomcat 服务器启动后的页面以及 http 服务器添加固件就绪后的页面：

![image-20201117163925455](image-20201117163925455.png)

![image-20201117163932934](image-20201117163932934.png)

其中 hfs 服务器及 tomcat 服务器可以从网上下载，hfs 下载后直接可用，tomcat(已测试过7.0.34 及 8.5.23 版本)服务器下载下来后需要在里面修改添加一些脚本文件。具体为将tomcat 根目录下的 webapps 文件夹下TestWeb 文件夹替换为官方提供的 TestWeb 文件夹(已在里面添加了测试 httpget httpput httppost 所需要的相应脚本文件)。

#### 5.6.1 t-httpget

![image24](image24.png)

#### 5.6.2 t-httpput

![image25](image25.png)

#### 5.6.3 t-httppost

![image26](image26.png)

#### 5.6.4 t-httpfwup

![image-20201117164722036](image-20201117164722036.png)

### 5.7 DEMO_SSL_SERVER 操作步骤

![image27](image27.png)

下图为使用 openssl(需要用户自己安装)工具连接 ssl server 成功后的命令行页面信息。

![image-20201117164928805](image-20201117164928805.png)

### 5.8 DEMO_WEBSOCKETS 操作步骤

注：此 DEMO 下有两个演示 DEMO，需要下载 WEBSOCKET_SERVER 测试服务器

#### 5.8.1 websocket 不加密方式的数据通信

![image28](image28.png)

#### 5.8.2 websocket 加密方式的数据通信

![image29](image29.png)

### 5.9 DEMO_HTTPS 操作步骤

![image-20201117165616926](image-20201117165616926.png)

### 5.10 DEMO_MQTT 操作步骤

![image30](image30.png)

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