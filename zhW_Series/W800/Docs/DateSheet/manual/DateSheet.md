<center> <font size=10> W800数据手册 </font></center>

<center> from SZDOIT </center>


## 1 概述

W 800 芯片是一款安全 IoT Wi-Fi/蓝牙 双模 SoC芯片。支持2.4G IEEE802.11b/g/n Wi-Fi 通讯协议；支持 BT/BLE 双模工作模式，支持 BT/BLE4.2 协议。芯片集成 32 位 CPU 处理器，内置UART、GPIO、SPI、I^2 C、I^2 S、 7816 等数字接口；支持TEE安全引擎，支持多种硬件加解密算法，内置DSP、浮点运算单元与安全引擎，支持代码安全权限设置，内置2MBFlash存储器，支持固件加密存储、固件签名、安全调试、安全升级等多项安全措施，保证产品安全特性。适用于用于智能家电、智能家居、智能玩具、无线音视频、工业控制、医疗监护等广泛的物联网领域。

## 2 特征

##### ◼ 芯片外观

✓ QFN 32 封装， 4 mm x 4 mm

◼ MCU 特性
✓ 集成 32 位 XT 804 处理器，工作频率 240 MHz，内置DSP、浮点运算单元与安全引擎

✓ 内置 2 MB Flash，288KB RAM

✓ 集成 5 路 UART 高速接口

✓ 集成 2 路 16 比特 SD-ADC，最高采样率1KHz

✓ 集成 1 个I^2 C控制器

✓ 集成GPIO控制器，最多支持 18 个GPIO

✓ 集成 5 路PWM接口

✓ 集成 1 路 Duplex I^2 S控制器

◼ 安全特性



✓ MCU内置 Tee 安全引擎，代码可区分安全世界/非安全世界

✓ 集成 SASC/TIPC，内存及内部模块/接口可配置安全属性，防止非安全代码访问

✓ 启用固件签名机制，实现安全Boot/升级

✓ 具备固件加密功能，增强代码安全

✓ 固件加密密钥使用非对称算法分发，增强密钥安全性

✓ 硬件加密模块：RC4 256 、AES 128 、DES/ 3 DES、SHA1/MD 5 、CRC 32 、 2048 RSA,真随机数发生器

◼ Wi-Fi 特性

✓ 支持GB15629.11- 2006 ，IEEE802.11 b/g/n

✓ 支持Wi-Fi WMM/WMM-PS/WPA/WPA2/WPS

✓ 支持EDCA信道接入方式

✓ 支持20/40M带宽工作模式

✓ 支持STBC、GreenField、Short-GI、支持反向传输

✓ 支持AMPDU、AMSDU

✓ 支持IEEE802.11n MCS 0~7、MCS32物理层传输速率档位，传输速率最高到150Mbps

✓ 2/5.5/11Mbps速率发送时支持Short Preamble

✓ 支持HT-immediate Compressed Block Ack、Normal Ack、No Ack应答方式

✓ 支持CTS to self

✓ 支持Station、Soft-AP、Soft-AP/Station功能

◼ 蓝牙特性

✓ 集成蓝牙基带处理器/协议处理器，支持BT/BLE 双模工作模式，支持BT/BLE4.2 协议

◼ 电源管理

✓ 3.3V单电源供电

✓ 支持Wi-Fi节能模式功耗管理

✓ 支持工作、睡眠、待机、关机工作模式

✓ 待机功耗小于 10 uA



## 3 芯片结构

![image-20201028174046935](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174046935.png)


## 4 地址空间划分

![image-20201028174206364](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174206364.png)
![image-20201028174451384](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174451384.png)
![image-20201028174542596](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174542596.png)
![image-20201028174736381](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174736381.png)
![image-20201028174846408](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174846408.png)
![image-20201028174957769](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028174957769.png)
![image-20201028175026085](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028175026085.png)
![image-20201028175107527](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028175107527.png)
![image-20201028175140117](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028175140117.png)

## 5 功能描述

### 5.1 DMA控制器

最多支持 8 通道， 16 个DMA请求源，支持链表结构与寄存器控制。

⚫ Amba2.0标准总线接口， 8 路DMA通道

⚫ 支持基于存储器链表结构的DMA操作

⚫ 软件配置 16 个硬件请求源

⚫ 支持 1 ， 4 - burst操作模式

⚫ 支持byte、half-word，word操作

⚫ 源、目的地址不变或顺序递增可配置或在预定义地址范围内循环操作

⚫ 同步DMA请求和DMA响应硬件接口时序

### 5.2 时钟与复位

 支持芯片时钟和复位系统的控制，时钟控制包括时钟变频，时钟关断以及自适应门控；复位控制包括系统以及子模块的软复位控制。

### 5.3 内存管理器

 支持发送接收缓存大小的配置，以及MAC访问缓存的基址，缓存个数，帧聚合上限等控制信息。

### 5.4 数字基带

