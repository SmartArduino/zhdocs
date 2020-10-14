<center> <font size=10> Start to Learn ESP-Series WiFi Modules </font></center>

<center> from SZDOIT </center>



# Connecting & Wiring

## Wiring

![start24](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start24.jpg)

When we get the module, we can test it according to the following wiring:

That is, VCC, EN connection 3.3v, GPIO15 GND grounding, module TX, RX connection serial port tool RX, TX, RST pin low level reset, unnecessary IO pin can be suspended, if you want to download the firmware in the module, please pull GPIO0 down processing (warm hint: if you buy ESP-01S/M/F1/F2, only need to connect VCC GND RX TX can work normally). If you buy an ESP-01 module, just connect CH-PD to VCC. Others can be connected according to the figure below (no IO port can not be connected). Please refer to the following instructions for product hardware design circuit.

![start1](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start1.jpg)

## Test

 

After completing the 1.1 connection, please check the circuit in detail and confirm that there is no problem. Open the debugging aid of serial port. The configuration mode is baud rate: 115200, data bit: 8 check bit: none stop bit: one flow control: none.

The configuration information is as follows:

To confirm that there is no problem, please press the RST reset key of K1 button (low level about 300m). Print the information as follows:

Display “read” to prove that the startup is normal.

The tools can be downloaded from the download center.

![start2](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start2.jpg)

  Frequently problems:

**Keyboard does not reflect**

(1) Please check whether the power supply of the module is 3.3V/800ma.

(2) Please check whether TX and RX are in the wrong place.

(3) Check whether the port number is selected correctly and whether the port of serial debugging assistant is closed.

**The keys are all scrambled.**

(1) Please confirm the baud rate of the module with the module manufacturer.

(2) Please check whether USB to TTL is compatible with module communication. What is recommended is a USB to TTL made of CH340 and CP2102 chips?

