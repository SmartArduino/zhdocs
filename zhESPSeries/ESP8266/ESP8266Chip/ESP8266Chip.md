<center><font size=10> ESP8266芯片数据手册 </center></font>
<center> From SZDOIT</center>

## 1. 概述

ESP8266EX 由乐鑫公司开发，提供了了一套高度集成的 Wi-Fi SoC 解决方案，其低功耗、紧凑设计和高稳定性可以满足用户的需求。

![image-20201222153513132](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222153513132.png)

ESP8266EX 拥有完整的且自成体系的 Wi-Fi 网络功能，既能够独立应用，也可以作为从机搭载于其他主机 MCU 运行行。当 ESP8266EX 独立应用时，能够直接从外接 Flash 中启动。内置的高速缓冲存储器器有利利于提高系统性能，并且优化存储系统。此外 ESP8266EX 只需通过SPI/SDIO 接口或 I2C/UART 口即可作为 Wi-Fi 适配器器，应用到基于任何微控制器器的设计中。

ESP8266EX 集成了了天线开关、射频 balun、功耗放大器器、低噪放大器器、过滤器器和电源管理理模块。这样紧凑的设计仅需极少的外部电路路并且将 PCB 的尺寸降到最小。

ESP8266EX 还集成了了增强版的 Tensilica’s L106 钻⽯石系列列 32-bit 内核处理理器器，带片上SRAM。ESP8266EX 可以通过 GPIO 外接传感器器和其他设备。软件开发包 (SDK) 提供了了一些应用的示例例代码。

乐鑫智能互联平台 (ESCP-Espressif Systems’ Smart Connectivity Platform) 表现出来的领先特征有：睡眠/唤醒模式之间的快速切换以实现节能、配合低功耗操作的自适应射频偏置、前端信号的处理理功能、故障排除和射频共存机制可消除蜂窝/蓝牙/DDR/LVDS/LCD 干扰。

### 1.1. Wi-Fi 协议

• 支持 802.11 b/g/n/e/i。

• 支持 Wi-Fi Direct (P2P)。

• P2P 发现，P2P GO 模式 (Group Owner)、GC 模式 (Group Client) 和 P2P 电源管理理。

• 基础结构型网络 (Infrastructure BSS) 工作站 (Station) 模式/P2P 模式/SoftAP 模式。

• 支持 CCMP（CBC-MAC、计数器器模式）、TKIP (MIC、RC4)、WAPI (SMS4)、WEP(RC4)、CRC 的硬件加速器器。

• WPA/PA2 PSK 和 WPS。

• 802.11 i 安全特征：预认证和 TSN。

• 针对企业级平台的开放接口，例例如 TLS、PEAP、LEAP、SIM、AKA 或者客户自定义接口。

• 支持 802.11n (2.4 GHz)。

• 支持 MIMO 1×1 和 2×1、STBC、A- MPDU 和 A-MSDU 帧聚合技术、0.4 μs 的保护间隔。

• WMM 低功耗 U-APSD。

• 多队列列管理理，充分利利用 802.11e 标准的 QoS 传输优先。

• UMA 认证标准。

• 802.1h/RFC1042 帧封装。

• 分散 DMA，实现数据传输操作时 Zero Copy，优化 CPU 负载。

• 天线分集与选择（软件控制硬件）。

• 时钟/电源门控与符合 802.11 标准的电源管理理一起动态地适应当前连接条件，实现最小功耗。

• 自适应速率回退算法基于实际信噪⽐比 (SNR) 和丢包信息来控制最佳传输速率和发射功耗。

• MAC 层上的自动重传和回复以防止在慢速主机环境中的数据包丢弃。

• 无缝漫游支持。

• 可配置的包仲裁 (PTA) 和基于专用的从机处理理器器的设计为大量量蓝牙芯片供应商提供灵活而精确的 Wi-Fi 和蓝牙共存模式。

• 双天线或单天线的蓝牙共存方式，支持分时接收（Wi-Fi/蓝牙）的功能。

### 1.2. 技术参数

![image1](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image1.png)

### 1.3 应用

• 家用电器器

