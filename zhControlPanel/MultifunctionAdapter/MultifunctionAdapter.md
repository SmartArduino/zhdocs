 <center> <font size=10> USB转SPI/IIC/UART/MEM/EPP/TTL多功能适配器 </font></center>

<center> from SZDOIT </center>

# 一、产品简介

## 1.1 性能与技术指标

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps1.png) 

● 全速 USB 设备接口，兼容 USB V2.0;

● USB 总线供电，无需外部电源;

● 支持 5V 电源电压或 3.3V 电源电压输出;

● 支持 3.3V TTL、5V TTL 电平输出；

● 支持异步串口(UART 方式)：

Ø 仿真标准串口，用于升级原串口外围设备，或者通过 USB 增加额外串口

Ø 计算机端 Windows 操作系统下的串口应用程序完全兼容，无需修改

Ø 硬件全双工串口，内置收发缓冲区，支持通讯波特率 50bps～2Mbps

Ø 支持 5、6、7 或者 8 个数据位，支持奇校验、偶校验、空白、标志以及无校验

Ø 支持串口发送使能、串口接收就绪等传输速率控制信号和 MODEM 联络信号

Ø 通过外加电平转换模块，提供 RS232、RS485、RS422 等接口

Ø 支持以标准的串口通讯方式间接地访问 CH341 外挂的串行 EEPROM 存储器

● 支持打印并口扩展：

Ø 标准 USB 打印口，用于升级原并口打印机，兼容相关的 USB 规范

Ø 兼容 Windows 操作系统，在 Windows 2000 和 XP 下无需驱动程序， 应用程序完全兼容

Ø 支持各种标准的并口打印机，可选低速打印方式和高速打印方式



Ø 支持 IEEE-1284 规范的双向通讯

● 支持并口扩展：

Ø 提供两种接口方式：EPP 方式和 MEM 方式

Ø EPP 方式提供 AS#、DS#、WR#等信号，类似于 EPP V1.7 或 EPP V1.9

Ø MEM 方式提供 A0、RD#、WR#等信号，类似于存储器读写方式

● 支持同步串口（I2C/SPI 方式）：

Ø 采用 FlexWireTM 技术，通过软件能够实现灵活多样的 2 线到 5 线的同步串口

Ø 作为 Host/Master 主机端，支持 2 线和 4 线等常用的同步串行接口

Ø 2 线接口提供 SCL 和 SDA 两个信号线，支持 4 种传输速度

● 支 持 WINDOWS 98/ME/2000/XP/Server 2000/VISTA/Server 2008/Win7 32 位/64 位，通过微软数字签名认证

● 外形尺寸：75 x 33 x 13mm

● PCB 尺寸：55 x 33 x 1.6mm

● 工作温度： -40°C - +85°C

## 1.2 典型应用

● I2C 总线测试， I2C 接口的元器件寄存器读写，EEPROM 存储数据读写

● SPI 总线测试，SPI 接口 FLASH 芯片读写, 单片机程序下载

● 串口程序调试，单片机下载，STC ISP 下载

## 1.3 通信协议转换

● USB 与 I2C 总线接口协议转换；

● USB 与 SPI 总线接口协议转换；

● USB与 UART 串口通信协议转换；

## 1.4 产品清单

● USB 转 I2C/UART/SPI 适配器主板

## 二、外形与接口描述

## 2.1 产品外形

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps2.png) 

## 2.2 适配器对外接口定义

​	本适配器为多功能合一产品, 涉及接口有 SPI 接口, I2C 接口, UART 接口, I2C 与UART 接口，异步串口预留接口，打印并口等。

### 2.2.1 SPI 接口（XH2.54MM 直插针）

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps3.jpg) 

| 引脚名称 | IO 类型 | 描述                                   |
| -------- | ------- | -------------------------------------- |
| MISO     | I       | SPI 主机数据输入，接从设备的数据输出   |
| MOSI     | O       | SPI 主机数据输出，接从设备的数据输入   |
| SCK      | O       | SPI 主机时钟输出，最大支持 2MHz        |
| CS2      | O       | SPI 片 选 2                            |
| CS1      | O       | SPI 片选 1                             |
| CS0      | O       | SPI 片选 0                             |
| VDD      | P       | 电源输出，电压可为 3.3V 或者 5V 或者无 |
| GND      | P       | 信号地                                 |