(3) Make sure that there is something wrong with the program in the module. (I'll talk about how to burn firmware for modules later.)

#  Examples for AT Commands

1. The following software can be downloaded by Search according to your own habits.

2. Don't confine yourself to one of these modes when testing, which is inconvenient to understand. It is suggested that all the following tests should be completely tested on one side to help understand.

3. This document is only part of AT's play. Please explore more interesting functions for yourself.

## TCP Server for Module in AP Mode

 

AT+CWMODE=2               Open AP mode (serial assistant)

AT+CWSAP= "ESP8266", "0123456789", "11,0" Set the WiFi and password of the module (serial assistant)

AT+CIPMUX=1               Open Multiple Connections (Serial Port Assistant)

AT+CIPSERVER=1,8899       Setting up Module Server Port (Serial Port Assistant)

Open the phone and start setting: Please open the computer to connect to the AP hotspot ESP8266 built by the module. And open the network debugging assistant, input the connection module's IP and the set port. The default IP of the following module is 192.168.4.1, and the port is 8899 (default 333) (network debugging assistant)

AT+CIPSEND=0,11           Enter data transmission mode for 11 bytes (serial assistant)

\> Enter Send Mode (Serial Port Assistant)

11 data sent by www.doit.am (serial assistant)

Network Debugging Assistant Sends Data: Shenzhen Sibozhi Liaison Technology Co., Ltd. (Network Debugging Assistant)

 ![start3](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start3.jpg)

![start4](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start4.jpg)

**If you want to set up boot-up and pass-through mode, please refer to the instructions in common use in the following documents. For more detailed instructions, please refer to the official AT instructions document.**

##  TCP server for WiFi module in STA mode

AT+CWMODE=1 sets the module to STA mode. (serial assistant)

AT+CWLAP Query Nearby WIFI (Serial Port Assistant)

AT+CWJAP= "123123", "12345678" connection WIFI (serial assistant)

AT + CIFSR looks at IP addresses assigned to modules by routers, such as 192.168.43.104 (serial assistant)

AT+CIPMUX=1 Open Multiple Connections (Serial Port Assistant)

AT+CIPSERVER=1,8899 Set up Module Server Port (Serial Port Assistant).

Open the network debugging assistant to set up: Please open the computer to connect the router's WIFI hotspot. And open the network debugging assistant, input the IP of the connection module and the port of the setup on the network debugging assistant. The IP allocated by router to module is 192.168.43.103, and the port is 8899 (default is 333) (network debugging assistant)

AT+CIPSEND=0,11 Enter data transmission mode for 11 bytes

\> Enter Send Mode

11 data sent by www.doit.am

Network Debugging Assistant Sends Data: Shenzhen Sibo Zhilian Technology Co., Ltd. (Network Debugging Assistant)

  ![start5](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start5.jpg)  

##  TCP Client transparent-transmission Mode

AT+CWMODE=1 sets the module to STA mode. (serial assistant)

AT+CWLAP Query Nearby WIFI (Serial Port Assistant)

AT+CWJAP= "123123", "12345678" WIFI to connect routers (serial assistant)

AT + CIFSR looks at IP addresses assigned to modules by routers, such as 192.168.43.103 (serial assistant)

AT+CIPMUX=0 Sets Single Connection (Serial Port Assistant)

AT+CIPMODE=1 Sets Pass-through Mode (Serial Port Assistant)

Network debugging assistant sets up computer connection router, opens network debugging assistant, configures TCP server port 8899, and checks IP 192.168.43.104 assigned by router to computer. (Network debugging assistant can be set up in advance.)

AT+CIPSTART= "TCP", "192.168.43.104", 8899 Connect to the TCP Server (Serial Port Assistant) established on the mobile terminal.

AT+CIPSEND starts sending data (serial assistant)

\> Enter Send Mode (Serial Port Assistant)

Www.doit.am Send Data (Serial Port Assistant)

+++ Attention should be paid to quitting the transmission and sending it directly. Cancel sending new lines

Network Debugging Assistant Sends Data: Shenzhen Sibo Zhilian Technology Co., Ltd. (Network Debugging Assistant)

![start6](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start6.jpg) 

![start7](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start7.jpg)

 Note that transmissions can only be carried out in single connection mode, so it is necessary to use (AT + CIPMUX = 0 to set up single connection) before establishing a connection, but when the module is in server mode, it must have multiple links. Because of the conflict, the module can not do TCP transmissions in open server mode!

##  UDP multi-connection mode

AT+CWMODE= 1 Sets STA Mode (Serial Port Assistant)

AT+CWLAP Query Nearby WIFI (Serial Port Assistant)

AT+CWJAP= "123123", "12345678" connect WIFI (serial assistant)

AT+CIFSR Views the current IP of the module. (serial assistant)

AT+CIPMUX=1 Open Module Multiple Connections (Serial Port Assistant)

Network Debugging Assistant: Computer connects router, opens network debugging assistant, configures UDP sending and receiving ports as follows: (network debugging assistant can be set up in advance)

AT+CIPSTART=0,'UDP','255.255.255.255','50000,1000', 0 are UDP connections, in which mobile UDP server is set to 50000 and UDP client is set to 1000 ports.

AT+CIPSEND=0,11 Module sends data in 9 bytes

\> Enter Send Data Mode

Www.doit.am Send Data

Network Debugging Assistant Sends Data: Shenzhen Sibo Zhilian Technology Co., Ltd. (Network Debugging Assistant)

Note: Multiple network debugging assistants can be used to send data to the module. Note: Local host port, target host and port number.

 ![start8](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start8.jpg)

![start9](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start9.jpg)

## UDP transparent transmission

Network Debugging Assistant: Computer Connect WIFI. View the IP address assigned by the router to the computer and set UDP ports in the network assistant.

Serial Assistant:

AT+CWMODE=1 Setting STA Mode (Serial Port Assistant)

AT+CWLAP Query Nearby WIFI (Serial Port Assistant)

AT+CWJAP= "123123", "12345678" connection WIFI (serial assistant)

AT+CIFSR View Module Current IP (Serial Port Assistant)

AT+CIPMUX=0 Setup Module Single Connection (Serial Port Assistant)

AT+CIPMODE=1 Setting Pass-through Mode (Serial Port Assistant)

AT+CIPSTART= "UDP", "192.168.43.104", "5000,2000,0" Connect IP and port of UDP (serial debugging assistant)

AT+CIPSEND Sending Data Instruction (Serial Port Assistant)

\> Enter Data Sending (Serial Port Assistant)

Www.doit.am Send Data (Serial Port Assistant)

## UDP transparent transmission between two wifi modules

Wi-Fi module is already integrated into high-speed GPIO and Peripheral interface, which may be generated the switch noise. If there is a high request for the power consumption and EMI characteristics, it is suggested to connect a serial 10~100 ohm resistance, which can suppress overshoot when switching power supply, and can smooth signal. At the same time, it also can, to a certain extent, prevent electrostatic discharge (ESD).

 Must be two serial assistants and both modules must work at the same time, remember not to power off and disconnect the serial port!

**1. Module as AP** 

AT+CWMODE=2 Sets the module to AP mode (Serial Port Assistant 1)

AT+CWSAP= "ESP8266", "12345678", "11,0" sets the hot spot of AP module (serial assistant 1).

AT+CIPMUX=0 Setup Module Single Connection (Serial Port Assistant 1)

AT+CIPMODE=1 Setting Pass-through Mode (Serial Port Assistant 1)

To set up the serial assistant of Module 2. After accepting the data, do the following.

AT+CIPSTART= "UDP", "192.168.4.2", "333,333,0" sets the IP and port to connect to UDP STA, which is the IP assigned to STA module by AP module.

AT+CIPSEND Sets Sending Instructions for Sending Data

\> 

Www.doit.am Send Data

​      ![start10](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start10.jpg)

**2. Module as STA**

AT+CWMODE=1 Setting STA Module to Compatible Mode (Serial Port Assistant II)

AT+CWLAP Search WIFI (Serial Port Assistant II)

AT+CWJAP= "ESP8266", "12345678" connection received AP hotspot (serial assistant 2) AT+CIPMUX=0) Setting up module single connection (serial assistant 2)