• 家庭自动化

• 智能插座、智能灯

• Mesh 网络

• 工业无线控制

• 婴儿监控器器

• IP 摄像机

• 传感器器网络

• 可穿戴电子产品

• 无线位置感知设备

• 安全 ID 标签

• 无线定位系统信标

## 2. 管脚定义

![image-20201222154635001](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222154635001.png)

管脚定义如表 2-1 所示。

![image2](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image2.png)

## 3. 功能描述

ESP8266EX 的功能原理理如图 3-1 所示。

![image-20201222154956754](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222154956754.png)

### 3.1. CPU、存储和 Flash

#### 3.1.1. CPU

ESP8266EX 内置 Tensilica L106，32-bit 微处理理器器 (MCU)，具有超低功耗的 16-bit RSIC。CPU 时钟速度为 80 MHz，最高可达 160 MHz。支持实时操作系统 (RTOS)。目前 Wi-Fi 协议栈只用了了 20% 的 MIPS，其他的都可以用来做应用编程和开发。CPU 包括以下接口。

• 可连接片内存储控制器器和外部 Flash 的可配置 RAM/ROM 接口 (iBus)

• 连接存储控制器器的数据 RAM 接口 (dBus)

• 访问寄存器器的 AHB 接口

#### 3.1.2 内置存储

ESP8266EX 芯片内置了了存储控制器器，包含 ROM 和 SRAM。MCU 可以通过 iBus、dBus和 AHB 接口访问存储控制器器。在发起请求后，所有存储单元都可以被访问。存储仲裁器器会根据处理理器器接受这些请求的时间，决定访问顺序。

根据目前我司提供的 SDK，当 ESP8266EX 运行行在 Station 模式下，连上路路由后，在Heap+Data 区用户可用 SRAM 空间为 50 kB。

芯片内无可编程存储器器，用户程序必须由外部 Flash 存储。

#### 3.1.1 外置 Flash

ESP8266EX 使用外置 SPI Flash 存储用户程序。理理论上最大可支持 16 MB 的存储。

建议按照如下所示来分配 SPI Flash 容量量。

• 不不支持 OTA：最少支持 512 kB

• 可支持 OTA：最少支持 1 MB

![image-20201222155400733](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222155400733.png)

### 3.2. AHB 和 AHB 模块

AHB 模块充当仲裁器器，通过 MAC、主机的 SDIO 和 CPU 控制 AHB 接口。由于发送地址不同，AHB 数据请求可能到达以下两个从机中的一个。

• APB 模块

• 闪存控制器器（通常在无主机的情况下）

高速请求一般是用来访问 Flash 控制器器，而访问寄存器器通过的是 APB 模块。

APB 模块充当解码器器。但只可以访问 ESP8266EX 主模块内可编程的寄存器器。由于发送地址不不同，APB 请求可能到达射频接收器器、SI/SPI、主机 SDIO、GPIO、UART、实时时钟(RTC)、MAC 或数字基带。

### 3.3. 时钟

#### 3.3.1. 高频时钟

基于外部晶振，ESP8266EX 内部晶体振荡器器可以生成射频时钟。该时钟可用于驱动 Tx 和Rx 混频器器。晶振频率在 24 MHz 到 52 MHz 之间。

尽管晶体振荡器器的内部校准功能使得一系列列的晶体满足时钟生成条件，但是晶体的质量量仍然是影响获得合适的相位噪声和 Wi-Fi 灵敏敏度的因素。请参照表 3-1 来测量量频率偏移。

![image3](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image3.png)

#### 3.3.2. 外部时钟参考要求

外部时钟的频率在 24 MHz 到 52 MHz 之间。为了了使射频性能良好，时钟需满⾜足要求如表3-2 所示。

![image-20201222155830574](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222155830574.png)

### 3.4. 射频

ESP8266EX 射频主要包含以下模块。

• 2.4 GHz 接收器器

• 2.4 GHz 发射器器

• 高速时钟生成器器和晶体振荡器器

• 实时时钟

• 偏置电路路与稳压器器

• 电源管理理

#### 3.4.1. 信道频率

