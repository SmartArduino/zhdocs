<center><font size=10> Flash 下载工具用户指南 </center></font>
<center> From SZDOIT</center>

## 1 准备工作

乐鑫模组在进行 flash 下载时所需的软、硬件资源如下方所示。

硬件设备：

1 x USB 串串⼝口底板

1 x 待下载设备

1 x PC（操作系统⽀支持 Windows XP、Windows 7、Windows 10）

软件设备：

下载程序：[Flash 下载工具](https://github.com/SmartArduino/zhdocs/blob/master/zhTools/flash_download_tool_v3.8.5.zip)（文件夹结构请参考 “附录 A”）

## 2 硬件介绍

### 2.1 串口底板

在本指南中，我们使用了了乐鑫 ESP_Test Board（如图所示）为 USB 转串串口底板，其核心部分为 USB 转UART 芯片。客户也可以自行购买其他 USB 转 UART 芯片或底板，用于连接模组与 PC，进⽽而将固件下载到设备。

![image-20201119111446568](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119111446568.png)

### 2.2 待下载设备

#### 2.2.1 工作模式

设备有以下两种工作模式：

• 下载模式：芯片启动时，若 IO0 为低电平，芯片会进入下载模式。

• 运行模式：芯片启动时，若 IO0 为⾼高电平，芯片会进⼊入运行模式。

#### 2.2.2. 设备连接

![image-20201119111619914](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119111619914.png)

![image-20201119111629560](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119111629560.png)

## 3 软件介绍

### 3.1 界面简介

乐鑫 Flash 下载工具的主界面如图 3-1 所示，用户可在本界面选择需要完成下载的具体设备。

![image-20201119111738369](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119111738369.png)

接着，工具将根据用户的选择，进⼊入对应设备的操作界⾯面。

![image-20201119111808336](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119111808336.png)

可以看到，工具的 “下载操作界面” 分为 5 个子界面：

• SPIDownload 界面

• HSPIDownload 界面

• RFConfig 界面

• GPIOConfig 界面

• MultiDownload 界面

### 3.2 SPIDownload 界面

#### 3.2.1 常用配置

![image-20201119111925447](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119111925447.png)

如图所示，SPIDownload 界面主要分为：
• Download Path Config

- 固件加载路路径

- 固件下载地址，以 16 进制格式填写

- MasterKey 文件夹路路径（仅当使⽤用乐鑫 IOT demo 时才使⽤用这个功能）

- MasterKey 下载地址，以 16 进制格式填写

• SPI Flash Config

- CrystalFreq：晶振频率（对于 ESP32，会忽略略这个晶振选项）

- SPI SPEED：SPI 启动速率

- SPI MODE：SPI 启动模式

对于 ESP8266，通常选择 QIO

对于 ESP8285，固定选择 DOUT

‣
对于 ESP32，根据编译选项填写，或者直接选择 DoNotChgBin
- FLASH SIZE：所使⽤用的 flash ⼤大⼩小，单位是 Mbits（在 ESP8266 下载界⾯面中的
  16Mbit-C1 和 32Mbit-C1 代表 flash 映射为 8 Mbit + 8 Mbit，反之为 4 Mbit + 4
  Mbit）

- DETECTED INFO：⾃自动检测到的 flash & 晶振信息

- 其他：将在 3.2.2 节中介绍
  • Download Panel

- START：开始按键

- STOP：停⽌止按键

- ERASE：擦除按键

- COM：下载串串⼝口

- BAUD：下载波特率

  #### 3.2.2 其他配置

  ##### 3.2.2.1 CombineBin 按键

  CombineBin 按键可将 Download Path Config 中选中的多个固件打包成一个大固件，打包后的固件包含所有选中独立固件的内容、烧录地址及 SPI Flash Config 中的配置信息。

  因此，用户在使用 CombineBin 功能前应确认每个独立固件的地址和 SPI Flash Config的配置是否准确无误。CombineBin 会将文件列列表中的文件按地址进行行拼接，文件之间空余的部分，会以 0xff 进行行填充。

  接着，完成 Combine 后打包的固件将保存为 ./combine/target.bin。

  ![image-20201119112519682](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119112519682.png)

  ##### 3.2.2.2 DoNotChgBin 选项

  如勾选该选项，SPI Flash Config 在下载过程中会将当前界面的 flash 配置信息一并烧录到 flash 中，确保固件能以客户希望的 flash size 和 flash mode运行。

  ![image-20201119112611043](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119112611043.png)

  ##### 3.2.2.3 Default 按键

  Default 按键可将 SPI 配置均还原成默认值。

  ![image-20201119112647538](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119112647538.png)

  ##### 3.2.2.4 SpiAutoSet 选项

  该选项会自动设置 SPI 下载配置。勾选后，下载过程中会根据⾃自动检测到的 flash 信息，填充 SPI 配置。

  ![image-20201119112721404](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119112721404.png)

  ##### 3.2.2.5 LOCK SETTINGS 选项

  该选项可将界面配置锁住并灰掉，主要适用于产线操作，避免产线误触导致的批量量烧录问题。使能方式：

  打开配置文件 ./configure/esp**/spi_download.conf，并将 [LOCK] 区域下的：

  lock_settings = 0

  修改为：

  lock_settings = 1

  ### 3.3 HSPIDownload 界面

  HSPIDownload 界面与 SPIDownload 完全相同，请见 3.2 节。

  ### 3.4 MultiDownload 界面

  ![image-20201119112859363](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119112859363.png)

  MultiDownload 界面与 SPIDownload 基本相同，仅需注意单独配置每一路路的串串口号和波特率即可，其他请见 3.2 节。

  ### 3.5 RFConfig 界⾯面

  本选项卡⽤用于内部调试，不不建议客户使⽤用。

  ### 3.6 GPIOConfig 界⾯面

  本功能可修改上电管脚电平，即通过修改 bootloader 中的内容，生成新的 bootloader 文件，从而实现修改上电电平的目的。

  ![image-20201119113016819](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113016819.png)

  如图 3-5 所示GPIOConfig 界面从上到下分别为 staticsBox1 管脚电平配置界面、File固件加载地址及按键栏。

  其中，按键栏共有 4 个按键：

  • SetDefault：将所有的 GPIO 都配置为 Default

  • SaveConfig：将当前的 GPIO 配置保存至配置文件中

  • LoadConfig：从配置⽂文件中加载已有 GPIO 配置

  • GeneBin：将当前的 GPIO 配置保存至已经加载的 bootloader ⽂文件中，并同时在相同路路径下保存一个新的 bootloader。

  ![image-20201119113121425](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113121425.png)

## 4 下载过程

### 4.1. ESP32 系列列下载

#### 4.1.1 外置 Flash 类 ESP32 产品的下载示例例

ESP32-WROOM-32 和 ESP32-WROVER 均属于外置 flash 的 ESP32 系列列模组，外置flash 的 ESP32 设备下载流程完全一样，这里以 ESP32-WROOM-32 为例例。

![image-20201119113303729](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113303729.png)

1. 打开下载⼯工具，进⼊入主界⾯面，点击 “ESP32 DownloadTool”，如图4-1。

![image-20201119113342505](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113342505.png)

2. 进入下载页面，填入需要烧录的 bin 文件和对应的烧录地址，并根据自己实际需求填入CrystalFreq、SPI SPEED、SPI MODE、FLASH SIZE、COM 及 BAUD，如图 4-2。

![image-20201119113442740](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113442740.png)

3. 点击 START 开始下载。下载过程中，下载工具会读取 flash 的信息和芯片的 MAC 地址，如图 4-3。

![image-20201119113523972](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113523972.png)

4. 下载完成后，下载工具的界面如图 4-4 所示。

![image-20201119113605611](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113605611.png)

5. 打开串串口工具，产品重新上电，检查上电 log。正确的上电 log 如图 4-5 所示：

![image-20201119113638883](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113638883.png)

#### 4.1.2 内置 Flash 类 ESP32 产品的下载示例例

ESP32-PICO-D4 和 ESP32-D2WD 均属于内置 flash 的 ESP32 系列列模组。内置 flash 的ESP32 的下载流程完全一样，这里以 ESP32-D2WD 为例例。

1. 打开下载⼯工具，进⼊入主界⾯面，点击 “ESP32D2WD DownloadTool”，如图 4-6

![image-20201119113729370](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119113729370.png)

2. 后续操作步骤与外置 flash 类 ESP32 产品完全⼀一致，请见 4.1.1 节。

#### 4.1.3 开启加密功能固件烧录

1. 配置加密功能，记事本打开配置文件 ./configure/esp32/security.conf，其中相关配置项的说明如下（True：使能，False：不使能）：

   • [DEBUG MODE]
   此模式下，可指定密钥文件路路径，使所有烧录产品均使用同一密钥

- debug_enable = False（是否使能 debug 模式）
- debug_pem_path =（密钥文件路路径）

• [SECURE BOOT]
   此配置项为开启 secure boot 时需要配置

- secure_boot_en = False（是否使能 secure boot）
- burn_secure_boot_key = False（是否烧录 secure boot 的密钥⽂文件）
- secure_boot_force_write = False（是否强制烧写 secure boot 的密钥⽂文件）
- secure_boot_rw_protect = False（烧写密钥文件后是否使能读写保护）

• [FLASH ENCRYPTION]

此配置项为开启 flash 加密时需要配置

- flash_encryption_en = False（是否开启 flash 加密功能）

- burn_flash_encryption_key = False（是否烧录 flash 加密的密钥文件）

- flash_encrypt_force_write = False（是否强制烧写 flash 加密的密钥文件）

- flash_encrypt_rw_protect = False（烧录 flash 加密密钥文件后，是否使能读写保护）

- reserved_burn_times = 0（是否预留留烧录次数）

典型配置如下：

![image-20201119114134084](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114134084.png)

2. 烧录过程

  • 运行行工具时会提示如下内容，需核对是否正确。

![image-20201119114225979](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114225979.png)

• 点击 START 按钮，开始烧录。烧录过程分两个阶段，首先进行行加密过程，加密过程时间较⻓长，耐心等待。加密完成后即进入烧录流程。

![image-20201119114528918](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114528918.png)

• 固件烧录完成后，会向芯片的 efuse 中烧录 key 等信息。待固件及 efuse 烧录完成后，显示 “FINISH /完成”。如下图所示。

![image-20201119114558343](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114558343.png)

### 4.2 ESP8266 系列列下载

#### 4.2.1 ESP-WROOM-02 下载示例例

1. 打开下载工具，选择“ESP8266 DownloadTool”，如图 4-7 所示。

![image-20201119114645199](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114645199.png)

2. 填入需要烧录的 bin 文件和对应的烧录地址，并根据自己实际需求填入 CrystalFreq、SPI SPEED、SPI MODE、FLASH SIZE、COM 和 BAUD。

![image-20201119114725856](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114725856.png)

![image-20201119114736901](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114736901.png)

3. 确认设备处在下载模式（打开串串口助⼿手，上电能看到 “ets Jan 8 2013,rst cause:1,boot mode:(1,2)” 字样）。
4. 断开与其他软件的串串口连接（否则会烧录失败）。
5. 在 Download Path Config 中勾选需要下载的固件。
6. 根据 3.1 节中的说明，在 SpiFlashConfig 中选择合适的参数。
7. 选择下载的 COM 口和 BAUD。
8. 点击 START 按键开始下载。
9. 下载过程中，下载⼯工具会读取 flash 的信息和芯⽚片的 MAC 地址，如图 4-9 所示。

![image-20201119114847847](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114847847.png)

10. 下载完成后，下载工具的界面如图 4-10 所示。

![image-20201119114919326](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114919326.png)

11. 打开串串口工具，产品重新上电，检查上电 log。正确的上电 log 如图 4-11 所示（乱码是由于上电波特率为 74880，而 AT 命令接收的波特率为 115200）：

![image-20201119114953868](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119114953868.png)

#### 4.2.2 ESP-WROOM-S2 下载示例例

ESP-WROOM-S2 下载与 ESP-WROOM-02 接近，区别在于以下几点：

• 上电之前需将 IO15 接地。

• 打开电源后，悬空 IO15，并保持电源开启状态。

• 下载模组时，选用 HSPI 下载，CrystalFreq 选择 26 M 晶振，SPI MODE 根据实际情况选择 QIO 或 DIO 模式，如图 4-12 所示。

![image-20201119115044800](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115044800.png)

![image-20201119115057897](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115057897.png)

### 4.3 ESP8266 系列列下载

1. 打开下载工具，选择 “ESP8285 DownloadTool”，如图 4-13 所示：

![image-20201119115142667](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115142667.png)

![image-20201119115152570](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115152570.png)

2. 后续操作步骤与 ESP-WROOM-02 完全一致，请见 4.2.1 节。

## 5 常见错误

### 5.1 COM 相关错误

1. 打开工具后，在 COM 下拉菜单中找不不到对应串串口？
答：首先查看设备管理器，确认串口已经安装成功。若没有成功，检查驱动是否有问题。
2. “连接串口失败”，如下图所示：

![image-20201119115315618](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115315618.png)

### 5.2 同步相关错误

1. ⼯工具⼀一直停留留在下图界⾯面，该怎么解决？

![image-20201119115344033](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115344033.png)

答：⼯工具停留留在同步过程中可能有以下⼏几种原因。
- 硬件原因：

  ‣ 串串⼝口底板没有接跳帽

  ‣ 设备没有处于下载模式，确认方式请⻅见第 3 章
  
  ‣ 所选⽤用的 flash 型号不不⽀支持
  
- 软件原因：

  ‣待下载的设备选择错误

### 5.3 Efuse 相关错误

1. 点击 START 后出现下图问题，是什什么原因？

![image-20201119115534591](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115534591.png)

答：若下载命令⾏行行框中出现 “ESP8266 Chip efuse check error esp_check_mac_and_efuse”，代表设备的 efuse 出现错误，可能有以下原因：
- 设备的 efuse 没有问题，待下载设备选择有误。此时，请重新选择待下载设备。
- 设备的 efuse 确有错误。此时，请联系乐鑫获取 esptool.exe 以及操作指令，并将efuse 读出后交由乐鑫进⾏行行调试。

### 5.4. 下载相关错误

1. 下载过程出现错误，什什么原因？
答：出现下载问题，请⾸首先确认：
- 设备的 TX/RX 没有与其他软件复⽤用

- 设备实际的 flash 不不⼩小于固件的⼤大⼩小

- 若出现 MD5 校验错误，请⾸首先擦除整⽚片 flash，然后尝试再次下载

 ### 5.5 运行行相关错误
1. 固件下载完成后，重新上电 crash。
答：请⾸首先确认烧录的固件本身没有问题，⽽而后确认以下方面：
- 待下载设备的选择是否正确
- Flash 启动模式的配置是否正确
- Flash 下载模式的选择是否正确

## A. 附录 – 下载程序文件夹结构

乐鑫 Flash 下载⼯工具（ESP8266 & ESP32）为 zip 压缩⽂文件包，内含可执⾏行行⽂文件、相关库文件及一些子文件夹，如下图所示：

![image-20201119115827975](https://github.com/SmartArduino/zhdocs/raw/master/zhESPSeries/Flash_DownloadTool/image-20201119115827975.png)

• configure 文件夹：存放下载配置⽂文件

• dl_temp 文件夹：存放下载暂存的 bin 文件

• init_data 文件夹：存放 RF 初始参数

• RESOURCE 文件夹：存放工具图像文件

• secure 文件夹：存放开启加密配置时，下载中产生的中间文件

• flash_download_tool.exe：下载工具可执行文件

**如非要求，请勿更更改任何文件夹内的文件。**

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