AT+CIPMODE=1 Setting Pass-through Mode (Serial Port Assistant II)

AT+CIPSTART= "UDP", "192.168.4.1", "333,333,0" sets the IP and port of the AP you want to connect to.

AT+CIPSEND Sends Data Instructions

![start11](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start11.jpg)
 Shenzhen Sibo Zhilian Technology Co., Ltd. Sends Data

##  TCP transparent transmission between two wifi modules

Must be two serial port assistants and both modules must work at the same time, remember not to power off and disconnect the serial port!!

**1. AP module**

AT+CWMODE=2 Sets the module to AP mode (Serial Port Assistant 1)

AT+CWSAP= "ESP8266", "12345678", "11,0" sets the hot spot of AP module (serial assistant 1).

AT+CIPMUX=1 Setting up Module Multiple Connections ((Serial Port Assistant 1))

AT+CIPSERVER=1,8899 Set up Module as TCP Server

To set up the serial assistant of Module 2. After accepting the data, do the following.

AT+CIPSEND=0,11 Sets Sending Instructions for Sending Data

![start12](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start12.jpg)
 Www.doit.am Send Data

 

 

**2. as sta module**

AT+CWMODE=1 Set the module to STA mode (Serial Assistant II) AT+CWLAP Search WIFI (Serial Assistant II)

AT+CWJAP= "ESP8266", "12345678" connect the AP hotspot received (serial assistant 2) AT+CIFSR view the assigned IP (serial assistant 2)

AT+CIPMUX=0 Setup Module Single Connection (Serial Port Assistant II)

AT+CIPMODE=1 Setting Pass-through Mode (Serial Port Assistant II)