根据 IEEE802.11b/g/n 标准，射频收发器器支持以下信道。

![image-20201222160151901](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222160151901.png)

#### 3.4.2. 2.4 GHz 接收器器

2.4 GHz 接收器器把射频信号降频，变成正交基带信号，用 2 个高分辨率的高速 ADC 将后者转为数字信号。为了适应不同的信号频道，ESP8266EX 集成了射频滤波器器、自动增益控制 (AGC)、DC 偏移补偿电路路和基带滤波器器。

#### 3.4.3. 2.4 GHz 发射器器

2.4 GHz 发射器器将正交基带信号升频到 2.4 GHz，使用大功耗互补金金属氧化物半导(CMOS) 功耗放大器器驱动天线。数字校准的使用进一步地改善了了功耗放大器器的线性，从而在802.11b 传输中达到 +19.5 dBm 的平均功耗，在 802.11n 传输中达到 +16 dBm 的平均功耗，功能超强。

为了了抵消无线电接收器器的瑕疵，ESP8266EX 还另增了了以下校准措施。

• 载波泄露露

• I/Q 相位匹配

• 基带非线性

这些内置的校准措施减少了了生产测试所需的时间和设备。

#### 3.4.4. 时钟生成器器

时钟生成器器为接收器器和发射器器生成 2.4 GHz 正交基带时钟信号，其所有部件均集成于芯片上，包括：电感器器、变容二极管、闭环滤波器器、监管者和分频器器。

时钟生成器器含有内置校准电路路和自测电路路。正交时钟相位和相位噪声通过拥有专利利的校准算法在芯片上进行行最优处理理，以确保接收器器和发射器器达到最佳性能。

### 3.5. Wi-Fi

ESP8266EX 支持 TCP/IP 协议，完全遵循 802.11 b/g/n/e/i WLAN MAC 协议和 Wi-FiDirect 标准。它支持分布式控制功能 (DCF) 下的基本服务集 (BSS) 操作，也支持符合最新的 Wi-Fi P2P 协议的 P2P 团体操作。ESP8266EX 自动采用低层协议功能。

• RTS/CTS

• 确认字符

• 分片和重组

• 聚合

• 帧封装 (802.11h/RFC 1042)

• 自动信标监测/扫描

• P2P Wi-Fi direct

跟 P2P 发现程序一样，被动或主动扫描一旦在适当的指令下起动，就会自主完成。执行电源管理理时，与主机互动最少，如此一来，工作时间达到最短。

### 3.6. 低功耗管理理

ESP8266EX 专为移动设备、可穿戴电⼦子产品和物联网应用设计，拥有先进的低功耗管理理技术。

节能模式共有三种：激活模式、睡眠模式和深度睡眠模式。ESP8266EX 在深度睡眠模式下（RTC 时钟仍处于工作状态）消耗的电流约为 20 μA；处于连接状态时消耗的电流少于1.0 mA (DTIM = 3) 或 0.6 mA (DTIM = 10)。

![image-20201222160813755](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222160813755.png)

• 关闭：CHIP_PU 管脚处于低功耗状态。RTC 停止工作。所有寄存器被清除。

• 深度睡眠：只有 RTC 处于工作状态，芯片的其他部分掉电。RTC 内部的备份恢复存储可保存基本的 Wi-Fi 连接信息。

• 睡眠：只有 RTC 在运行。晶体振荡器停止工作。任何唤醒事件（MAC、主机、RTC定时器或外部中断）都会唤醒芯片。

• 唤醒：在这种状态下，系统从睡眠状态进入起动 (PWR) 状态。晶体振荡器和 PLL 均进入使能状态。

• 开启：高速时钟可以运行行，并发送⾄至各个被时钟控制寄存器使能的模块。各个模块，包括 CPU 在内，执行行较低层的时钟门控。系统运作时，可以通过 WAITI 指令关闭 CPU 内部时钟。

## 4. 外设接口

### 4.1. 通用输入/输出接口 (GPIO)

