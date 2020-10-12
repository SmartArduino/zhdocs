<center> <font size=10> User Manual for ESP32u </font></center>

<center> from SZDOIT </center>


# 1. Introduction

ESP-WROOM-32 module is a universal WiFi-BT-BLE MCU module with powerful functions and wide applications. It can be used in low-power sensor networks and high-demand tasks, such as voice coding, audio streaming and MP3 decoding. The core of this module is ESP32 chip, which is scalable and adaptive. Two CPU cores can be controlled or powered on separately. The adjustable range of clock frequency is from 80 MHz to 240 MHz. Users can cut off CPU power and use low-power coprocessors to continuously monitor the state changes of peripherals or whether some analog quantities exceed the threshold. ESP-WROOM-32 module also integrates a wealth of peripherals, including capacitive touch sensor, Hall sensor, low noise sensor amplifier, SD card interface, Ethernet interface, high-speed SDIO/SPI, UART, I2S and I2C. ESP-WROOM-32 module is hereinafter referred to as ESP32.

![img](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/ESP32/ESP32u/clip_image002.jpg)

ESP-32 integrates traditional Bluetooth, low-power Bluetooth and Wi-Fi, and has a wide range of applications: Wi-Fi supports a wide range of communication connections, but also supports direct Internet connection through routers; Bluetooth allows users to connect to mobile phones or broadcast BLE Beacon for signal detection. The sleep current of ESP32 chip is less than 5uA, which makes it suitable for wearable electronic devices powered by batteries. The data transmission rate supported by ESP-32 is up to 150 Mbps. After power amplifier, the output power can reach 22 dBm, which can realize the maximum range of wireless communication. Therefore, the chip has the industry's leading technical specifications, and has the best performance in high integration, wireless transmission distance, power consumption and network connectivity. ESP3 2's operating system is free RTOS with LWIP, and TLS 1.2 with hardware acceleration function is built-in. The chip also supports OTA encryption upgrades, and developers can continue to upgrade after the product is released. Software releases are included in the ESP32 bug reward program, and users can report any bugs to [bug-bounty@espressif.com](mailto:bug-bounty@espressif.com).

Users can send feedback on modules, chips, APIs and firmware to yichone@doit.am.

 

Table 1 ESP32 specifications