AT+CIPSTART= "TCP", "192.168.4.1", 8899 Set the IP and port of the AP you want to connect to

​        AT+CIPSEND Sends Data Instructions

\> 

Shenzhen Sibo Zhilian Technology Co., Ltd. Sends Data

 ![start13](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start13.jpg)

# TCP transparent by internet

AT+CWMODE=3 Sets AP and STA coexistence mode

AT+CWLAP Query Nearby WIFI

AT+CWJAP= "HUAWEI-C4VTTJ", "1234567890" connection WiFi

AT+CIPMUX=0 Setting Single Connection

AT+CIPMODE=1 Setting Pass-through Mode

AT+CIPSTART= "TCP", "115.29.109.104", "6602" to connect to the external network server, please refer to the following website

AT+CIPSEND

\> 

I found a TCP network server http://tcp.doit.am on the Internet at will./

![start14](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start14.jpg)

  

# Common AT commands

1. Read IO status

AT+CIOREAD=15 is GPIO15, the return value is 0:LOW (low level) OK

2. Setting IO Port Status

AT+CIOWRITE=2,1// This instruction is DOIT internal instruction 2 is GPIO slogan, 1 is high level, 0 is low level.

3. Intelligent Distribution Network (Mobile App Distribution Network)

AT + CWSTARTSMART, to provide APP with Lexin. Download ESP-TOUCH: http://espressif.com/zh-hans/support/download/documents on the official website of Shanghai Lexin. Refer to AT instruction set for details.

4. Query chip ID

AT+CSYSID

The return values are as follows: +CSYSID: CHIP: 000FDD04; FLASH: 001640E0; KEY: DD6D800C

5. Setting baud rate

AT+UART_DEF=9600,8,1,0,0 modifies the serial port baud rate and saves it to flash. The second power-on effective module does not support hardware flow control.

6. Save TCP/UDP Pass-through Instructions

AT + SAVETRANSLINK = 1,'192.168.6.110','1002','TCP'1 boots into the transmission mode, 192.168.6.110 represents the remote ip, 1002 remote port, refer to the at instruction set for details.

7. TCP Server

AT+CIPSERVER=0 Returns OK

8. Sleep mode (normal 70 ma, maximum transmit power 500 ma) AT+SLEEP=0 is prohibited sleep mode.

1 is light-sleep mode with power consumption of 20 mA and 2 is modem-sleep mode with power consumption of 70 Ma (wif connection in sta mode can be used). Sleep mode only works in single-station mode, default is modem-sleep, refer to at instruction set for details.

9. Restore factory settings (this instruction can be used for distribution network failure)

AT+RESTORE

10. Mac of Print AP

AT+CIFSR

11. Setting up STA Mode MAC Address

AT+CIPSTAMAC="18:fe:35:98:d3:7b"

12. Wechat Distribution Network

AT+CWSMARTSTART=2

There are many more AT instructions, please refer to the official AT instructions document.

4A-ESP8266__AT Instruction Set__CN_v1.

# Built-in Firmware

Program download is based on the original wiring to lower GPIO0 for burning, it is recommended to use the latest version of download software. The power supply requires 3.3V/800MA stable power supply. If the burning error is still displayed, you can use 4.2V. Choose the following figure: This is a BIN file that has been synthesized. It is necessary to distinguish the BIN file after synthesizing from the BIN file before synthesizing. The burning method before synthesizing will be mentioned later. Following is a compiled document.

1. Documents and addresses should not be written incorrectly;

2. Pay attention to the choice of SPI and FLASH;

3. Note to check DoNotChgBin (default way to synthesize firmware burning);

4. COM port is based on COM on your computer.

5. Burning speed is recommended to use 115200, the faster the burning speed, the greater the power consumption.

6. The connection must be as short as possible and the module should be supplied independently as possible.

Be careful:

