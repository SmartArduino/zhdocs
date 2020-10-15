<center> <font size=10> Arduino IDE搭建esp32开发环境 </font></center>

<center> from SZDOIT </center>

# 开发环境搭建

## 使用windows环境开发，安装步骤：

### 1． 安装Arduino IDE ，可以从[arduino.cc](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/https://www.arduino.cc/en/Main/Software) 下载Arduino IDE客户端。

### 2． 安装Git GUI，可以从[git-scm.com](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/https://git-scm.com/download/win) 下载Git GUI客户端。

### 3． 打开Git GUI 选择Clone Existing Repository

在Source Location选项键入https://github.com/espressif/arduino-esp32.git

在Target Directory选项点击Browse选择Arduino IDE目录下的/hardware文件夹

然后在文件路径后面添加/espressif/esp32。其实就是创建一个文件夹，但是不能自己先创建，需要用软件里填写创建。

以我现在的路径为例，Target Directory选项完整路径为F:/bao/arduino-1.8.2/hardware/espressif/esp32

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps1.jpg) 

### 4． 点击Clone，等待安装完成

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps2.jpg) 

### 5． 安装完成

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps3.jpg) 

### 6点击.打开刚才定义的目录下的tools文件夹，点击get.exe，开始下载库文件

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps4.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps5.jpg) 

### 7. 下载完成后打开Arduino IDE可以看到板卡中已经可以选择ESP 32开发板

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps6.jpg) 

### 8. 板卡选择ESP32 Dev Modeule，打开示例的WiFi Scan 点击上传

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps7.jpg) 

显示下载完成

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps8.jpg) 

打开串口助手即可看到扫描到的wifi信息了

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP32/ArduinoEnvironment/wps9.jpg)

更多详情请参见https://github.com/espressif/arduino-esp32

# 支持与服务

| 官方技术支持QQ群 |           |
| :--------------- | --------- |
| 技术支持群4      | 278888904 |
| 技术支持群5      | 278888905 |
| 技术支持群6      | 278888906 |
| 技术支持群7      | 278888907 |
| 技术支持群8      | 278888908 |
| 技术支持群9      | 278888909 |
| 技术支持群10     | 278888900 |

# 免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。 

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明 

# 注 意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。