| Type                                                         | Item                                                         | Specifications                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------------------------- |
| Wi-Fi                                                        | standard                                                     | FCC/CE/TELEC/KCC                                            |
| protocol                                                     | 802.11 b/g/n/d/e/i/k/r (802.11n, speed 150 Mbps)             |                                                             |
| A-MPDU and A-MSDU aggregates to support 0.4us  protection interval |                                                              |                                                             |
| frequency                                                    | 2.4~2.5 GHz                                                  |                                                             |
| Bluetooth                                                    | protocol                                                     | Compliance with Bluetooth v4.2 BR/EDR and BLE  standards    |
| RF                                                           | NZIF Receiver with-98 dBm Sensitivity                        |                                                             |
| Class-1, Class-2 and Class-3 transmitter                     |                                                              |                                                             |
| AFH                                                          |                                                              |                                                             |
| audio frequency                                              | CVSD and SBC Audio frequency                                 |                                                             |
| Hardware                                                     | Interface                                                    | SD, UART, SPI, SDIO, I2C, LED PWM, motor PWM, I2S,  I2C, IR |
| GPIO, Capacitive Touch Sensor, ADC, DACLNA  Preamplifier     |                                                              |                                                             |
| On-chip sensor                                               | Hall  Sensor and Temperature Sensor                          |                                                             |
| On-board clock                                               | 26 MHz crystal oscillator and 32 kHz crystal  oscillator     |                                                             |
| working  voltage                                             | 2.2~3.6V                                                     |                                                             |
| working current                                              | Mean: 80 mA                                                  |                                                             |
| Working temperature range                                    | -40°C~+85°C [1)](http://wiki.ai-thinker.com/esp32/spec/esp32s?do=#fn__1) |                                                             |
| Ambient temperature range                                    | Normal  temperature                                          |                                                             |
| Packaging dimensions                                         | 18 mm x 20 mm x 3 mm                                         |                                                             |
| Software                                                     | Wi-Fi mode                                                   | Station/softAP/SoftAP+station/P2P                           |
| Security  mechanism                                          | WPA/WPA2/WPA2-Enterprise/WPS                                 |                                                             |
| Encryption  type                                             | AES/RSA/ECC/SHA                                              |                                                             |
| Firmware  update                                             | UART download / OTA (download and write firmware  via network / host) |                                                             |
| software  development                                        | Supporting  Cloud Server Development/SDK for User Firmware Development |                                                             |
| Network  Protocol                                            | IPv4、IPv6、SSL、TCP/UDP/HTTP/FTP/MQTT                       |                                                             |
| User  Configuration                                          | AT+Instruction  Set, Cloud Server, Android/iOS APP           |                                                             |

# 2 Pins Definition

# 2.1 Layout



![img](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/ESP32/ESP32u/clip_image004.jpg)

Figure 1 ESP32  size

 

Table 2 ESP32 size

| length | width      | heigth       | PAD(bottom)      | Distance between pins | Shield Cover Height | PCB thickness |
| ------ | ---------- | ------------ | ---------------- | --------------------- | ------------------- | ------------- |
| 18 mm  | 19.2±0.1mm | 2.8 ± 0.1 mm | 0.45 mm x 0.9 mm | 1.27 mm               | 2 mm                | 0.8 ± 0.1 mm  |

# 2.2 pins description

ESP32 has 38 pins, which are shown in Table 3.

Table3 ESP32 pins definition

| Name      | Num  | Function                                                     |      |      |
| --------- | ---- | ------------------------------------------------------------ | ---- | ---- |
| GND       | 1    | GND                                                          |      |      |
| 3V3       | 2    | power                                                        |      |      |
| EN        | 3    | Enabling  chip, high level effective.                        |      |      |
| SENSOR_VP | 4    | GPI36, SENSOR_VP, ADC_H, ADC1_CH0, RTC_GPIO0                 |      |      |
| SENSOR_VN | 5    | GPI39, SENSOR_VN, ADC1_CH3, ADC_H, RTC_GPIO3                 |      |      |
| IO34      | 6    | GPI34, ADC1_CH6, RTC_GPIO4                                   |      |      |
| IO35      | 7    | GPI35, ADC1_CH7, RTC_GPIO5                                   |      |      |
| IO32      | 8    | GPIO32, XTAL_32K_P (32.768 kHz crystal oscillator  input), ADC1_CH4, TOUCH9, RTC_GPIO9 |      |      |
| IO33      | 9    | GPIO33, XTAL_32K_N (32.768 kHz crystal oscillator  output), ADC1_CH5, TOUCH8, RTC_GPIO8 |      |      |
| IO25      | 10   | GPIO25, DAC_1, ADC2_CH8, RTC_GPIO6, EMAC_RXD0                |      |      |
| IO26      | 11   | GPIO26, DAC_2, ADC2_CH9, RTC_GPIO7, EMAC_RXD1                |      |      |
| IO27      | 12   | GPIO27, ADC2_CH7, TOUCH7, RTC_GPIO17, EMAC_RX_DV             |      |      |
| IO14      | 13   | GPIO14, ADC2_CH6, TOUCH6, RTC_GPIO16, MTMS,  HSPICLK, HS2_CLK, SD_CLK, EMAC_TXD2 |      |      |
| IO12      | 14   | GPIO12, ADC2_CH5, TOUCH5, RTC_GPIO15, MTDI,  HSPIQ, HS2_DATA2, SD_DATA2, EMAC_TXD3 |      |      |
| GND       | 15   | GND                                                          |      |      |
| IO13      | 16   | GPIO13, ADC2_CH4, TOUCH4, RTC_GPIO14, MTCK,  HSPID, HS2_DATA3, SD_DATA3, EMAC_RX_ER |      |      |
| SHD/SD2   | 17   | GPIO9, SD_DATA2, SPIHD, HS1_DATA2, U1RXD                     |      |      |
| SWP/SD3   | 18   | GPIO10, SD_DATA3, SPIWP, HS1_DATA3, U1TXD                    |      |      |
| SCS/CMD   | 19   | GPIO11, SD_CMD, SPICS0, HS1_CMD, U1RTS                       |      |      |
| SCK/CLK   | 20   | GPIO6, SD_CLK, SPICLK, HS1_CLK, U1CTS                        |      |      |
| SDO/SD0   | 21   | GPIO7, SD_DATA0, SPIQ, HS1_DATA0, U2RTS                      |      |      |
| SDI/SD1   | 22   | GPIO8, SD_DATA1, SPID, HS1_DATA1, U2CTS                      |      |      |
| IO15      | 23   | GPIO15, ADC2_CH3, TOUCH3, MTDO, HSPICS0,  RTC_GPIO13, HS2_CMD, SD_CMD, EMAC_RXD3 |      |      |
| IO2       | 24   | GPIO2, ADC2_CH2, TOUCH2, RTC_GPIO12, HSPIWP,  HS2_DATA0, SD_DATA0 |      |      |
| IO0       | 25   | GPIO0, ADC2_CH1, TOUCH1, RTC_GPIO11, CLK_OUT1,  EMAC_TX_CLK  |      |      |
| IO4       | 26   | GPIO4, ADC2_CH0, TOUCH0, RTC_GPIO10, HSPIHD,  HS2_DATA1, SD_DATA1, EMAC_TX_ER |      |      |
| IO16      | 27   | GPIO16, HS1_DATA4, U2RXD, EMAC_CLK_OUT                       |      |      |
| IO17      | 28   | GPIO17, HS1_DATA5, U2TXD, EMAC_CLK_OUT_180                   |      |      |
| IO5       | 29   | GPIO5, VSPICS0, HS1_DATA6, EMAC_RX_CLK                       |      |      |
| IO18      | 30   | GPIO18, VSPICLK, HS1_DATA7                                   |      |      |
| IO19      | 31   | GPIO19, VSPIQ, U0CTS, EMAC_TXD0                              |      |      |
| NC        | 32   | -                                                            |      |      |
| IO21      | 33   | GPIO21, VSPIHD, EMAC_TX_EN                                   |      |      |
| RXD0      | 34   | GPIO3, U0RXD, CLK_OUT2                                       |      |      |
| TXD0      | 35   | GPIO1, U0TXD, CLK_OUT3, EMAC_RXD2                            |      |      |
| IO22      | 36   | GPIO22, VSPIWP, U0RTS, EMAC_TXD1                             |      |      |
| IO23      | 37   | GPIO23, VSPID, HS1_STROBE                                    |      |      |
| GND       | 38   | GND                                                          |      |      |
|           |      |                                                              |      |      |

 

# 2.3 Strapping  pins

ESP32 has six Strapping pins. The software can read the values of these six bits in the register "GPIO_STRAPPING". During the reset process, the Strapping pin sampled the level and stored it in the latch. The latch was "0" or "1" and remained until the chip turned off or turned off.

Each Strapping pin is connected to an internal pull-up/pull-down. If a Strapping pin is not connected or the connected external line is in a high impedance state, the internal weak pull-up/pull-down will determine the default value of the input level of the Strapping pin. To change the value of Strapping bits, users can apply external pull-down/pull-up resistors or apply GPIO of host MCU to control the Strapping pin level when ESP32 is powered on and reset. After reduction, the function of Strapping pin is the same as that of common pin. Detailed startup mode for configuring Strapping pins is shown in Table 4.

Table 4 Strapping pins

| Built-in LDO  (VDD_SDIO) voltage                             |           |                                     |                                       |                                       |                                         |      |      |
| ------------------------------------------------------------ | --------- | ----------------------------------- | ------------------------------------- | ------------------------------------- | --------------------------------------- | ---- | ---- |
| PIN                                                          | default   | 3.3V                                | 1.8V                                  |                                       |                                         |      |      |
| MTDI/GPIO12                                                  | Pull down | 0                                   | 1                                     |                                       |                                         |      |      |
| System start mode                                            |           |                                     |                                       |                                       |                                         |      |      |
| pin                                                          | default   | SPI Flash start mode                | Download start mode                   |                                       |                                         |      |      |
| GPIO0                                                        | Pull-up   | 1                                   | 0                                     |                                       |                                         |      |      |
| GPIO2                                                        | Pull-down | none                                | 0                                     |                                       |                                         |      |      |
| During  system start-up, U0TXD outputs log print information |           |                                     |                                       |                                       |                                         |      |      |
| Pin                                                          | default   | U0TXD flip                          | U0TXD static                          |                                       |                                         |      |      |
| MTDO/GPIO15                                                  | Pull up   | 1                                   | 0                                     |                                       |                                         |      |      |
| SDIO Slave signal input and output timing                    |           |                                     |                                       |                                       |                                         |      |      |
| PIN                                                          | default   | Drop  edge input  Drop  Edge Output | Drop  edge input  Rising  edge output | Rising  edge input  Drop  Edge Output | Rising  edge input  Rising  edge output |      |      |
| MTDO/GPIO15                                                  | Pull up   | 0                                   | 0                                     | 1                                     | 1                                       |      |      |
| GPIO5                                                        | Pull up   | 0                                   | 1                                     | 0                                     | 1                                       |      |      |
|                                                              |           |                                     |                                       |                                       |                                         |      |      |

 

#  3 Function description

# 3.1 CPU and memory

ESP32 has two low power Xtensa < 32-bit LX6 MCUs built in. On-chip storage includes:

1. ROM of 448KBytes for program startup and kernel function call

2. 520 KBytes on-chip SRAM for data and instruction storage

3. The SRAM of 8KBytes in RTC, which is RTC slow memory, can be accessed by coprocessor in Deep-sleep mode.

4. The SRAM of 8kBytes in RTC, namely RTC fast memory, can be used for data storage and access by the main CPU when RTC starts in Deep-sleep mode.

5 and 1 kbit EFUSE, 256 bits of which are system-specific (MAC address and chip settings); the remaining 768 bits are reserved for user applications, including Flash encryption and chip ID.

# 3.2 external Flash and SRAM

ESP32 supports up to four 16 MBytes of external QSPI Flash and static random access memory (SRAM) with hardware encryption based on AES, thus protecting developers' programs and data.

ESP32 accesses external QSPI Flash and SRAM through caching. Up to 16 MBytes, Flash maps to CPU code space, supports 8-bit, 16-bit and 32-bit access, and executes code.

Up to 8 MBytes of external Flash and SRAM are mapped to the CPU data space, supporting 8-bit, 16-bit and 32-bit access. Flash only supports read operations, while SRAM supports read and write operations.

# 3.3 Crystal oscillator 

The support frequencies are 40 MHz, 26 MHz and 24 MHz. The accuracy of the crystal oscillator is between (+10 PPM) and the working temperature range is from - 40 C to 85 C.

Choose the correct crystal type when using the download tool. In the circuit design, the ground regulating capacitors C1 and C2 are added to the input and output terminals of the crystal oscillator respectively. The values of the two capacitors can be set flexibly, ranging from 6 pF to 22 pF. However, the specific capacitance value can not be determined until the overall performance of the whole circuit is matched. Generally speaking, if the frequency of crystal oscillation is 26 MHz, the capacitance value of C1 and C2 is less than 10 pF; if the frequency of crystal oscillation is 40 MHz, the capacitance value of C1 and C2 is 10 pF < C1, C2 < 22 pF.

The frequency of RTC crystal oscillator is usually 32 kHz or 32.768 kHz. Because internal calibration is used to correct the frequency offset, the frequency of crystal oscillator may exceed (+20 PPM). When the chip works in low power mode, the device should choose external low speed 32 kHz crystal clock instead of internal RC oscillator to obtain accurate wake-up time.

# 3.4 Power consumption

ESP32 has advanced power management technology and can switch between various power saving modes.

\1. Power saving mode

Active mode: The chip RF is working. The chip can receive, transmit and listen to signals.

Modem-sleep mode: The CPU keeps running and the clock can be configured. Wi-Fi/Bluetooth baseband and RF turn off.

Light-sleep mode: CPU pauses. RTC and ULP coprocessors run. Any wake-up event (MAC, host, RTC timer or external interrupt) wakes up the chip.

Deep-sleep mode: Only RTC is working. Wi-Fi and Bluetooth connection data are stored in RTC. The ULP coprocessor keeps running.

Hibernation mode: The built-in 8 MHz oscillator and ULP coprocessor are disabled. RTC memory recovery power was cut off. Only one RTC clock timer on a slow clock and some RTC GPIO are active. RTC timer or RTC GPIO can wake up the chip from Hibernation mode.

2、Sleep patterns

Associated Sleep Mode: Power-saving mode switching between Active mode and Modem-sleep mode/Light-sleep mode. CPU, Wi-Fi, Bluetooth and RF are waked up in accordance with the predetermined period to ensure Wi-Fi/Bluetooth connection.

Ultra-low power sensor monitoring mode: the main system is in Deep-sleep mode, ULP coprocessor is regularly turned on or off to measure sensor data. Based on the data measured by the sensor, the ULP coprocessor decides whether to wake up the main system. Power consumption varies with the mode of power saving/sleep mode and the working state of functional modules (see Table 5).

 

Table 5 Power consumption under different power-saving modes

| Power saving  mode                                           | Description                         | Power consuption |
| ------------------------------------------------------------ | ----------------------------------- | ---------------- |
| Active (RF)                                                  | Wi-Fi Tx packet 13 dBm~21 dBm       | 160~260 mA       |
| Wi-Fi/BT Tx packet 0 dBm                                     | 120 mA                              |                  |
| Wi-Fi/BT Rx and listening                                    | 80~90 mA                            |                  |
| Associated  Sleep Patterns (Associated with Light-sleep Patterns) | 0.9 mA@DTIM3,   1.2 mA@DTIM1        |                  |
| Modem-sleep                                                  | CPU in working state                | Max speed: 20 mA |
| Normal speed: 5~10 mA                                        |                                     |                  |
| Slow speed: 3 mA                                             |                                     |                  |
| Light-sleep                                                  | -                                   | 0.8 mA           |
| Deep-sleep                                                   | ULP coprocessor in working state    | 0.5 mA           |
| Ultra-Low Power Sensor Monitoring Mode                       | 25 uA @1 % duty                     |                  |
| RTC Timer + RTC Memory                                       | 20uA                                |                  |
| Hibernation                                                  | Only RTC timer is in working state. | 2.5 uA           |

 

# 3.5 Peripheral Interface

Table 6: Interface description

| Interface                            | Signal             | Pins      | Function                                                     |
| ------------------------------------ | ------------------ | --------- | ------------------------------------------------------------ |
| ADC                                  | ADC1_CH0           | SENSOR_VP | Two 12-bit SAR ADCs                                          |
| ADC1_CH3                             | SENSOR_VN          |           |                                                              |
| ADC1_CH4                             | IO32               |           |                                                              |
| ADC1_CH5                             | IO33               |           |                                                              |
| ADC1_CH6                             | IO34               |           |                                                              |
| ADC1_CH7                             | IO35               |           |                                                              |
| ADC2_CH0                             | IO4                |           |                                                              |
| ADC2_CH1                             | IO0                |           |                                                              |
| ADC2_CH2                             | IO2                |           |                                                              |
| ADC2_CH3                             | IO15               |           |                                                              |
| ADC2_CH4                             | IO13               |           |                                                              |
| ADC2_CH5                             | IO12               |           |                                                              |
| ADC2_CH6                             | IO14               |           |                                                              |
| ADC2_CH7                             | IO27               |           |                                                              |
| ADC2_CH8                             | IO25               |           |                                                              |
| ADC2_CH9                             | IO26               |           |                                                              |
| Ultra-low Noise Pre-analog Amplifier | SENSOR_VP          | IO36      | The  larger capacitance on the PCB provides about 60 dB gain for the ADC. |
| SENSOR_VN                            | IO39               |           |                                                              |
| DAC                                  | DAC_1              | IO25      | Two  8-bit DACs                                              |
| DAC_2                                | IO26               |           |                                                              |
| Touch  Sensor                        | TOUCH0             | IO4       | Capacitive  Touch Sensor                                     |
| TOUCH1                               | IO0                |           |                                                              |
| TOUCH2                               | IO2                |           |                                                              |
| TOUCH3                               | IO15               |           |                                                              |
| TOUCH4                               | IO13               |           |                                                              |
| TOUCH5                               | IO12               |           |                                                              |
| TOUCH6                               | IO14               |           |                                                              |
| TOUCH7                               | IO27               |           |                                                              |
| TOUCH8                               | IO33               |           |                                                              |
| TOUCH9                               | IO32               |           |                                                              |
| SDSDIO /  MMC  host controller       | HS2_CLK            | MTMS      | SD  Card Complying with V3.01 Standard                       |
| HS2_CMD                              | MTDO               |           |                                                              |
| HS2_DATA0                            | IO2                |           |                                                              |
| HS2_DATA1                            | IO4                |           |                                                              |
| HS2_DATA2                            | MTDI               |           |                                                              |
| HS2_DATA3                            | MTCK               |           |                                                              |
| Motor PWM                            | PWM0_OUT0~2        | Any GPIO  | Three  16-bit timers generate PWM waveforms.  Each  channel contains a pair of output signals.  Three  fault detection signals.  Three  even capture signals.  Three  synchronous signals. |
| PWM1_OUT_IN0~2                       |                    |           |                                                              |
| PWM0_FLT_IN0~2                       |                    |           |                                                              |
| PWM1_FLT_IN0~2                       |                    |           |                                                              |
| PWM0_CAP_IN0~2                       |                    |           |                                                              |
| PWM1_CAP_IN0~2                       |                    |           |                                                              |
| PWM0_SYNC_IN0~2                      |                    |           |                                                              |
| PWM1_SYNC_IN0~2                      |                    |           |                                                              |
| LED PWM                              | ledc_hs_sig_out0~7 | Any GPIO  | 16 separate channels running at 80 MHz clock or  RTC clock. Duty cycle accuracy: 16-bit. |
| ledc_ls_sig_out0~7                   |                    |           |                                                              |
| UART                                 | U0RXD_in           | Any GPIO  | Two  UART devices with hardware flow control and DMA         |
| U0CTS_in                             |                    |           |                                                              |
| U0DSR_in                             |                    |           |                                                              |
| U0TXD_out                            |                    |           |                                                              |
| U0RTS_out                            |                    |           |                                                              |
| U0DTR_out                            |                    |           |                                                              |
| U1RXD_in                             |                    |           |                                                              |
| U1CTS_in                             |                    |           |                                                              |
| U1TXD_out                            |                    |           |                                                              |
| U1RTS_out                            |                    |           |                                                              |
| U2RXD_in                             |                    |           |                                                              |
| U2CTS_in                             |                    |           |                                                              |
| U2TXD_out                            |                    |           |                                                              |
| U2RTS_out                            |                    |           |                                                              |
| I2C                                  | I2CEXT0_SCL_in     | Any GPIO  | Two  I2C devices working in slave or host mode               |
| I2CEXT0_SDA_in                       |                    |           |                                                              |
| I2CEXT1_SCL_in                       |                    |           |                                                              |
| I2CEXT1_SDA_in                       |                    |           |                                                              |
| I2CEXT0_SCL_out                      |                    |           |                                                              |
| I2CEXT0_SDA_out                      |                    |           |                                                              |
| I2CEXT1_SCL_out                      |                    |           |                                                              |
| I2CEXT1_SDA_out                      |                    |           |                                                              |
| I2S                                  | I2S0I_DATA_in0~15  | Any GPIO  | For  input and output of serial stereo data and output of parallel LCD data |
| I2S0O_BCK_in                         |                    |           |                                                              |
| I2S0O_WS_in                          |                    |           |                                                              |
| I2S0I_BCK_in                         |                    |           |                                                              |
| I2S0I_WS_in                          |                    |           |                                                              |
| I2S0I_H_SYNC                         |                    |           |                                                              |
| I2S0I_V_SYNC                         |                    |           |                                                              |
| I2S0I_H_ENABLE                       |                    |           |                                                              |
| I2S0O_BCK_out                        |                    |           |                                                              |
| I2S0O_WS_out                         |                    |           |                                                              |
| I2S0I_BCK_out                        |                    |           |                                                              |
| I2S0I_WS_out                         |                    |           |                                                              |
| I2S0O_DATA_out0~23                   |                    |           |                                                              |
| I2S1I_DATA_in0~15                    |                    |           |                                                              |
| I2S1O_BCK_in                         |                    |           |                                                              |
| I2S1O_WS_in                          |                    |           |                                                              |
| I2S1I_BCK_in                         |                    |           |                                                              |
| I2S1I_WS_in                          |                    |           |                                                              |
| I2S1I_H_SYNC                         |                    |           |                                                              |
| I2S1I_V_SYNC                         |                    |           |                                                              |
| I2S1I_H_ENABLE                       |                    |           |                                                              |
| I2S1O_BCK_out                        |                    |           |                                                              |
| I2S1O_WS_out                         |                    |           |                                                              |
| I2S1I_BCK_out                        |                    |           |                                                              |
| I2S1I_WS_out                         |                    |           |                                                              |
| I2S1O_DATA_out0~23                   |                    |           |                                                              |
| Infrared  remote controller          | RMT_SIG_IN0~7      | Any GPIO  | 8-channel  IR transceiver, supporting different waveform standards |
| RMT_SIG_OUT0~7                       |                    |           |                                                              |
| Parallel QSPI                        | SPIHD              | SHD/SD2   | Support Standard SPI, Dual SPI and Quad SPI,  External  Flash and SRAM can be connected |
| SPIWP                                | SWP/SD3            |           |                                                              |
| SPICS0                               | SCS/CMD            |           |                                                              |
| SPICLK                               | SCK/CLK            |           |                                                              |
| SPIQ                                 | SDO/SD0            |           |                                                              |
| SPID                                 | SDI/SD1            |           |                                                              |
| HSPICLK                              | IO14               |           |                                                              |
| HSPICS0                              | IO15               |           |                                                              |
| HSPIQ                                | IO12               |           |                                                              |
| HSPID                                | IO13               |           |                                                              |
| HSPIHD                               | IO4                |           |                                                              |
| HSPIWP                               | IO2                |           |                                                              |
| VSPICLK                              | IO18               |           |                                                              |
| VSPICS0                              | IO5                |           |                                                              |
| VSPIQ                                | IO19               |           |                                                              |
| VSPID                                | IO23               |           |                                                              |
| VSPIHD                               | IO21               |           |                                                              |
| VSPIWP                               | IO22               |           |                                                              |
| General SPI                          | HSPIQ_in/_out      | Any GPIO  | Standard  SPI includes clock, chip selection, MOSI and MISO. These SPIs can connect LCD  and other peripherals. It has the following characteristics:  (a)  Host and slave mode of operation;  (b)  Transmission in SPI format according to four modes of polarity (POL) and  phase (PHA);  (c)  Configurable CLK frequency;  (d)  FIFO and DMA of 64 Byte. |
| HSPID_in/_out                        |                    |           |                                                              |
| HSPICLK_in/_out                      |                    |           |                                                              |
| HSPI_CS0_in/_out                     |                    |           |                                                              |
| HSPI_CS1_out                         |                    |           |                                                              |
| HSPI_CS2_out                         |                    |           |                                                              |
| VSPIQ_in/_out                        |                    |           |                                                              |
| VSPID_in/_out                        |                    |           |                                                              |
| VSPICLK_in/_out                      |                    |           |                                                              |
| VSPI_CS0_in/_out                     |                    |           |                                                              |
| VSPI_CS1_out                         |                    |           |                                                              |
| VSPI_CS2_out                         |                    |           |                                                              |
| JTAG                                 | MTDI               | IO12      | JTAG  for Software Debugging                                 |
| MTCK                                 | IO13               |           |                                                              |
| MTMS                                 | IO14               |           |                                                              |
| MTDO                                 | IO15               |           |                                                              |
| SDIO slave                           | SD_CLK             | IO6       | SDIO  interface conforms to V2.0 industry standard           |
| SD_CMD                               | IO11               |           |                                                              |
| SD_DATA0                             | IO7                |           |                                                              |
| SD_DATA1                             | IO8                |           |                                                              |
| SD_DATA2                             | IO9                |           |                                                              |
| SD_DATA3                             | IO10               |           |                                                              |
| EMAC                                 | EMAC_TX_CLK        | IO0       | Ethernet  MAC with MII/RMII interface                        |
| EMAC_RX_CLK                          | IO5                |           |                                                              |
| EMAC_TX_EN                           | IO21               |           |                                                              |
| EMAC_TXD0                            | IO19               |           |                                                              |
| EMAC_TXD1                            | IO22               |           |                                                              |
| EMAC_TXD2                            | IO14               |           |                                                              |
| EMAC_TXD3                            | IO12               |           |                                                              |
| EMAC_RX_ER                           | IO13               |           |                                                              |
| EMAC_RX_DV                           | IO27               |           |                                                              |
| EMAC_RXD0                            | IO25               |           |                                                              |
| EMAC_RXD1                            | IO26               |           |                                                              |
| EMAC_RXD2                            | TXD                |           |                                                              |
| EMAC_RXD3                            | IO15               |           |                                                              |
| EMAC_CLK_OUT                         | IO16               |           |                                                              |
| EMAC_CLK_OUT_180                     | IO17               |           |                                                              |
| EMAC_TX_ER                           | IO4                |           |                                                              |
| EMAC_MDC_out                         | Any GPIO           |           |                                                              |
| EMAC_MDI_in                          | Any GPIO           |           |                                                              |
| EMAC_MDO_out                         | Any GPIO           |           |                                                              |
| EMAC_CRS_out                         | Any GPIO           |           |                                                              |
| EMAC_COL_out                         | Any GPIO           |           |                                                              |

# 4 Electrical characteristics

Note: Without special instructions, the test environment for the specifications listed in this chapter is: VBAT= 3.3V, TA= 27 degrees °C.

# 4.1 Limit parameters 

Table limit parameters

| Rating value                | Condition           | Value     | Unite |
| --------------------------- | ------------------- | --------- | ----- |
| Storage temperature         | -                   | -40~85    | °C    |
| Maximum welding temperature | -                   | 260       | °C    |
| Power supply voltage        | IPC/JEDEC J-STD-020 | +2.2-+3.6 | V     |

# 4.2 Recommended working conditions 

Table 8 Recommended working conditions

| work  environment    | Name | Min  | Classical | Max  | Unite |
| -------------------- | ---- | ---- | --------- | ---- | ----- |
| working temperature  | -    | -40  | 20        | 85   | °C    |
| Power supply voltage | VDD  | 2.2  | 3.3       | 3.6  | V     |

 

# 4.3 Digital Port Characteristics 

 

Table 9 Digital Port Characteristics

| Port                     | Name | Min     | Classical | Max     | Unite |
| ------------------------ | ---- | ------- | --------- | ------- | ----- |
| Low input logic level    | V/L  | -0.3    | -         | 0.25VDD | V     |
| High input logic level   |      | 0.75VDD | -         | VDD+0.3 | V     |
| Low  output logic level  | VOL  | N       | -         | 0.1VDD  | V     |
| High  output logic level |      | 0.8VDD  | -         | N       | V     |

 

 

# 4.4 Wi-Fi RF

Table 10 Wi-Fi RF characteristics

| Description             | Min  | Classical | Max  | Unite |
| ----------------------- | ---- | --------- | ---- | ----- |
| Universal  features     |      |           |      |       |
| Input frequency         | 2412 | -         | 2484 | MHz   |
| Input impedance         | -    | 50        | -    | Ω     |
| Input Reflection        | -    | -         | -10  | dB    |
| Output power of PA      | 15.5 | 16.5      | 21.5 | dBm   |
| Sensitivity             |      |           |      |       |
| DSSS, 1 Mbps            | -    | -98       | -    | dBm   |
| CCK, 11 Mbps            | -    | -90       | -    | dBm   |
| OFDM, 6 Mbps            | -    | -93       | -    | dBm   |
| OFDM, 54 Mbps           | -    | -75       | -    | dBm   |
| HT20, MCSO              | -    | -93       | -    | dBm   |
| HT20, MCS7              | -    | -73       | -    | dBm   |
| HT40, MCSO              | -    | -90       | -    | dBm   |
| HT40, MCS7              | -    | -70       | -    | dBm   |
| MCS32                   | -    | -91       | -    | dBm   |
| Neighborhood inhibition |      |           |      |       |
| OFDM, 6 Mbps            | -    | 37        | -    | dB    |
| OFDM, 54 Mbps           | -    | 21        | -    | dB    |
| HT20, MCS0              | -    | 37        | -    | dB    |
| HT20, MCS7              | -    | 20        | -    | dB    |

 

 

# 4.5 Low Power Bluetooth Radio Frequency

# 4.5.1 Receiver 

Table 11 BLE receiver characteristics

| Parameters                            | Condition         | Min  | Classical | Max  | Unite |
| ------------------------------------- | ----------------- | ---- | --------- | ---- | ----- |
| Sensitivity @0.1% BER                 | -                 | -    | -98       | -    | dBm   |
| Max received signal @0.1 % BER        | -                 | 0    | -         | -    | dBm   |
| Common Channel C/I                    | -                 | -    | +10       | -    | dB    |
| Neighborhood selectivity C/I          | F = F0 + 1 MHz    | -    | -5        | -    | dB    |
| F = F0 - 1 MHz                        | -                 | -5   | -         | dB   |       |
| F = F0 + 2 MHz                        | -                 | -25  | -         | dB   |       |
| F = F0 - 2 MHz                        | -                 | -35  | -         | dB   |       |
| F = F0 + 3 MHz                        | -                 | -25  | -         | dB   |       |
| F = F0 - 3 MHz                        | -                 | -45  | -         | dB   |       |
| Anti-out-of-band blocking performance | 30 MHz - 2000 MHz | -10  | -         | -    | dBm   |
| 2000 MHz - 2400 MHz                   | -27               | -    | -         | dBm  |       |
| 2500 MHz - 3000 MHz                   | -27               | -    | -         | dBm  |       |
| 3000 MHz - 12.5 GHz                   | -10               | -    | -         | dBm  |       |
| Intermodulation performance           | -                 | -36  | -         | -    | dBm   |

# 4.5.2 Transmitter

Table 12 BLE Emitter Characteristics

| Parameters                          | Condition      | Min   | Classical | Max  | Unite    |
| ----------------------------------- | -------------- | ----- | --------- | ---- | -------- |
| Radio Frequency Transmitting Power  | -              | -     | +7.5      | +10  | dBm      |
| Radio Frequency Power Control Range | -              | -     | 25        | -    | dB       |
| Neighborhood transmit power         | F = F0 + 1 MHz | -     | -14.6     | -    | dBm      |
| F = F0 - 1 MHz                      | -              | -12.7 | -         | dBm  |          |
| F = F0 + 2 MHz                      | -              | -44.3 | -         | dBm  |          |
| F = F0 - 2 MHz                      | -              | -38.7 | -         | dBm  |          |
| F = F0 + 3 MHz                      | -              | -49.2 | -         | dBm  |          |
| F = F0 - 3 MHz                      | -              | -44.7 | -         | dBm  |          |
| F = F0 + > 3 MHz                    | -              | -50   | -         | dBm  |          |
| F = F0 - > 3 MHz                    | -              | -50   | -         | dBm  |          |
| ∆f1avg                              | -              | -     | -         | 265  | kHz      |
| ∆f2max                              | -              | 247   | -         | -    | kHz      |
| ∆f2avg/∆f1avg                       | -              | -     | -0.92     | -    | -        |
| ICFT                                | -              | -     | -10       | -    | kHz      |
| Frequency drift rate                | -              | -     | 0.7       | -    | kHz/50us |
| Frequency drift                     | -              | -     | 2         | -    | kHz      |

 

# 4.6 Reflow Profile

Table 13 Temperature Curve of Reflow Welding

| Item                                                       | value                               |
| ---------------------------------------------------------- | ----------------------------------- |
| Temperature rise rate TS Max to TL                         | Max 3°C/s                           |
| Preheat                                                    |                                     |
| Minimum Temperature Value (TS Min.)                        | 150°C                               |
| Typical Temperature Value (TSTyp.)                         | 175°C                               |
| Maximum temperature (TS Max.)                              | 200°C                               |
| Time (TS)                                                  | 60-180s                             |
| Heating rate (TL to TP)                                    | Max 3°C/s                           |
| Duration: Temperature (TL)/Time (TL)                       | 217°C/60~150s                       |
| Peak Temperature (TP)                                      | Max temperature 260°C, duration 10s |
| Target Temperature Peak (TP Target Value)                  | 260°C +0/-5°C                       |
| Duration of actual peak temperature (tP) 5°C               | 20~40s                              |
| Cooling rate TS Max to TL                                  | Max 6°C/s                           |
| Time required to adjust from 25°C to peak  temperature (t) | Longest 8minutes                    |

Description: 32 kHz board crystal oscillator connects GPIO32 and GPIO33 of ESP32. In order to use the ADC, Touch or GPIO functions of IO32 and IO33, 32 kHz crystal oscillators and their capacitors C13 and C17 need to be removed, and 0 ohm resistors R5 and R6 need to be welded.

 

# 5 Schematic diagram 

![img](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/ESP32/ESP32u/clip_image006.jpg)

 

ESP32-WROOM-32U Schematic diagram

# 6 The recommended PCB design 

ESP32-WROOM-32U module can be welded directly to PCB board. For the ESP-32 version of the external antenna, due to the external antenna, the module placement requirements are not high, please adjust as appropriate. The specification of the external antenna connector is shown in the figure below.

![img](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/ESP32/ESP32u/clip_image008.jpg)

Figure 9.1 External antenna connector

 

# Appendix 1. Minimum system

![img](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/ESP32/ESP32u/clip_image010.jpg)

# Note: The power consumption of ESP-32 module is relatively large. It is recommended to supply power independently.

# Appendix 2. Automatic Burning Circuit 

Connecting EN and GPIO pins of module with DTR and RTS of serial chip can realize software control operation mode.

[![ESP32S自动烧录](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/ESP32/ESP32u/clip_image012.jpg)](http://wiki.ai-thinker.com/_detail/esp32/spec/esp32s_auto_download.png?id=esp32:spec:esp32s)

 