支持IEEE802.11a/b/g/e/n（1T1R）发射和接收机算法实现，主要参数：

⚫ 数据速率：1~54Mpbs（802.11a/b/g）， 6.5~150Mbps(802.11n)

⚫ MCS格式：MCS0~MCS7，MCS32(40MHz HT Duplicate模式)

⚫ 支持40MHz带宽non-HT Duplicate模式，6M～54M

⚫ 信号带宽：20MHz, 40MHz

⚫ 调制方式：DSSS(DBPSK,DQPSK,CCK)和OFDM(BPSK,QPSK,16QAM,64QAM)

⚫ 实现1T1R的MIMO-OFDM spatial multiplexing

⚫ 支持Short GI模式

⚫ 支持legacy模式与Mixed模式

⚫ 支持40MHz带宽下对20M上下边带信号的发射接收

⚫ 支持MCS0～ 7 、 32 的STBC接收

⚫ 支持Green Field模式




### 5.5 MAC控制器

支持IEEE802.11a/b/g/e/n MAC子层的协议控制，具体规格包括：

⚫ 支持EDCA信道接入方式

⚫ 支持CSMA/CA，NAV与TXOP保护机制

⚫ Beacon、Mng、VO、VI、BE、BK五路发送队列与QoS

⚫ 支持单、广组波帧接收发送

⚫ 支持RTS/CTS，CTS2SELF，Normal ACK，No ACK帧序列

⚫ 支持重传机制以及重传速率和功率控制

⚫ 支持MPDU硬件聚合解聚合与Immediate BlockAck模式

⚫ 支持RIFS，SIFS，AIFS

⚫ 支持反向传输机制

⚫ 支持TSF计时，并且软件可配置

##### ⚫ 支持MIB统计信息



### 5.6 安全系统

支持IEEE802.11a/b/g/e/n协议规定的安全算法，配合完成发送接收数据帧的加解密。
⚫ 满足加解密吞吐率大于150Mbps

⚫ Amba2.0标准总线接口

⚫ 支持WAPI安全模式2.

⚫ 支持WEP安全模式- 64 位加密

⚫ 支持WEP安全模式- 128 位加密

⚫ 支持TKIP安全模式

⚫ 支持CCMP安全模式



### 5.7 FLASH控制器

⚫ 提供总线访问FLASH接口

⚫ 提供系统总线和数据总线访问仲裁

⚫ 实现CACHE缓存系统提高FLASH接口访问速度


⚫ 提供对不同QFlash的兼容性

### 5.8 RSA加密模块

RSA运算硬件协处理器，提供Montgomery(FIOS算法)模乘运算功能。配合RSA软件库实现RSA算法。
支持 128 位到 2048 位模乘。

### 5.9 通用硬件加密模块

 加密模块自动完成指定长度的源地址空间数据的加密，完成后自动将加密数据回写到指定的目的地址空间；

支持SHA1/MD5/RC4/DES/3DES/AES/CRC/TRNG。

⚫ 支持SHA1/MD5/RC4/DES/3DES/AES/CRC/TRNG加密算法

⚫ DES/3DES支持ECB和CBC两种模式

⚫ AES支持ECB、CBC和CTR三种模式

⚫ CRC支持CRC8、CRC16_MODBUS、CRC16_CCITT和CRC32四种模式

⚫ CRC支持输入/输出反向

⚫ SHA1/MD5/CRC支持连续多包加密

⚫ 内置真随机数发生器，也支持seed种子产生伪随机数



### 5.10 I^2 C控制器

APB总线协议标准接口，只支持主设备控制器，I²C工作频率支持可配，100K—400K。

### 5.11 主/从SPI控制器

支持同步的SPI 主从功能。其工作时钟为系统内部总线时钟。其特点如下：
⚫ 发送和接收通路各有 8 个字深度的FIFO

⚫ master支持Motorola SPI的 4 种格式（CPOL，CPHA），TI时序，macrowire时

⚫ slave支持支持Motorola SPI的 4 种格式（CPOL，CPHA）；

⚫ 支持全双工和半双工

⚫ 主设备支持bit传输，最大支持 6553 5bit传输

⚫ 从设备支持各种长度byte的传输模式

⚫ 从设备输入的SPI_Clk最大时钟频率为系统时钟的1/



### 5.12 UART控制器



⚫ 设备端符合APB总线接口协议

⚫ 支持中断或轮询工作方式

⚫ 支持DMA传输模式，发送接收各存在 32 - byte FIFO

⚫ 波特率可编程

⚫ 5 - 8bit 数据长度，以及parity极性可配置

⚫ 1 或 2 个stop位可配置

⚫ 支持RTS/CTS流控

⚫ 支持Break帧发送与接收

⚫ Overrun，parity error，frame error，rx break frame中断指示

⚫ 最大 16 - burst byte DMA操作



### 5.13 GPIO控制器

 可配置的GPIO、软件控制的输入输出、硬件控制的输入输出、可配置中断方式。

 GPIOA和GPIOB寄存器起始地址不同，但是功能一致。