Once you have selected it, you can start burning, click start, and power up the module. Be careful not to power off the serial port. If you have not entered the download, give the reset foot several low-level pulses to see if there is any effect. If you haven't entered the download, you can try to increase the voltage by no more than 4.2V. When downloading, as long as there is no problem with the wiring, remember that the wiring should not be too long, basically no problem. It's important to pay attention to the power supply in the communication between TX and RX. More than 90% of the unsuccessful burning is a power problem.

How to choose the following figure:

 ![start15](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start15.jpg)

​     

# Environment Development

1. Installation and development environment. Refer to Installation Guidelines

2. How to import engineering for compilation

(1) Open the development environment, click the menu and select Import

​     ![start16](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start16.jpg)

(2) Open the C/C++ branch and select Existing Code as Makefile Project

![start17](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start17.jpg)

(3) Remove C++ support, select Cygwin GCC, click Browser, and select the directory where esp_iot_sdk_v1.5.2 is located. Note that there are no Chinese characters and spaces in the import path.     

​    ![start19](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start19.jpg)

 (4) Click Finish to complete the import of esp_iot_sdk_v1.5.2

![start18](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start18.jpg)

​    3. Compilation Engineering

​      Select the name of the project and click on the right button to display the menu.

 Build Project: Compile Project Clean Project: Clean Project. Remember to save the cleanup project in the compilation project first, and the console output is as follows: Note the success of the compilation: Look at Console.

  ![start20](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start20.jpg)   

4. Burn down the compiled project

Compiled two files, we need to burn four files, compiled two files should be based on the address of our successful compilation prompt, not compiled two files according to this document prompt, not compiled two files are initialization files do not burn may appear a strange phenomenon, remember

5. Burning

Click on the Combine Bin button, and the software will automatically generate a target. bin file according to the above configuration. That is the type of bin file we burned above.     

 ![start21](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start21.jpg)

 Note: Do not check DoNotChgBin when burning. Please change the SPI MODE in the figure to DOUT (here to update)

# How to write a hello word!

1. Please add them to the empty engineering group according to the above.

2. The main program entry is in app/user/user_main.c. Remember to add the header file that is. h file and call oh. See the following picture for details:

 ![start22](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start22.jpg)

#  Hardware Reference Design

Hardware design can refer to Nodemcu, part of the schematic diagram is as follows

