<center><font size=10> W800_参数区使用说明 </center></font>
<center> From SZDOIT</center>

## 1 引言

### 1.1 编写目的

本文档主要用于阐述 W800 中的 QFLASH 布局，关键参数区和系统参数区使用以及用户参数区处理。

### 1.2 预期读者

该文档适用的读者包括研发人员、测试人员、架构师等。

### 1.3 术语定义

![image-20201114095103047](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114095103047.png)

## 2 QFLASH 参数区布局

![image-20201114095145220](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114095145220.png)

本文档以 X=1 为例，即 Flash 容量为 2MByte。

### 2.1 物理层参数区

地址空间：0x8000000-0x8000FFF，共 4KByte
参数内容：
MAC 地址和 RF 参数。
参数布局：

![image-20201114095233873](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114095233873.png)

### 2.2 用户参数区

地址空间：0x81C0000-0x81FBFFF，共 240KByte
参数内容：
用于用户存放自定义参数时使用。
参数布局：
用户自定义

### 2.3 系统参数区域

地址空间：0x81FC000-0x81FEFFF，共 12KByte
参数内容：
系统运行时所需的相关参数
参数布局：

![image-20201114095321327](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114095321327.png)

1）系统参数 1 区：0x81FC000-0x81FCFFF

2）系统参数 2 区：0x81FD000-0x81FDFFF

3）系统参数 3 区：0x81FE000-0x81FEFFF

## 3 物理层参数区

### 3.1 物理层参数介绍

W800 模块工作所需要的 MAC 地址，以及 Wi-Fi 收发机工作所需要的 RF 校准参数

### 3.2 物理层参数写入阶段

W800 芯片或者模块生产时写入

### 3.3 物理层参数的使用

W800 模块启动时会从关键参数区把所需参数读取出来使用。
物理层参数具有备份机制。

## 4 系统参数区

### 4.1 系统参数介绍

系统参数是指 W800 模块运行时所需要的联网，接口配置，模式配置等的参数，具体如下：
1）Wi-Fi 相关（SSID，BSSID，KEY，信道列表，节电标志，速率设置，区域码，工作模式）

2）IP 信息（静态 IP，DHCP 使能信息，NTP 服务器，DNS 服务器）

3）接口配置（UART 配置）

4）BT 参数

5）其他参数（WEB）

### 4.2 系统参数的使用

#### 4.2.1 初始化阶段

系统参数区具有备份机制，通过 CRC 和 MODIFY_CNT 校验值确定使用哪个参数区的内容作为系统运行时使用的参数，具体机制为：

1）参数区 CRC 均正确的情况下，依据 MODIFY_CNT 选取使用的当前参数

2）参数区 CRC 只有一个正确的情况下，选择 CRC 正确的参数区作为当前参数，另外一个参数区更新为当前参数区的值

3）参数区 CRC 都不正确的情况下，首先尝试参数恢复，如果尝试恢复后，参数依然都不正确，则使用默认参数值作为运行时使用参数，同时，更新参数区的内容为默认参数。

![image1](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image1.png)

#### 4.2.2 参数使用阶段

1）参数获取
系统参数区除了存放于 QFLASH 的两个区域外，还会在初始化的时候在内存中备份
一份，以便于运行时的使用，防止频繁访问 QFLASH。
2）参数写入
（1）系统启动时，第一次初始化或者参数区有破坏，会写参数区
（2）运行中，系统参数更新，会写参数区

## 5 用户参数区

### 5.1 用户参数

W800 使用者期望存储自定义的参数或者运行日志。

### 5.2 用户区使用

#### 5.2.1 用户参数区的操作

W800 的 SDK 会增加针对用户参数区的操作机制，保证用户针对参数区的操作仅使用相对地址（相对 USER_ADDR_START）即可实现。

#### 5.2.2 用户参数区的调整规则

W800 的默认 QFLASH 的布局所能提供给用户的区域为 240KByte。但是，当前的 W800用户参数区设置是依据尽可能大的代码区来设计的。

##### 5.2.2.1 用户参数区的调整规则：

1) 依据用户编译的 w800.img 确定的所用运行区空间

![image-20201114100031469](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114100031469.png)

2) 依据 w800.img 的压缩比来确定所用的升级区空间

![image-20201114100050917](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114100050917.png)

3) 依据 w800.img 的大小按照 QFLASH 的 BLOCK（64Kbyte）区间向上取整划分（需要重点关注）。

4) 依据 IMAGE 的划分结果重新确定用户空间的起始地址。

5) 根据新划分的空间调整 W800 SDK 的宏定义确定新的用户空间起始地址



![image-20201114100120590](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114100120590.png)

6) 依据确定的运行区 IMAGE HEADER 的起始位置调整 IMAGE 生成的参数(下划线部分)

wm_tool.exe -b w800.bin -o w800 -it $img_type -fc 0 -ra <u>080d0400</u> -ih <u>080d0000</u> -ua 08010000 -nh 0-un 0

此指令修改后，生成 w800.img

7) w800_ota.img 固件

wm_tool.exe -b w800.img -o w800 -it $img_type -fc 0 -ra 080d0400 -ih 080d0000 -ua 08010000 -nh 0-un 0

##### 5.2.2.2 举例

如果用户编译的 IMAGE 大小为
W800.img：560KByte

压缩后 img：400KByte

把 IMAGE 的大小向上取 64KByte 的整数倍（重要），则

运行区空间：576KByte

升级区空间：448KByte

配置步骤如下:

1) 用户的新空间如图黄色部分

![image-20201114100313591](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114100313591.png)

2) 新的代码空间调整为：

![image-20201114100336189](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_Parameter/image-20201114100336189.png)

3) w800.img 生成修改为：
wm_tool.exe -b w800.bin -o w800 -it $img_type -fc 0 -ra 08080400 -ih 08080000 -ua 08010000 -nh 0 -un0

4) w800_ota.img 固件生成修改为：wm_tool.exe -b w800.img -o w800 -it $img_type -fc 0 -ra 08080400 -ih 08080000 -ua 08010000 -nh 0-un 

5) 重新编译烧录 W800.img 文件，模块启动后，用户参数区即变为新的设定值。

#### 5.2.3 用户参数区的双备份机制

如果用户参数区会记录关键信息，建议用户实现双备份机制，主区和备区按照 4Kbyte间隔划分。

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