ESP8266EX 共有 17 个 GPIO 管脚，通过配置适当的寄存器可以给它们分配不不同的功能。每个 GPIO 都可以配置为内部上拉/下拉，或者被设置为高阻。当被配置为输入时，可通过读取寄存器获取输入值；输入也可以被设置为边缘触发或电平触发来产生 CPU 中断。简⾔言之，IO 管脚是双向、非反相和三态的，带有三态控制的输入和输出缓冲器。

这些管脚可以与其他功能复用，例如 I2C、I2S、UART、PWM、IR 遥控、LED Light 和Button 接口等。

在低功耗模式下，GPIO 可被设定为保持状态。例例如，当芯片断电，所有输出使能信号都可以被设定为保持低功耗状态。

选择性的保持功能可以应需植入 IO 中。当 IO 不由内外部电路路驱动时，保持功能可以被用于保持上次的状态。保持功能给管脚引入一些正反馈。因此，管脚的外部驱动必须强于正反馈。脱离保持状态所需的驱动力很小，在 5 μA 之内。

### 4.2. SDIO

ESP8266EX 拥有 1 个从机 SDIO 接口，接口管脚定义如下表 4-1 所示。支持 4-bit 25 MHz SDIO v1.1 和 4-bit 50 MHz SDIO v2.0。

![image-20201222161337624](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222161337624.png)

### 4.3. 串行外设接口 (SPI/HSPI)

ESP8266EX 拥有 1 个通用从机/主机 SPI，1 个从机 SDIO/SPI，和 1 个通用从机/主机HSPI。所有接口的功能均由硬件实现。接口定义如下所示

#### 4.3.1. 通用 SPI（主机/从机）

![image-20201222161440407](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222161440407.png)

#### 4.3.2. HSPI（从机）

![image-20201222161509919](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222161509919.png)

### 4.4. I2C 接口

ESP8266EX 拥有 1 个 I2C 接口，用于连接微控制器以及外围设备，如传感器等。I2C 接定义如表 4-4 所示。

![image-20201222161603654](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222161603654.png)

### 4.5. I2S 接口

ESP8266EX 拥有 1 个 I2S 输入接口和 1 个 I2S 输出接口。I2S 主要用于音频数据采集、处理理和传输，也可用于串行数据输入输出，如支持 LED 彩灯（WS2812 系列列）。I2S 管脚定义如表 4-5 所示。I2C 接口功能可以使用复用 GPIO 通过软件编程实现，支持链表DMA。

![image-20201222161747485](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222161747485.png)

### 4.6. 通用异步收发器 (UART)

ESP8266EX 拥有两个 UART 接口，分别为 UART0 和 UART，接口定义如表 4-6 所示。

![image4](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image4.png)

### 4.7. 脉冲宽度调制 (PWM)

ESP8266EX 拥有 4 个 PWM 输出接口，如表 4-7 所示。用户可自行扩展。

![image-20201222162006541](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222162006541.png)

### 4.8. IR 遥控接口

ESP8266EX 芯片目前定义了了 1 个 IR 红外遥控接口，该接口定义如表 4-8 所示。

![image-20201222162041733](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222162041733.png)

### 4.9. ADC（模/数转换器器）

ESP8266EX 内置了一个 10-bit 精度的 SAR ADC。TOUT（管脚 6）定义如表 4-9 所示。

![image5](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image5.png)

### 4.10. LED Light 和 Button 接⼝口

ESP8266EX 拥有多达 17 个 GPIO 接口，均可定义作为 LED 与 Button 的控制接口。基于目前 ESP8266EX 一些示例例设计的应用，我们对 LED 与 Button 的 GPIO 接口定义如表 4-10 所示。

![image-20201222162309581](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222162309581.png)

## 5. 电气参数

### 5.1. 电气特性

![image-20201222162356003](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222162356003.png)

### 5.2. 功耗

![image6](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image6.png)

### 5.3. Wi-Fi 射频特征

表 5-3 中数据是在室内温度下，电压为 3.3V 和 1.1V 时分别测得。

![image-20201222162556650](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222162556650.png)

## 6. 封装信息

![image-20201222162618402](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/ESP8266/ESP8266Chip/image-20201222162618402.png)



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