​     ![start23](https://github.com/SmartArduino/document/raw/master/docs/ESPSeries/start/start23.jpg)

 8. Documents and Rescoureces

**I. Introduction Category**

1. Introduction Guidance of Lexin

Http://espressif.com/zh-hans/support/exploration/get-start/esp8266/get-start-guide

2. Introduction Guide of Four Wisdom Associations http://bbs.doit.am/forum.php

3. Overseas Development Guidance https://github.com/esp8266/esp8266-wiki/wiki

**II. Document Class**

Http://espressif.com/zh-hans/support/download/documents

**III. Tools**

Http://espressif.com/zh-hans/support/download/other-tools

**IV. SDK, Demo, Solids**

1. Lexin SDK Publishing Address

Http://www.espressif.com/zh-hans/support/download/sdks-demos

2. Lexin Github Code

Https://github.com/espressif

Http://www.espressif.com/zh-hans/support/iot-college/code

3. NONOS sample https://github.com/espressif/esp8266-nonos-sample-code

4. RTOS sample https://github.com/espressif/esp8266-rtos-sample-code

5. Personal Data

1. https://github.com/CHERTS/esp8266-devkit/tree/master/Espressif/examples/ESP8266

2. https://pan.baidu.com/s/1nvboYdb (with video tutorials)

3. https://github.com/Smart Arduino

4. https://github.com/Nicholas 3388/LuaNode

5. https://github.com/Smart Arduino/WiFiMCU

6. https://github.com/SmartArduino/szDOITWiKi/wiki

**V. App Class**

1. https://github.com/espressifApp

2. https://github.com/gizwits

6. Arduino Development 8266

1. Installation library https://github.com/esp8266/Arduino

2. API document http://esp8266.github.io/Arduino/versions/2.3.0/

**Development Board**

1. Node MCU official website http://nodemcu.com

2. Node MCU Document Center https://nodemcu.readthedocs.io/en/master/

3. Firmware source https://github.com/nodemcu/nodemcu-firmware

4. Nodemcu Development Board https://github.com/nodemcu/nodemcu-devkit-v1.0

5. Dashen Architecture Firmware System https://nodemcu-build.com/

6. https://github.com/Smart Arduino

**Cloud Server**

China Mobile http://open.iot.10086.cn/

2. Smart Cloud http://docs.gizwits.com/zh-cn/overview/overview.html

3. Graffiti Cloud https://docs.tuya.com/cn/

4. Ali Xiaozhi http://smart.aliyun.com

5. Jingdong Microlink https://devsmart.jd.com

6. Microsoft Hardware Platform http://iot.weixin.qq.com/

7. Shenzhiyun http://www.dtston.com/developer.php

**ESP32 Development Materials**

1. ESP32 Document Download

Http://espressif.com/zh-hans/support/download/documents

2. ESP32 Forum Community https://www.esp32.com/

3. Technical documentation http://espressif.com/zh-hans/support/download/overview

4. Arduino develops ESP32 https://github.com/espressif/arduino-esp32

Https://github.com/Smart Arduino/DOITWiKi/wiki/ESP8266--ESP32Duino

Https://github.com/espressif/openocd-esp32

 

# Q & A

Q: Which development method is suitable for beginners? Do you have a video tutorial?

A: I recommend using Arduino environment for development.

Cloud Disk Development Information: https://pan.baidu.com/s/1i5025Q9

Q: How do beginners start when they get the module?

A: Please open the cloud disk: https://pan.baidu.com/s/1i5025Q9

For more information, please check the tutorial.

Q: What's the difference between 8285 and 8266?

A: ESP8285 chip has a 1MB FLASH built into the chip of ESP8266, and is fully compatible with the package of ESP8266. The underlying protocol is fully compatible. The integration of ESP8285 chip is higher and the high temperature resistance effect is better (the conventional external FLASH in the market has a high temperature resistance of 85 C).

Q: ESP8266 Customer Question Module Selection?

A: ESP-F/F1, ESP-M1/2 and 01S are recommended for direct interpolation.

Q: What's the difference between ESP-F and ESP-12E and ESP-12F?

A: ESP-F has four PCB layers. The PCB layer of 12F is two layers, and the PCB layer of 12E is two layers. If you have certification and quality requirements, please choose ESP-F (FCC, CE, SRRC). Four-tier PCBs are more stable and can be authenticated by WiFi because of the ground layer.

Q: How about the performance of ESP series modules?

The main frequency of A: ESP series modules ranges from 80 MHz to 160MHz, and the maximum serial transmission rate is 115200*40 (4.5 Mbps). ESP8266 module can support 16 MByt external storage. ESP Series RAM is 160kb, but customers can use less than 50k. The ADC effective bits in the ESP series modules are 12 bits, but the API returns 10 bits.

Q: Which of the ESP series modules will transmit farther?

A: The transmission distance is related to the antenna. And ESP-F/M/S is about 150 meters. ESP-12F/12E is 100 meters. ESP-01/01S/07 is 70 meters (open distance test)

Q: Can ESP07 antennas be used together?

A: It can be used together, but it is not recommended. If the antenna efficiency is used together, it will be greatly reduced.

Q: What is the maximum packet length of TCP and UDP data transmission for the module?

A: The single packet length of Tcp is 1460 bytes and that of UDP is 1472 bytes.

Q. Why does a passbook lose its package?

A: Because there is no serial port flow control.


# Contact Us

- E-mails: [yichone@doit.am](mailto:yichone@doit.am), [yichoneyi@163.com](mailto:yichoneyi@163.com)
- Skype: yichone
- WhatsApp:+86-18676662425
- Wechat: 18676662425