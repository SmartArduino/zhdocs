<center><font size=10> W800_ROM功能简述 </center></font>
<center> From SZDOIT</center>

## 1 引言

### 1.1 概述

本文档是对 W800 的 ROM 功能及使用说明进行简单描述，供开发者和设计者理解
W800 的 ROM 功能。

### 1.2 术语定义

![image-20201114084248740](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114084248740.png)

## 2 ROM 基本功能

### 2.1 ROM 流程图

![image-20201114084449368](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114084449368.png)

### 2.2 引导程序

#### 2.2.1 QFLASH 自检

完成 QFLASH 工作状态检查

#### 2.2.2 QFLASH 模式切换

ROM 启动后，QFLASH 默认是 1 线模式。要使得程序能够运行于 QFLASH，ROM 需要把 QFLASH 切换到 4 线模式。

#### 2.2.3 IMAGE 校验

完成 IMAGE 头校验和 IMAGE 内容校验

#### 2.2.4 向量表重定向

W800 的程序最终是要运行在 QFLASH 里（代码的运行基址：0x8000000），因此需要对向量表进行重定向。
重定向地址规则：（异常向量+中断）总共是 64 个 word，根据 VBR 寄存器的要求，向量表地址必须是 0x400 的整数倍。

### 2.3 升级程序

利用 Xmodem 协议实现把 IMAGE 升级到 QFLASH 或内存区域，升级到内存区域的Image 在升级完成后即跳转到内存执行，升级的 FLASH 的需要重启后跳转执行。升级 IMAGE 格式：

![image-20201114084602692](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114084602692.png)

W800 的 IMAGE 包括 header、image area 和 signature 三部分。Header 包含magic_no、img_attr 等内容，其中 img_attr 是一个 Uint32 类型，包含 img_type、code_encrypt 等字段。
W800 的 IMAGE header 字段描述：

![image-20201114084638592](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114084638592.png)

W800 的 IMAGE Attribute 字段描述：

![image1](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image1.png)

W800 的 Flash 区域划分：

![image-20201114085010140](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114085010140.png)

ROM 程序根据 upgrade_area_addr 参数，判断第一个 header 的 img_type 是否为sec boot，如果是，在校验 header 和 img 的 crc 和签名，比较版本号，如果校验通过并且版本更新，则将 header 搬到 img_header_addr 的地址，将 img 和 signature 搬到img_addr 的地址。

ROM 程序根据 img_header_addr 参数，找到 SECBOOT 程序的 img header，校验img header 和 img 的 crc 和签名成功后，跳转 img_addr 执行 SECBOOT。

SECBOOT 程序根据 upgrade_area_addr 参数，依次遍历 header，直至 img_type是 img 的 header，然后类似 ROM 程序，搬运 header 到 next_img_addr 的地址，搬运img 和 signature 到 img_addr 的地址。

升级区可以支持包含 SECBOOT 在内的多个 img 升级，仅需要将待升级程序首尾相接放在 upgrade_area_addr 的地址即可。

对 于 header 中 zip_type=1 的 img ， img 部 分 是 将 原 始 img 的header+img+signature 三部分压缩后的结果，搬运前先解压。SECBOOT 不支持压缩。

### 2.4 OTP 参数区

W800 的 OTP 参数区存放一些有关固件升级和签名验证相关的参数。

### 2.5 测试程序

W800 针对芯片测试阶段的测试程序，没有放在 ROM 中，需要测试前先通过 uartxmodem 的方式升级到内存或 Flash 中运行。

### 2.6 操作指令

W800 的 ROM 程序支持模块生产阶段的部分操作：波特率切换，QFLASH ID 和容量获取，获取 ROM 版本，系统重启等。
指令发送方式：十六进制

#### 2.6.1 命令列表

![image2](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image2.png)

#### 2.6.2 常用指令集合

波特率变更：

2M 设置指令： 21 0a 00 ef 2a 31 00 00 00 80 84 1e 00

1M 设置指令： 21 0a 00 5e 3d 31 00 00 00 40 42 0f 00

921600 设置指令： 21 0a 00 5d 50 31 00 00 00 00 10 0e 00

460800 设置指令： 21 0a 00 07 00 31 00 00 00 00 08 07 00

115200 设置指令： 21 0a 00 97 4b 31 00 00 00 00 c2 01 00

BT MAC 地址获取： 21 06 00 D8 62 34 00 00 00

WiFi MAC 地址获取： 21 06 00 ea 2d 38 00 00 00

获取上一个错误： 21 06 00 36 B6 3B 00 00 00

QFLASH ID 和容量获取：21 06 00 1b e7 3c 00 00 00

获取 ROM 版本： 21 06 00 73 0a 3e 00 00 00

系统重启： 21 06 00 c7 7c 3f 00 00 00

QFlash 擦除(1M)： 21 0a 00 e2 25 32 00 00 00 02 00 fe 00

QFlash 擦除(2M)： 21 0a 00 c3 35 32 00 00 00 02 00 fe 01

### 2.7 ROM 的错误码

ROM 启动过程中，如果遇到异常，则会进入 ROM 右侧死循环程序，然后打印一个错误码，指示当前遇到的错误信息，供使用者分析遇到的问题。错误码定义如下:

![image3](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image3.png)

## 3 QFLASH 和 RAM 使用情况

### 3.1 QFLASH 布局

W800 支持四地址模式，最大支持 128MB Flash，但是，ROM 程序仅支持三地址模式，最大支持 16MB 地址访问。
ROM 视角的 QFLASH 布局：

![image-20201114090057824](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114090057824.png)

### 3.2 RAM 的使用

W800 的内存分成两块：160Kbyte 和 128Kbyte，ROM 里的分布如下：

![image-20201114090200382](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/System_Function/W800_ROM/image-20201114090200382.png)



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