<center><font size=10> W600_芯片产品规格书 </center></font>
<center> From SZDOIT</center>



# 1. 概述

W600是北京联盛德自主研发设计的一款嵌入式WiFi芯片，该系列模块支持标准的802.11 b/g/n 协议，内置完整的 TCP/IP 协议栈。

![image-20201026101008377](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026101008377.png)

W600\_SoC芯片集成 Cortex-M3 内核，内置 Flash，集成射频收发前端 RFTransceiver，CMOS PA 功率放 大器，基带处理器/媒体访问控制，支持SDIO、SPI、UART、GPIO、I²C、PWM、I²S、7816 等接口, 支持多种加解密协议，如 PRNG(Pseudo random Number Generator)/ SHA1/ MD5/ RC4/DES/ 3DES/ AES/ CRC 等。

W600是一款支持多接口、多协议的无线局域网 IEEE802.11n（1T1R）的 SoC 芯片。适用于智能家
电、智能家居、无线音视频、智能玩具、医疗监护、工业控制等物联网应用领域。

# 2. 特征

![image-20201026101512407](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026101512407.png)

![image-20201026101637654](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026101637654.png)

![image-20201026101704041](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026101704041.png)

![image-20201026101724045](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026101724045.png)

# 3. 芯片特点

该SoC芯片集成 Cortex-M3内核，内置 Flash，集成射频收发前端 RF Transceiver，CMOS PA功率放大器，基带处理器/媒体访问控制，支持 SDIO、SPI、UART、GPIO、I²C、PWM、I²S、7816等接口, 支持多种加解密协议，如 PRNG(Pseudo random Number Generator)/ SHA1/ MD5/ RC4/ DES/ 3DES/AES/ CRC等。

# 4. 芯片结构

![image-20201026102000423](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026102000423.png)

# 5. 地址空间划分

![image-20201026102326233](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026102326233.png)

![image-20201026102401721](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026102401721.png)
![image-20201026102458003](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026102458003.png)
![image-20201026102520675](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026102520675.png)

# 6. 功能描述

## 6.1 SDIO 设备控制器

SDIO2.0 设备端接口，完成与主机数据的交互。内部集成 1024Byte 的异步 FIFO，完成主机与芯片的
数据交互。

- 兼容 SDIO 卡规范 2.0

- 支持主机速率 0~50MHz

- 支持最大 1024 字节的 Block

- 支持软复位功能

- 支持 SPI、1 比特 SD 和 4 比特 SD 模式

## 6.2 高速 SPI 设备控制器

兼容通用 SPI 物理层协议，通过约定与主机交互的数据格式，主机对设备的高速访问，最高支持工作
频率为 50Mbps。

- 兼容通用 SPI 协议；

- 可选择的电平中断信号；

- 最高支持 50Mbps 速率；

- 简单的帧格式，全硬件解析与 DMA；

## 6.3 DMA 控制器

最多支持 8 通道，16 个 DMA 请求源，支持链表结构与寄存器控制。

- Amba2.0 标准总线接口，8 路 DMA 通道；

- 支持基于存储器链表结构的 DMA 操作；

- 软件配置 16 个硬件请求源；

- 支持 1，4-burst 操作模式；

- 支持 byte、half-word，word 操作；

- 源、目的地址不变或顺序递增可配置或在预定义地址范围内循环操作；

- 同步 DMA 请求和 DMA 响应硬件接口时序；

## 6.4 时钟与复位

支持芯片时钟和复位系统的控制，时钟控制包括时钟变频，时钟关断以及自适应门控；复位控制包括
系统以及子模块的软复位控制。

## 6.5 内存管理器

支持发送接收缓存大小的配置，以及 MAC 访问缓存的基址，缓存个数，帧聚合上限等控制信息。

## 6.6 数字基带

支持 IEEE802.11a/b/g/e/n（1T1R）发射和接收机算法实现，主要参数：

- 数据速率：1~54Mpbs（802.11a/b/g）， 6.5~150Mbps(802.11n)；

- MCS 格式：MCS0~MCS7，MCS32(40MHz HT Duplicate 模式)；

- 支持 40MHz 带宽 non-HT Duplicate 模式，6M～54M；

- 信号带宽：20MHz, 40MHz；

- 调制方式：DSSS(DBPSK,DQPSK,CCK)和 OFDM(BPSK,QPSK,16QAM,64QAM)；

- 实现 1T1R 的 MIMO-OFDM spatial multiplexing；