### 2.2.2 I2C 接口（PH2.25MM 排针）

​	![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps4.jpg)

| 引脚名称 | IO 类型 | 描述                                   |
| -------- | ------- | -------------------------------------- |
| SDA      | I/O     | I2C 总线数据线                         |
| SCL      | O       | I2C 总线时钟输出，支持多种速率         |
| GND      | P       | 信号地                                 |
| VDD      | P       | 电源输出，电压可为 3.3V 或者 5V 或者无 |



 

### 2.2.3 UART 接口（PH2.25排针 ）

​	![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps5.jpg)

| 引脚名称 | IO 类型 | 描述                                       |
| -------- | ------- | ------------------------------------------ |
| RXD      | I       | 异步串口（UART）接收端，连接目标设备发送端 |
| TXD      | O       | 异步串口（UART）发送端，连接目标设备接收端 |
| GND      | P       | 信号地                                     |
| VDD      | P       | 电源输出，电压可为 3.3V 或者 5V 或者无     |

### 2.2.4 I2C 与UART 接口（XH2.5MM 弯插针）

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps6.jpg) 

| 引脚名称 | IO 类型 | 描述                                       |
| -------- | ------- | ------------------------------------------ |
| SCL      | O       | I2C 总线时钟输出，支持多种速率             |
| SDA      | I/O     | I2C 总线数据线                             |
| GND      | P       | 信号地                                     |
| VDD      | P       | 电源输出，电压可为 3.3V 或者 5V 或者无     |
| TNOW     | O       | 串口发送指示，高电平有效                   |
| RTS      | O       | MODEM 联络输出信号，请求发送，低有效       |
| CTS      | I       | MODEM 联络输入信号，清除发送，低有效       |
| RXD      | I       | 异步串口（UART）接收端，连接目标设备发送端 |
| TXD      | O       | 异步串口（UART）发送端，连接目标设备接收端 |
| GND      | P       | 信号地                                     |
| VDD      | P       | 电源输出，电压可为 3.3V 或者 5V 或者无     |

### 2.2.5 异步串口预留接口

​	异步串口即 UART 的全信号预留接口位于适配器主板正面中间位置，共 20 个插孔，可以安装双排 2.54MM 间距的插针或者 DC3-20P 简易牛角座。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps7.jpg) 

| 引脚序号 | 引脚名称 | IO 类型 | 描述                                               |
| -------- | -------- | ------- | -------------------------------------------------- |
| 1        | RXD      | I       | 串行数据输入，内置上拉电阻                         |
| 2        | TXD      | O       | 串行数据输出                                       |
| 3        | INT      | I       | 自定义中断请求，上升沿有效，内置上拉电阻           |
| 4        | IN3      | I       | 自定义通用输入信号，建议悬空不用                   |
| 5        | TEN      | I       | 串口发送使能，低电平有效，内置上拉电阻             |
| 6        | IN7      | I       | 自定义通用输入信号，建议悬空不用                   |
| 7        | TNOW     | O       | 串口发送正在进行的状态指示，高电平有效             |
| 8        | ROV      | TRI_O   | 三态输出,口接收缓冲区溢出，低电平有效              |
| 9        | GND      | P       | 信号地                                             |
| 10       | RDY      | O       | 串口接收就绪，低电平有效                           |
| 11       | D7       | TRI_O   | SLP#三态输出, 睡眠状态输出信号，低电平有效         |
| 12       | RTS      | TRI_O   | 三态输出,MODEM 联络输出信号，请求发送，低有效      |
| 13       | DTR      | TRI_O   | 三态输出, MODEM 联络输出信号，数据终端就绪，低有效 |
| 14       | OUT      | TRI_O   | 三态输出, 自定义通用输出信号，低电平有效           |
| 15       | DCD      | I       | MODEM 联络输入信号，载波检测，低有效               |
| 16       | RI       | I       | MODEM 联络输入信号，振铃指示，低有效               |
| 17       | DSR      | I       | MODEM 联络输入信号，数据装置就绪，低有效           |
| 18       | CTS      | I       | MODEM 联络输入信号，清除发送，低有效               |
| 19       | VCC      | P       | 电源，电压与芯片电压一致                           |
| 20       | PWR      | P       | 电源，电压可选与 VCC 或者 VDD 一致                 |