### 5.14 定时器

 微秒与毫秒计时（据时钟频率配置计数个数），实现六个可配置的 32 位计数器，当相应计算器配置的计数完 成时，产生相应中断。

### 5.15 看门狗控制器

支持“看门狗”功能。观察软件形为的正确性及允许系统崩溃后进行全局复位。“看门狗”产生一个周期性 的中断，系统软件必须响应这个中断，并清除中断标志；若由于系统崩溃中断标志很长时间没有被清除，则 产生一个硬复位进行系统的全局复位。

### 5.16 射频配置器

实现了同步的SPI 主功能。其工作时钟为系统内部总线时钟。其特点如下：

⚫ 发送和接收通路各有 1 个字深度的FIFO


### 5.17 射频收发器

⚫ 射频收发器部分包括功率放大器、发射通路、接收通路、锁相环以及SPI在内的模块。通过调整控制端口SHDN, RXEN 和TXEN来改变芯片工作状态

⚫ 接收通路采用了零中频结构，直接将射频信号转换为基带I、Q两路输出。射频前端工作在2.4GHz，
包含低噪放和正交混频器；基带由低通滤波器和可变增益放大器组成，实现信道滤波和增益控制；驱动放大器为ADC接口提供不同的直流输出

⚫ 发射通路包含：可编程控制滤波器，上变频混频器，可变增益放大器和功放，发射通路也采用直接变频结构。DAC的输出信号经过低通滤波器，滤掉镜像频率及带外噪声。PA输出是差分输出驱动片外天线

### 5.18 PWM控制器

 ⚫ 5 通道PWM信号生成功能

 ⚫ 2 通道输入信号捕获功能（PWM0 和PWM4两个通路）

 ⚫ 频率范围： 3 Hz~160KHz

 ⚫ 占空比最大精度： 1 /256，插入死区的计数器宽度：8bit



### 5.19 I²S控制器

⚫ 支持AMBA APB总线接口，32bit single读写操作

⚫ 支持主，从模式，可以双工工作

⚫ 支持 8 / 16 / 24 / 32 位宽，最高采样频率为128KHz

⚫ 支持单声道和立体声模式

⚫ 兼容I²S和MSB justified 数据格式，兼容PCM A/B格式

⚫ 支持DMA请求读写操作。只支持按字操作


### 5.20 7816/UART控制器

⚫ 设备端符合APB总线接口协议

⚫ 支持中断或轮询工作方式

⚫ 支持DMA传输模式，发送接收各存在 32 - byte FIFO

⚫ DMA只能按字节进行操作，最大 16 - burst byte DMA操作

兼容UART以及 7816 接口功能：
串口功能：
⚫ 波特率可编程

⚫ 5 - 8bit 数据长度，以及parity极性可配置

⚫ 1 或 2 个stop位可配置

⚫ 支持RTS/CTS流控

⚫ 支持Break帧发送与接收

⚫ Overrun，parity error，frame error，rx break frame中断指示

7816 接口功能：

⚫ 兼容 ISO- 7816 - 3 T=0.T=1 模式

⚫ 兼容EVM2000协议

⚫ 可配置guard time（11 ETU-267 ETU）

⚫ 正向/反向约定可软件配置

⚫ 支持发送/接收奇偶校验及重传功能

⚫ 支持0.5和1.5停止位配置

## 6 管脚定义

![image-20201028175754745](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028175754745.png)


##### 

![image-20201028180130901](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180130901.png)
![image-20201028180209226](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180209226.png)
![image-20201028180254795](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180254795.png)
![image-20201028180331978](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180331978.png)
![image-20201028180353128](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180353128.png)

## 7 电气特性

### 7.1 极限参数

![image-20201028180522388](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180522388.png)



### 7.2 射频功耗参数

![image-20201028180653376](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180653376.png)
![image-20201028180753519](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180753519.png)

### 7.3 Wi-Fi射频

![image-20201028180913937](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180913937.png)
![image-20201028180948110](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028180948110.png)
![image-20201028181010399](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181010399.png)

### 7.4 蓝牙射频

#### 7.4.1 传统蓝牙射频

![image-20201028181507703](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181507703.png)
![image-20201028181529979](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181529979.png)

![image-20201028181600862](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181600862.png)
![image-20201028181735963](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181735963.png)

![image-20201028181809282](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181809282.png)
![image-20201028181904401](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181904401.png)

![image-20201028181936948](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028181936948.png)
![image-20201028182010331](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182010331.png)
![image-20201028182026268](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182026268.png)

#### 7.4.2 低功耗蓝牙射频

![image-20201028182140283](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182140283.png)

![image-20201028182156305](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182156305.png)
![image-20201028182221593](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182221593.png)

## 8 封装信息

![image-20201028182323706](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182323706.png)

![image-20201028182431555](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182431555.png)

![image-20201028182443920](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/DateSheet/manual/image-20201028182443920.png)