- 支持 Short GI 模式；

- 支持 legacy 模式与 Mixed 模式；

- 支持 40MHz 带宽下对 20M 上下边带信号的发射接收；

- 支持 MCS0～7、32 的 STBC 接收；

- 支持 Green Field 模式；

## 6.7 MAC 控制器

支持 IEEE802.11a/b/g/e/n MAC 子层的协议控制，具体规格包括：

- 支持 EDCA 信道接入方式；

- 支持 CSMA/CA，NAV 与 TXOP 保护机制；

- Beacon、Mng、VO、VI、BE、BK 五路发送队列与 QoS；

- 支持单、广组波帧接收发送；

- 支持 RTS/CTS，CTS2SELF，Normal ACK，No ACK 帧序列；

- 支持重传机制以及重传速率和功率控制；

- 支持 MPDU 硬件聚合解聚合与 Immediate BlockAck 模式；

- 支持 RIFS，SIFS，AIFS；

- 支持反向传输机制；

- 支持 TSF 计时，并且软件可配置；

- 支持 MIB 统计信息；

## 6.8 安全系统

支持 IEEE802.11a/b/g/e/n 协议规定的安全算法，配合完成发送接收数据帧的加解密。

- 满足加解密吞吐率大于 150Mbps；

- Amba2.0 标准总线接口；

- 支持 WAPI 安全模式 2.0；

- 支持 WEP 安全模式-64 位加密；

- 支持 WEP 安全模式-128 位加密；

- 支持 TKIP 安全模式；

- 支持 CCMP 安全模式；

## 6.9 FLASH 控制器

- 提供总线访问 FLASH 接口；

- 提供系统总线和数据总线访问仲裁；

- 实现 CACHE 缓存系统提高 FLASH 接口访问速度；

- 提供对不同 QFlash 的兼容性；

## 6.10 RSA 加密模块

RSA 运算硬件协处理器，提供 Montgomery(FIOS 算法)模乘运算功能。配合 RSA 软件库实现 RSA 算法。支持 128 位到 2048 位模乘。

## 6.11 通用硬件加密模块

加密模块自动完成指定长度的源地址空间数据的加密，完成后自动将加密数据回写到指定的目的地址
空间；支持 PRNG(Pseudo random Number Generator)/SHA1/MD5/RC4/DES/3DES/AES/CRC。

## 6.12 I 2 C 控制器

APB 总线协议标准接口，只支持主设备控制器，I²C 工作频率支持可配，100K—400K。

## 6.13 主/从 SPI 控制器

支持同步的 SPI 主从功能。其工作时钟为系统内部总线时钟。其特点如下：

- 发送和接收通路各有 8 个字深度的 FIFO；

- master 支持 Motorola SPI 的 4 种格式（CPOL，CPHA），TI 时序，macrowire 时序；

- slave 支持支持 Motorola SPI 的 4 种格式（CPOL，CPHA）；

- 支持全双工和半双工；

- 主设备支持 bit 传输，最大支持 65535bit 传输；

- 从设备支持各种长度 byte 的传输模式；

- 从设备输入的 SPI_Clk 最大时钟频率为系统时钟的 1/6；

## 6.14 UART 控制器

- 设备端符合 APB 总线接口协议；

- 支持中断或轮询工作方式；

- 支持 DMA 传输模式，发送接收各存在 32-byte FIFO；

- 波特率可编程；

- 5-8bit 数据长度，以及 parity 极性可配置；

- 1 或 2 个 stop 位可配置；

- 支持 RTS/CTS 流控；

- 支持 Break 帧发送与接收；

- Overrun，parity error，frame error，rx break frame 中断指示；

- 最大 16-burst byte DMA 操作；

## 6.15 GPIO 控制器

48 位可配置的 GPIO、软件控制的输入输出、硬件控制的输入输出、可配置中断方式。
GPIOA 和 GPIOB 寄存器起始地址不同，但是功能一致。

## 6.16 定时器

微秒与毫秒计时（据时钟频率配置计数个数），实现六个可配置的 32 位计数器，当相应计算器配置的
计数完成时，产生相应中断。

## 6.17 看门狗控制器

支持“看门狗”功能。观察软件形为的正确性及允许系统崩溃后进行全局复位。“看门狗”产生一个周期性的中断，系统软件必须响应这个中断，并清除中断标志；若由于系统崩溃中断标志很长时间没有被清除，则产生一个硬复位进行系统的全局复位。

## 6.18 射频配置器