## 2.3 功能切换开关

​	适配器用哪种功能由适配器的 USB 转换芯片上电初始化状态决定，初始化过程完成芯片的功能配置，功能切换需要给适配器重新上电（重新插拔）。

### 2.3.1 I2C/SPI 与 UART 功能配置

​	适配器功能切换跳线位于 USB 接口旁，通过调整跳线冒的位置来实现常用功能之间的切换。

I2C 与 SPI 功能的配置相同，为![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps8.png)；UART 串口功能配置为![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps9.jpg)	。

### 2.3.2 MEM/EPP 等其他功能配置

​	适配器可以直接通过 SCL 和 SDA 引脚的连接组合来配置芯片的功能。

| SCL 和 SDA 的引脚状态  | 功能                            | 默认的产品 ID |
| ---------------------- | ------------------------------- | ------------- |
| SDA 悬空，SCL 悬空     | USB 转异步串口，仿真计算机串口  | 5523H         |
| SDA 接低电平，SCL 悬空 | USB 转 EPP/MEM 并口及同步串口   | 5512H         |
| SDA 与 SCL 直接相连    | 转换并口打印机到标准 USB 打印机 | 5584H         |

注：在不适用 I2C 功能时，务必与目标机断开 I2C 连接，否则可能影响芯片其他功能的配置。

## 2.4 I/O 电平选择

​	适配器的 USB 芯片支持 3.3V 和 5V 的工作电压，因此，适配器的输出接口 IO 信号 TTL 电平可以通过调整芯片的工作电压来切换 3.3V TTL 和 5V TTL。

### 2.4.1 3.3V I/O 电平选择

​	3.3V TTL IO 电平通过调整芯片右侧 Level Select 跳线帽位于 3.3V 一侧来实现，如下图所示：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps10.png)

### 2.4.2 5V I/O 电平选择

​	5V TTL IO 电平通过将芯片右侧 Level Select 跳线帽置于 5V 一侧来实现，如下图所示：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps11.png)

## 2.5 对外接口电源电压选择

​	适配器可以对外提供与 IO 信号电平一致的电源电压，或者与 IO 信号电平无关的 5V 电源电压，也可以不对外提供电源输出。该功能可以通过调整位于两个白色座子中间的 PWR-SEL 跳线来实现。

### 2.5.1 5V 供电电压

​	将 PWR-SEL 红色跳线帽置于 5V 侧，则适配器输出接口 VDD 的电压为5V，与芯片当前工作电压无关。配置如下图所示：

 ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps12.png) 

### 2.5.2 3.3V 供电电压

​	将 PWR-SEL 红色跳线帽置于 VCC 侧，则适配器输出接口 VDD 的电压与芯片当前工作电压保持一致。配置如下图所示：

 ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps13.png)

若要 3.3V 电源电压输出，则芯片工作电压必须设置为 3.3V。

## 2.6 指示灯

​	指示灯位于 SPI 接口两侧，在给适配器上电后，会有短暂的配置时间，待 USB 芯片完成功能配置后，不同功能指示灯会有不同的状态，由此可以判断 USB 芯片的功能配置是否成功，以及 USB 芯片的工作状态。

### 2.6.1 I2C/SPI 功能指示灯状态

​	适配器在配置为 I2C 和SPI 功能时，指示灯状态相同，红色指示灯 TNOW常亮，绿色指示灯 RDY	。

### 2.6.2 UART 功能指示灯状态

​	适配器在配置为UART 串口功能时，红色指示灯灭，绿色指示灯 RDY 亮。在串口有数据传送时 TNOW 指示灯闪烁。

# 三、上位机应用软件

## 3.1 驱动程序的安装

​	适配器的驱动程序有两个： 并口驱动和串口驱动。在使用不同功能的时候适配会自动调用合适的驱动，不会产生冲突。所以，无论用什么功能，推荐两种驱动都安装。

### 3.1.1 并口驱动程序安装

​	打开资料包，找到存放驱动的文件夹，鼠标双击 CH341PAR.EXE 开始并口

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps14.png) |

驱动的安装：

点击安装，等待几秒钟，弹出“驱动预安装成功！”窗口，点击 OK 完成安装。



![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps15.png)

### 3.1.2 串口驱动程序安装

​	打开资料包，找到存放驱动的文件夹，鼠标双击 CH341SER.EXE 开始串口驱动的安装：

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps16.png) |

点击安装，等待几秒钟，弹出“驱动预安装成功！”窗口，点击 OK 完成安装。

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps17.png) |

## 3.2 I2C 应用软件

### 3.2.1 USB2I2C 上位机软件

​	软件有两个子页面，I2C 接口和 EEPROM 读写接口，界面如下：

​	I2C 接口界面

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps18.png)

EEPROM 读写界面

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps19.png)

#### 3.2.1.1 I2C 接口

​	本软件以流模式读写兼容 I2C 的两线同步串口，调用的是驱动接口中 API USB IO_Stream I2C 函数，详细描述如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps20.png)

写入数据

长度（<400H）: 数据缓冲区中待写出的数据字节数，16 进制表示，字节数小于 400H。

数据 ： 待写入数据缓冲区， 所有数字以 16 进制表示，第一个字节为 I2C 从设备地址，例如： A0000102030405060708

A0 为从设备的 I2C 地址，00 为写入起始位置地址，后面 01~08 为依次写入的数据。

读取数据

长度（<400H）: 准备读取的数据字节数，16 进制表示，字节数小于 400H。

数据 ： 读出的数据缓冲区， 所有数字以 16 进制表示。例子：读写 24C02 EERPOM

从 00 位置开始读取从设备 A0 中的数据：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps21.png)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps22.png)

从 A0的 00 位置开始写入 01~08 数据

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps23.png) |

从 A0的 00 位置读出刚才写入的数据。



#### 3 2.1.2 EEPROM 读写

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps24.png) |

EEPROM 读写是调用驱动库中 EEPROM 专用 API 函数来实现的：

例子：从 24C02 的	址8 开始写入 16 字节数据，如下：

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps29.png) |

读出刚才写入的数据，只需填写数据单元起始地址为 8，长度为 F（十六进制），点 Read，结果如下：

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps30.png) |

本软件提供源码，位于软件目录 Resource 下，供二次开发 I2C 上位机软件参考。

### 3.2.2 USB2IIC&SPI 上位机软件（I2C 部分）

本软件主要以演示 I2C 和 SPI 功能为主，具有丰富菜单界面，存放于USB2IIC&SPI_EXE 文件夹。I2C 接口菜单如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps31.jpg) 

​	I2C 协 议 测 试 界 面 如 下 ， 软 件 调 用 的 驱 动 库 函 数 API 为USBIO_StreamI2C, 读写原理跟 USB2I2C 软件一样，只是界面不同。

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps32.png) |

​	地址下的 0x 只是数据头，表示数据格式为 16 进制，读写数据缓冲区从0 开始，双击缓冲区内位置，在状态显示框的值后面输入要写入的数据。

注意： 写入数据长度及读取数据长度为十进制格式，这点与 USB2I2C不一样。

I2C 协议通信界面如下，操作方式与协议测试页面相同。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps33.png)

本软件的详细操作例子请参考《USB2IIC&SPI 使用说明书》。

本软件提供附带 SDK 源码，位于文件夹 USB2IIC&SPI_SDK 下。

## 3.3 SPI 应用软件

SPI 工作模式参见下表：

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps34.jpg) |

适配器 SPI 接口默认工作与SPI Mode0, 时钟固定为 2MHz，时序图如下图所示：

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps35.jpg) |

### 3.3.1 USB2SPI 上位机软件

​	软件调用驱动库中 USBIO_StreamSPI4 接口库 API 函数以流模式读写兼容 SPI 的 4 线制同步串口，界面如下，

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps39.png) |

数据字节数（16 进制表示）小于 40H，写出与读入数据共用一个缓冲区。

本软件选择 CS0 作为片选信号。

本软件提供源码，位于软件目录 Resource 下，供二次开发 I2C 上位机软件参考。

|      |                                                              |
| ---- | ------------------------------------------------------------ |
|      | ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps44.png) |

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps45.png)

 

 

例子： 读写X5045