实现了同步的 SPI 主功能。其工作时钟为系统内部总线时钟。其特点如下：

- 发送和接收通路各有 1 个字深度的 FIFO；

## 6.19 射频收发器

- 射频收发器部分包括功率放大器、发射通路、接收通路、锁相环以及 SPI 在内的模块。通过调整
  控制端口 SHDN, RXEN 和 TXEN 来改变芯片工作状态；

- 接收通路采用了零中频结构，直接将射频信号转换为基带I、Q两路输出。射频前端工作在2.4GHz，包含低噪放和正交混频器；基带由低通滤波器和可变增益放大器组成，实现信道滤波和增益控制；驱动放大器为 ADC 接口提供不同的直流输出；

- 发射通路包含：可编程控制滤波器，上变频混频器，可变增益放大器和功放，发射通路也采用直
  接变频结构。DAC 的输出信号经过低通滤波器，滤掉镜像频率及带外噪声。PA 输出是差分输出驱
  动片外天线；

## 6.20 PWM 控制器

- 5 通道 PWM 信号生成功能；

- 2 通道输入信号捕获功能（PWM0 和 PWM4 两个通路）；

- 频率范围：3Hz~160KHz；；

- 占空比最大精度：1/256，插入死区的计数器宽度：8bit；

## 6.21 I²S 控制器

- 支持 AMBA APB 总线接口，32bit single 读写操作；

- 支持主，从模式，可以双工工作；

- 支持 8/16/24/32 位宽，最高采样频率为 128KHz；

- 支持单声道和立体声模式；

- 兼容 I²S 和 MSB justified 数据格式，兼容 PCM A/B 格式；

- 支持 DMA 请求读写操作。只支持按字操作, 不支持按块操作

## 6.22 7816/UART 控制器

- 设备端符合 APB 总线接口协议；

- 支持中断或轮询工作方式；

- 支持 DMA 传输模式，发送接收各存在 32-byte FIFO；

- DMA 只能按字节进行操作，最大 16-burst byte DMA 操作；

兼容 UART 以及 7816 接口功能：
串口功能：

- 波特率可编程；
- 5-8bit 数据长度，以及 parity 极性可配置；
- 1 或 2 个 stop 位可配置；
- 支持 RTS/CTS 流控；
- 支持 Break 帧发送与接收；
- Overrun，parity error，frame error，rx break frame 中断指示；

7816 接口功能：
- 兼容 ISO-7816-3 T=0.T=1 模式；

- 兼容 EVM2000 协议；

- 可配置 guard time（11 ETU-267 ETU）；

- 正向/反向约定可软件配置；

- 支持发送/接收奇偶校验及重传功能；

- 支持 0.5 和 1.5 停止位配置；

# 7.管脚定义

![image-20201026104235629](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026104235629.png)

![image-20201026104316204](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026104316204.png)
![image-20201026104342610](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026104342610.png)

# 8. 电气特性

## 8.1 极限参数

| 参数             | 名称 | 最小值 | 典型值 | 最大值  | 单位 |
| :--------------- | :--: | :----: | :----: | :-----: | :--: |
| 供电电压         | VDD  |  3.0   |  3.3   |   3.6   |  V   |
| 输入逻辑电平低   | Vil  |  -0.3  |        |   0.8   |  V   |
| 输入逻辑电平高   | Vih  |  2.0   |        | VDD+0.3 |  V   |
| 输入引脚电容     | Cpad |        |        |    2    |  pF  |
| 输出逻辑电平低   | Vol  |        |        |   0.4   |  V   |
| 输出逻辑电平高   | Voh  |  2.4   |        |         |  V   |
| 输出最大驱动能力 | Imax |        |        |   24    |  mA  |
| 存储温度范围     | Tstr |  -40℃  |        |  +125℃  |  ℃   |
| 工作温度范围     | Topr |  -40℃  |        |  +85℃   |  ℃   |

## 8.2 射频功耗参数

![image-20201026105428661](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105428661.png)

## 8.3 Wi-Fi 射频

![image-20201026105453526](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105453526.png)
![image-20201026105511361](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105511361.png)

# 9. 封装信息

![image-20201026105558588](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105558588.png)

![image-20201026105757258](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105757258.png)
![image-20201026105823724](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105823724.png)

# 10. 产品型号定义

![image-20201026105926947](https://github.com/SmartArduino/zhdocs/raw/master/W_Series/W600/DateSheet/image-20201026105926947.png)

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

# 免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明。

# 注意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。