读 X5045 的状态寄存器，命令码为：05（Hex），00（Hex，实际上这个字节可以任意填充，只是为了产生必要的 SCK

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps49.png)

2 为准备读写的字节长度，0500 为准备从时钟）。MOSI 写出的数据，点击Read/Write 按钮后，得到从 MISO 返回的数据，如下图：



![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps53.png)

### 3.3.2 USB IIC&SPI 上位机软件（SPI 部分）

USB2IIC&SPI 软件 SPI 接口菜单如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps54.jpg)

SPI 协议测试界面如下，这部分调用的驱动库函数 API 为USBIO_StreamSPI4,读写原理跟 USB2SPI 软件一样，只是界面不同。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps55.png)

地址 0x 是数据头，表示数据格式为十六进制 读写数据缓冲区从 0 开始，

双击缓冲区内位置，在状态显示框的值后面输入要写入的数据。

注意： 写入数据长度及读取数据长度为十进制格式，这点与 USB2SPI不一样。

SPI 协议通信界面如下，操作方式与协议测试页面相同。

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps56.png)

本软件的详细操作例子请参考《USB2IIC&SPI 使用说明书》。

本软件提供附带 SDK 源码，位于文件夹 USB2IIC&SPI_SDK 下。

## 3.4 UART 串口软件

适配器支持单工、半双工或者全双工异步串行通讯。串行数据包括 1 个低电平起始位、 5 到 9 个数据位、 1 或 2 个高电平停止位，支持奇校验/偶校验/标志校验/空白校验。支持常用通讯波特率：50、75、100、110、134.5、150、300、600、900、1200、1800、2400、3600、4800、9600、14400、19200、28800、33600、38400、56000、57600、76800、115200、128000、153600、230400、460800、921600、1500000、2000000 等。串口发送信号的波特率误差小于 0.3％，串口接收信号的允许波特率误差不小于 2％。在计算机端的 Windows 操作系统下，适配器的驱动程序能够仿真标准串口，所以绝大部分原串口应用程序完全兼容，通常不需要作任何修改。本适配器资料包内搜集了多款常用的串口软件，一般置于 USB2UART 文件夹内。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/wps57.png)

# 四、支持与服务

| 四博智联资源                                                 |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 官网                                                         | [www.doit.am](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/http://www.doit.am/) |
| 教材                                                         | [ESPDuino智慧物联开发宝典](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/https://item.taobao.com/item.htm?spm=a1z10.3-c.w4002-7420449993.9.Bgp1Ll&id=520583000610) |
| 购买                                                         | [官方淘宝店](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/https://szdoit.taobao.com/)(szdoit.am) |
| 讨论                                                         | [技术论坛](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/http://bbs.doit.am/forum.php)(bbs.doit.am) |
| 应用案例集锦                                                 | [智能建筑云](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/http://building.doit.am)(building.doit.am) |
| [光伏监控云](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/http://solar.doit.am)(solar.doit.am) |                                                              |
| [Doit玩家云](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/http://wechat.doit.am)(wechat.doit.am) |                                                              |
| [免费TCP公网调试服务](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/MultifunctionAdapter/http://tcp.doit.am)(tcp.doit.am) |                                                              |
| 官方技术支持QQ群1/2/3群已满                                  |                                                              |
| 技术支持群4                                                  | 278888904                                                    |
| 技术支持群5                                                  | 278888905                                                    |
| 技术支持群6                                                  | 278888906                                                    |
| 技术支持群7                                                  | 278888907                                                    |
| 技术支持群8                                                  | 278888908                                                    |
| 技术支持群9                                                  | 278888909                                                    |
| 技术支持群10                                                 | 278888900                                                    |

# 五、免责申明和版权公告

本文中的信息，包括供参考的URL地址，如有变更，恕不另行通知。 

文档“按现状”提供，不负任何担保责任，包括对适销性、适用于特定用途或非侵权性的任何担保，和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任，包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可，不管是明示许可还是暗示许可。 

Wi-Fi联盟成员标志归Wi-Fi联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产，特此声明

# 六、注 意

由于产品升级或其他原因，本手册内容有可能变更。深圳四博智联科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导，深圳四博智联科技有限公司尽全力在本手册中提供准确的信息，但是并不确保手册内容完全没有错误，本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。