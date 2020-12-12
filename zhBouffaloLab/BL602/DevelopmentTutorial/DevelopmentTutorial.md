<center><font size=10> 博流BL602&BL604开发板教程 </center></font>
<center> From SZDOIT</center>

## 一、开发板介绍

### 1.1.BL602/BL604芯片介绍：

BL602 / BL604是用于超低功耗应用的Wi-Fi + BLE组合芯片组。无线子系统包括2.4G无线电、Wi-Fi 802.11b/g/n和蓝牙LE5.0基带/MAC设计。微控制器子系统包含低功耗32位RISC-V CPU、高速缓存和存储器.电源管理单元控制低功耗模式.此外，还支持各种安全特性。

外围接口包括SDIO、SPI、UART、I2C、IR Remote、PWM、ADC、DAC、ACOMP、PIR等。

支持灵活的GPIO配置。BL602共有16个GPO，BL 604共有23个GPO。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps1.jpg) 

### 1.2.芯片主要特点

无线 （第1层RF性能）

· Wi-Fi 802.11 b / g / n

· 低功耗蓝牙®5.0

· 具有BLE协助的Wi-Fi快速连接

· Wi-Fi和BLE共存

· Wi-Fi安全WPS / WEP / WPA / WPA2 / WPA3

· STA，SoftAP和嗅探器模式

· 多云连接

· 2.4 GHz射频收发器

· 集成射频巴伦，PA / LNA

l周边设备

· SDIO 2.0从站（AP主机）

· SPI主/从

· 两个UART

· I2C主/从

· 五个PWM通道

· 10位通用DAC

· 12位通用ADC

· 两个通用模拟比较器

· PIR（被动红外）检测

· 红外遥控硬件加速器

· 灵活的16个GPIO（BL602）/ 23个GPIO（BL604）

l微控制器子系统

· 带FPU的32位RISC CPU

· L1快取

· RTC计时器长达一年

· 两个32b通用定时器

· 四个DMA通道

· 1MHz至192MHz的动态频率

· JTAG开发支持

· XIP QSPI闪存支持

l记忆

· 276KB SRAM

· 128KB ROM

· 1Kb电子保险丝

· 嵌入式Flash（可选）

l安全性 （完整的安全性功能）

· 安全启动

· 安全调试

· XIP QSPI即时AES解密（OTFAD）

· AES 128/192/256

· SHA-1 / 224/256

· TRNG（真随机数生成器）

· PKA（公钥加速器）

l时钟

· 支持XTAL 24/26/32 / 38.4 / 40MHz

· 支持XTAL 32 / 32.768KHz

· 内部RC 32KHz和32MHz振荡器

· 内部系统PLL

功耗模式 （超低功耗模式）

· Off

· Hibernate

· Power Down Sleep (flexible)

· Active

 

### 1.3.开发板介绍

供电

开发板可以通过 USB 接口。板上集成有 AMS1117-3.3V 稳压芯片，把输入的 5V 电压稳压到 3.3V， 用于给板上的设备和模块供电。

USB 接口

USB 接口有三种功能：

供电：只要插上 USB 线到 USB 接口即可。

下载：USB 下载会有单独的一节说明。

串口调试：串口调试在实验中有说明。

注：当使用 USB 接口进行调试或者程序下载的时候，需先按住D8键后按EN键进入下载模式。

 按键

开发板共有两个按钮，分别为D8和EN，D8为进入下载模式所需按键，同时可作为普通按键连接至GPIO8使用，EN为复位按键，当需要进入下载模式时需先按住D8然后按一下EN。

## 二. 开发环境搭建

### 2.1. 串口驱动的安装

我们的开发板使用了 CH340G 的 USB 转串口芯片。通过 USB 线把开发板接到电脑上：

接着查看电脑的设备管理器，如下图表示驱动已经正确安装，可以跳过这一节：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps2.png) 

如下图，表示要安装驱动：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps3.png) 

安装驱动步骤一:CH340 串口驱动位置：.开发软件USB-SERIAL CH340 Driver.rar，解压后如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps4.png)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps5.png) 

安装驱动步骤二:把开发板通过 USB 线接到电脑上（要打开开发板电源），提示安装驱动如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps6.png) 

安装驱动步骤三:打开电脑的设备管理器，查看串口的驱动是否已自动安装，如下图是未安装的。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps7.png) 

安装驱动步骤四:右键更新驱动，如下图：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps8.png) 

安装驱动步骤五:选择第一步解压好的目录：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps9.png) 

安装驱动步骤六:选择确定后，有可能会出现以下的提示，选择“始终安装此驱动程序软件”。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps10.png) 

安装驱动步骤七:安装完成后，设备管理器，如下图：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps11.png) 

串口驱动程序安装好之后，关于串口程序下载和调试，后面会陆续讲解。

### 2.2.编译环境搭建

 BL602&BL604的编译环境为linux环境，WIN10用户可选linux子系统进行开发

1. 准备一台Linux主机，win10用户可使用Liunx子系统

2. 打开终端，安装make，命令sudo apt-get install make国内用户可更改镜像源，加快安装速度

3. 安装git，命令sudo apt-get install git

4. 克隆仓库git clone https://github.com/SmartArduino/Doiting_BL.git

5. 修改权限，运行以下两条命令

6. chmod -R 777 ./Doiting_BL/bl_iot_sdk/toolchain/

find ./Doiting_BL/bl_iot_sdk/customer_app -name "genromap"|xargs chmod 777

GitHub下载速度较慢，可通过网盘下载完整的SDK：

链接: https://pan.baidu.com/s/123dQAG2lBEDT8VbtzN0TFQ 

提取码: d4qw

下载好SDK后，配置系统环境变量

1. 打开Linux终端，配置profile文件，命令vim ~/.profile

2. 添加环境变量，填写真实的路径export BL60X_SDK_PATH="$HOME/Doiting_BL/bl_iot_sdk"

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps12.jpg)

### 2.3.测试编译环境

以下使用hello-world为例

由于工具链以放在SDK中，故无需再下载工具链，可直接编译

进入例程目录，命令cd Doiting_BL/bl_iot_sdk/customer_app/sdk_app_helloworld/

使用项目提供的sh脚本进行编译，命令./genromap

编译完成提示：

Generating BIN File to /home/hogc/Doiting_BL/bl/bl_iot_sdk/ customer_app/sdk_app_helloworld/build_out/sdk_app_helloworld.bin

Building Finish. To flash build output.

### 2.4.程序烧录

程序编译好后，会在项目目录下生成build_out文件夹，生成的.bin文件就是我们烧录的固件。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps13.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps14.jpg) 

在SDK中已经包含烧录工具，位于....../bl_iot_sdk/tools/flash_tool。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps15.jpg) 

打开烧录工具

1.选择Partition Table, 选择partition_cfg_2M.toml

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps16.jpg) 

2.选择Boot2 Bin,选择blsp_boot2.bin

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps17.jpg) 

3. 选择Firmware Bin，根据自己编译出的固件位置选择编译好的固件

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps18.jpg) 

4．开始烧录，按住D8后按一下EN进入烧录模式，

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps19.jpg) 

 

 

注意存放固件的路径不能带有中文！

## 三.外设基础实验

### 3.1. Hello world

BL602/BL604的函数入口在main.c文件中，系统的函数入口为bfl_main(void)函数，编译成功后，烧录程序。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps20.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps21.jpg) 

 

### 3.2.GPIO控制LED灯

为了方便开发，在bfl_main(void)系统主函数中已经将一些常用的系统函数初始化，后续的开发只需要通过app_main.c文件的void user_main(void)作为函数入口即可。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps22.jpg) 

为方便调试，示例程序已通过处理使串口打印输出能输出红色和绿色两种颜色，白色部分为系统输出，LOGI(TAG, "LED :%d",value)输出为绿色，LOGE(TAG, "LED :%d",value)，输出为红色。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps23.jpg) 

编译完成后，烧录程序，将LED灯接到GPIO1，便可以看到LED灯以一秒的频率闪烁。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps24.jpg)

### 3.3.PWM呼吸灯

接着上节的GPIO实现LED闪烁效果，本节通过PWM控制来实现LED灯有暗变亮由亮变暗的呼吸效果，BL602/BL604共有五组PWM，其中GPIO与PWM对应的关系如下图：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps25.jpg) 

选用PWM1控制GPIO1来实现呼吸灯功能

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps26.jpg) 

编译完成后，烧录程序，将LED灯接到GPIO1，便可以看到LED灯的呼吸效果

### 3.4. ADC采集电压值实验

本例程用到了两个ADC相关函数

ADC初始化函数：

int hal_adc_init(int mode, int freq, int data_num, int gpio_num);

mode:高速，慢速

freq：采样频率

data_num:采样的buffer

gpio_num:gpio

ADC读取函数：

int32_t hal_adc_get_data(int gpio_num, int raw_flag);

gpio_num：gpio

raw_flag：原始数据还是转换成voltage的值

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps27.jpg) 

编译完成后，烧录程序，将GPIO12接到VCC或GND，可以看到串口输出测量的电压数值和原始数值。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps28.jpg) 

### 3.5.FLASH读写操作

BL602/BL604可以很便捷地对FLASH进行读写操作，下面以存储wifi信息为例进行FLASH读写操作，使用easyflash库可以很方便地对FLASH进行读写操作。

这里用到了FLASH读和写两个函数：

EfErrCode ef_set_env_blob(const char key, const void value_buf, size_t buf_len);

size_t ef_get_env_blob(const char key, void value_buf, size_t buf_len, size_t saved_value_len);

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps29.jpg) 

编译完成后，烧录程序，可以看到串口输出两组wifi信息，绿色打印输出的为存储到FALSH的信息，红色打印输出为从FLASH读取到的信息

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps30.jpg) 

### 3.6.定时器控制LED闪烁

本例程通过BL602的定时器实现LED灯的闪烁，Timer库相关的函数如下：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps31.jpg) 

功能实现：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps32.jpg) 

编译完成后，烧录程序，每2秒输出一个times，LED灯以2秒的频率闪烁

### 3.7.串口收发

例程在SDK目录下的...customer_appsdk_app_uart_echo,直接到SDK下的例程进行编译。



```
//串口任务
static void uart_echo_task(void arg)
{
  int length = 0, total = 0;
  uint8_t buf_recv[128];
  uint8_t pbuf = buf_recv;
  const char name = arg;
  const char send_recv_log = "1234567890abcdefg";
  int fd = aos_open(name, 0);
  log_info("%s-> fd = %drn", name, fd);
  if (fd < 0) {
​    return;
  }
  memset(buf_recv, 0, sizeof(buf_recv));
  log_step(ci_table_step_init);
  aos_write(fd, send_recv_log, strlen(send_recv_log));
  log_step(ci_table_step_send);
  vTaskDelay(1000);
  length = 0;
  while (1) {
​    length = aos_read(fd, pbuf + total, strlen(send_recv_log));
​    total += length;  
​    
​    if (total != strlen(send_recv_log)) {
​      continue;
​    }
​    if (memcmp(buf_recv, send_recv_log, strlen(send_recv_log)) == 0) {
​      printf("recvbuff:%srn", send_recv_log);
​      aos_write(fd, send_recv_log, strlen(send_recv_log));
​      log_step(ci_table_step_recv);
​      break;
​    }
​    vTaskDelay(10);
  }
  aos_close(fd);
  log_step(ci_table_step_end);

}
//创建任务

void ci_loop_proc()

{
  aos_task_new("uart_echo", uart_echo_task, "/dev/ttyS1", 2048);

}
```

 

编译完成后烧录程序，打开串口测试工具，发送数据。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps33.jpg) 

## 四.蓝牙通讯

### 4.1.蓝牙通讯

本例程通过蓝牙控制GPIO1上的LED的亮灭

系统初始化：

```
void user_main(void){

 

  bl_gpio_enable_output(LED, 0, 0);                      //初始化GPIO

  do_ble_init();                               //蓝牙初始化

  do_ble_set_reve_cb(ble_reve_cb);                      //蓝牙接收回调  

  do_ble_set_connect_cb(ble_connect_cb);                   //蓝牙连接回调

}

```

蓝牙初始化函数：

```


void do_ble_init(void){                            

  // Initialize BLE controller 

  LOGI(TAG, "do_ble_init ");

  ble_controller_init(configMAX_PRIORITIES - 1);

  //Initialize BLE Host stack

  hci_driver_init();

  bt_enable(bt_ready_cb);

  bt_set_name("BL602_BLE");                  

  bt_gatt_service_register((struct bt_gatt_service )&dis);    

  notify_attrs = &ble_attrs[1];                  

  bt_conn_cb_register(&conn_callbacks);

  ble_start_advertise();

}
```

蓝牙接收回调函数：

static void ble_reve_cb(struct bt_conn conn, const char buf, u16_t len){   //蓝牙处理函数，可在此对接收到的蓝牙数据进行处理

```


  	char ret_str[10]="";
  	LOGE(TAG, "ble_reve_buf: %s", buf);
  	if(CDM_CMP(buf,"on"))                            //当接收到“on”,拉高GPIO1点亮LED
  	{
  		bl_gpio_output_set(LED, 1);
  		strcpy(ret_str,"on");
 	 }
  	if(CDM_CMP(buf,"off"))                           //当接收到“off”,拉低GPIO1熄灭LED
  	{
 	 	bl_gpio_output_set(LED, 0);
  		 strcpy(ret_str,"off");
  	}
 	 do_ble_notify(conn, ret_str, strlen(ret_str));               //蓝牙回复状态
 	 memset(buf, 0, sizeof(buf));

}
```

蓝牙连接状态函数：

```
static void ble_connect_cb(uint8_t status, char addr){     //蓝牙连接状态回调函数

  if(status == DO_BLE_DEVICE_CONNECT){

​    LOGI(TAG, "ble_connect: %s", addr);       

​    

  }else if(status == DO_BLE_DEVICE_DISCONNECT){              

​    LOGI(TAG, "ble_disconnect: %s", addr);

​    ble_start_advertise();                       //蓝牙断开，开始广播

  }

}

 
```

打开“蓝牙调试器”APP，找到模块发射出的蓝牙，点击设置UUID

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps34.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps35.jpg) 

连接成功后发送字符“ok”便会收到模块回复一个“ok”，且LED灯会点亮，手机发送“off”,同意也会收到“off”，此时LED灯会熄灭。串口会输出接收到的蓝牙数据

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps36.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps37.png) 

## 4.2.蓝牙配网

在SDK下的路径...customer_appsdk_app_ble_sync有蓝牙配网的例程，编译例程后烧录程序，用微信扫一扫扫描此二维码，进入配网小程序。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps38.jpg) 

进入小程序后点击搜索，选择搜索到的蓝牙设备，点击获取wifi列表，选择需要连接的wifi，输入密码点击发送密码，等待连接，连接成功后能看到wifi的相关信息。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps39.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps40.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps41.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps42.jpg) 

连接成功后串口会输出wifi相关信息

## 五．WIFI通讯

### 5.1.WIFI连接

系统初始化：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps43.jpg) 

```
WIFI初始化相关函数：

//wifi初始化
void wifi_init(wifi_event_cb_t user_wifi_event_cb) {
  LOGI(TAG, "wifi init");
  cmd_stack_wifi(NULL, 0, 0, NULL);
  static_wifi_cb = user_wifi_event_cb;
void wifi_set_event_cb(void (user_wifi_cb)(input_event_t event, void private_data));
wifi_set_event_cb(event_cb_wifi_event);
}
static void cmd_stack_wifi(char buf, int len, int argc, char argv)
{
  /wifi fw stack and thread stuff/
  static uint8_t stack_wifi_init = 0;
  if (1 == stack_wifi_init) {
​    puts("Wi-Fi Stack Started already!!!rn");
​    return;
  }
  stack_wifi_init = 1;
  printf("Start Wi-Fi fw @%lumsrn", bl_timer_now_us()/1000);
  hal_wifi_start_firmware_task();
  /Trigger to start Wi-Fi/
  printf("Start Wi-Fi fw is Done @%lumsrn", bl_timer_now_us()/1000);
  aos_post_event(EV_WIFI, CODE_WIFI_ON_INIT_DONE, 0);
}
//wifi连接状态
void wifi_event_handler(wifi_event_indicate_t event){
  switch (event)
  {
​    case WIFI_EVENT_CONNECT:
​      LOGE(TAG, "wifi_connect");
​      break;
​    case WIFI_EVENT_DISCONNECT:
​      LOGE(TAG, "wifi_disconnect");
​      break;
​    default:
​      LOGE(TAG, "wifi_event: %d",event);
​      break;
  }
} 
static void event_cb_wifi_event(input_event_t event, void private_data)
{
  switch (event->code) {
​    case CODE_WIFI_ON_DISCONNECT:
​    {
​      LOGI(TAG, "wifi disconnect");
​      if(static_wifi_connect_status != 0){
​        static_wifi_connect_status = 0;
​        if(static_wifi_cb != NULL){
​          static_wifi_cb(WIFI_EVENT_DISCONNECT);
​        }
​      }
​    }
​    break;
​    case CODE_WIFI_ON_CONNECTED:
​    {
​      LOGI(TAG, "wifi connect");
​    }
​    break;
​    case CODE_WIFI_ON_GOT_IP:
​    {
​      LOGI(TAG, "wifi get ip");
​      if(static_wifi_connect_status != 1){
​        static_wifi_connect_status = 1;
​        if(static_wifi_cb != NULL){
​          static_wifi_cb(WIFI_EVENT_CONNECT);
​        }
​      }
​    }
​    break;
  }
}

 
```

Wifi连接成功后会输出连接的相关信息

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps44.jpg) 

### 5.2.TCP CLIENT

在上一节我们已经可以成功连接上WIFI，连接上WIFI后就可以进行TCP通讯，下面来看看bl602作为TCP client与TCP server的通讯。

bl_iot sdk的socket就是bsd socket，常见的linux socket编程直接可以使用。但目前暂不支持poll api。

```
//TCP任务函数
static void tcp_client_conn(void pvParameters){
  LOGI(TAG, "tcp_client_conn init");
  char re_hostbyname_cnt = 0;
  char databuff[512];
  memset(databuff, 0x00, sizeof(databuff));
  char sub_buf[200];
  memset(sub_buf, 0x00, sizeof(sub_buf));
  struct sockaddr_in server_addr;
  int client_fd = 0;
  struct hostent server_host = NULL;
  while(1){
      if (!wifi_get_connect_status())
    ​      // LOGI(TAG, "wifi disconnected!");
      vTaskDelay(1000 / portTICK_RATE_MS);
      continue;
  } 
  client_fd = socket(AF_INET, SOCK_STREAM, 0);
  if (client_fd < 0) {
      LOGI(TAG, "create socket fail: %d", client_fd);
      vTaskDelay(1000 / portTICK_RATE_MS);
      continue;
  }
  memset(&server_addr, 0, sizeof(server_addr));
  server_addr.sin_family = AF_INET;
  //修改为你的服务器端口号
  server_addr.sin_port = htons(80);
  //修改为你的连接IP地址
  uint8_t upload_srv_ip[4] = {192, 168, 9, 146}; 
  memcpy(&server_addr.sin_addr.s_addr, upload_srv_ip, 4);
  re_hostbyname_cnt = 0;
  uint8_t sip[4];
  memcpy(sip, (void )&server_addr.sin_addr.s_addr, 4);
  LOGI(TAG, "connectting server:(%d.%d.%d.%d)", sip[0], sip[1], sip[2], sip[3]);
  for (;;) {
​          //连接服务器
  if (connect(client_fd, (struct sockaddr )&server_addr, sizeof(server_addr)) < 0) 	{
      LOGE(TAG, "client connect %d", client_fd);
      LOGI(TAG, "connect failed!");
      vTaskDelay(5000 / portTICK_RATE_MS);
      close(client_fd);
      break;
  }
  LOGI(TAG, "connect success!");
  g_client_fd = client_fd;
  const struct timeval timeout = { 10, 0 }; 
  setsockopt(client_fd, SOL_SOCKET, SO_RCVTIMEO, &timeout, sizeof(timeout));
  memset(sub_buf, 0x00, sizeof(sub_buf));
​      //发送注册包
  sprintf(sub_buf, "hello");
  LOGI(TAG, "nsubscribe buff: %s", sub_buf);
  send(client_fd, sub_buf, strlen(sub_buf), 0);
  b_start_keep_alive = true;
  //处理服务器发送的消息
  while (1) {
      memset(databuff, 0x00, sizeof(databuff));
      int len = recv(client_fd, databuff, sizeof(databuff), 0);
      if (len > 0) {
     	 LOGE(TAG, "recv: %s", databuff);
      }
      if (len == 0) {
          LOGE(TAG, "close fd %d", client_fd);
          break;
      }
      if (len < 0) {
      if (errno == EAGAIN || errno == EWOULDBLOCK || errno == EINTR) {
         ;
      } else {
          LOGE(TAG, "len < 0");
          break;
  	  }
  }
  close(client_fd);
  b_start_keep_alive = false;
  break;
  } //recv
  }
  while (1)
  {
 	 vTaskDelay(10000 / portTICK_RATE_MS);
  }
}
```

 

在上节的wifi连接状态函数中添加创建TCP任务创建即可

```
// wifi连接状态
void wifi_event_handler(wifi_event_indicate_t event){
  switch (event)
  {
​    case WIFI_EVENT_CONNECT:
​      LOGE(TAG, "wifi_connect");
  //WIFI连接成功创建TCP任务
  if (!tcpc_task_handle) {
​    if (xTaskCreate(tcp_client_conn, "tcp_client_conn", TCPC_TASK_SIZE, NULL, 2, &tcpc_task_handle) != pdPASS) {
​      LOGE(TAG, "create tcp_client_conn fail");
​    }
  }
​      break;
​    case WIFI_EVENT_DISCONNECT:
​      LOGE(TAG, "wifi_disconnect");
​      break;
​    default:
​      LOGE(TAG, "wifi_event: %d",event);
​      break;
  }
}  
```

 

在例程中根据你自己的TCP服务器修改IP地址和端口号，将程序编译好完成后烧录到模块，下面用TCP测试工具进行测试。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps45.jpg) 

本例程所用到的TCP测试工具，下载地址：[http://bbs.doit.am/forum.php?mod=viewthread&tid=174&highlight=tcp![img](file:///C:UsersADMINI~1AppDataLocalTempksohtml4088wps46.jpg)](http://bbs.doit.am/forum.php?mod=viewthread&tid=174&highlight=tcp)也可以用其他TCP调试工具进行测试。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps47.jpg) 

 

按win+R打开程序搜索，输入cmd按回车打开cmd窗口，输入ipconfig查看本地的IP地址，在调试工具中创建服务器，将IP地址指定为查看到的本机IP地址。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps48.jpg) 

创建服务器后启动服务器

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps49.jpg) 

等待模块进行TCP连接，连接成功后会向服务器发送“hello”,串口会输出相关信息，同时在TCP调试工具中会出现一个新的连接，

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps50.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps51.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps52.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps53.jpg) 

### 5.3.TCP SERVER

在上一节我们成功实现了模块作为TCP client接入到TCP server实现通讯，这节我们来实现模块作为TCP server,让其他TCP client接入实现通讯。

在5.1节实现wif连接的基础上，在wifi连接成功后创建TCPserver任务。

```
void wifi_event_handler(wifi_event_indicate_t event){
  switch (event)
  {
​    case WIFI_EVENT_CONNECT:
​    LOGE(TAG, "wifi_connect");
  //WIFI连接成功创建TCP server 任务
  if (!tcpc_task_handle) {
  if (xTaskCreate(tcp_server, "tcp_server", TCPC_TASK_SIZE, NULL, 2, &tcpc_task_handle) != pdPASS) {
​      LOGE(TAG, "create tcp_server fail");
​    }
  }
​      break;
​    case WIFI_EVENT_DISCONNECT:
​      LOGE(TAG, "wifi_disconnect");
​      break;
​    default:
​      LOGE(TAG, "wifi_event: %d",event);
​      break;
  }
}  
//TCP server任务
static void tcp_server(void arg)
{
  char databuff[512];
  uint8_t recv_data;
  uint32_t sin_size;
  int sock = -1, connected, bytes_received;
  struct sockaddr_in server_addr, client_addr;
  char host = (char)arg;
  LOGE(TAG," start tcp_server ");
  recv_data = (uint8_t )pvPortMalloc(IPERF_BUFSZ);
  if (recv_data == NULL)
  {
​    LOGE(TAG,"No memory");
​    goto __exit;
  }
  (void) host;
  sock = socket(AF_INET, SOCK_STREAM, 0);
  if (sock < 0) {
​    LOGE(TAG,"Socket error");
​    goto __exit;
  }
  server_addr.sin_family = AF_INET;
  server_addr.sin_port = htons(IPERF_PORT);
  server_addr.sin_addr.s_addr = INADDR_ANY;//INADDR_ANY;
  memset(&(server_addr.sin_zero), 0x0, sizeof(server_addr.sin_zero));
  if (bind(sock, (struct sockaddr )&server_addr, sizeof(struct sockaddr)) == -1) {
​    LOGE(TAG,"Unable to bind");
​    goto __exit;
  }
  if (listen(sock, 5) == -1) {
​    LOGE(TAG,"Listen error");
​    goto __exit;
  }
  while (1) {
​    sin_size = sizeof(struct sockaddr_in);
​    connected = accept(sock, (struct sockaddr )&client_addr, (socklen_t )&sin_size);
​    LOGI(TAG,"new client connected from (%s, %d)",
​         inet_ntoa(client_addr.sin_addr),ntohs(client_addr.sin_port));
​    {
​      int flag = 1;
​      setsockopt(connected,
​        IPPROTO_TCP,   / set option at TCP level /
​        TCP_NODELAY,   / name of option /
​        (void ) &flag, / the cast is historical cruft /
​        sizeof(int));  / length of option value /
​    }
​    while (1) {
​      
​      memset(databuff, 0x00, sizeof(databuff));
​      bytes_received= recv(connected, databuff, sizeof(databuff), 0);
​      if (bytes_received <= 0) break;
​      send(connected, databuff, strlen(databuff), 0);//将接收到的消息发送回客户端
​      LOGE(TAG, "recv: %s", databuff);
​    }
​    if (connected >= 0) closesocket(connected);
​    connected = -1;
  }
__exit:
  if (sock >= 0) closesocket(sock);
  if (recv_data) vPortFree(recv_data);
  if (arg) vPortFree(arg);
}
```

编译好程序后，将固件烧录到模块后复位，观察串口输出，当连接上wifi后，用TCP测试工具建立TCP client连接。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps54.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps55.jpg) 

创建成功后点击连接，连接成功后串口会输出该连接的IP和端口

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps56.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps57.jpg) 

连接成功后进行通讯测试，在测试工具中发送的数据，设备在接收到数据后会将数据发送回客户端，同时串口会打印出数据。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps58.jpg) 

## 六．综合项目

### 6.1.Dohome智能全彩灯具

通过BL602芯片作为系统主控，实现智能全彩灯的控制，可通过wifi接入Dohome平台，同时DoHome APP已经对接了各大智能音箱（小米小爱，百度小度，阿里天猫精灵，Amazon，Google，京东叮咚）。可根据需求通过BL602模组制作智能灯具和其他相关产品。

项目地址：https://github.com/SmartArduino/Doiting_BL/tree/master/examples/bl602_Dohome_Light_RGB

在app_config.h中定义了软件的版本号，开发板产生的热点名，我们需连接通信的DoHome服务器，和我们udp,tcp通信使用的端口号，以及使用到的IO口：

```
//Log config

#define USE_UART_LOG    1

#define LOG_COLOR_ENABLE  0

#define USE_UDP_LOG     0

 

#if USE_UART_LOG

#define LOG_MIAN_EN    1

#define LOG_WIFI_EN    1

#define LOG_FLASH_EN   1

#define LOG_UTILS_EN   0

#define LOG_PROTOCOL_EN  1

#define LOG_DEVICE_EN   1

#define LOG_UDP_EN    1

#define LOG_LIGHT_EN   0

#define LOG_TCP_EN    0

#define LOG_TCP_CONFIG_EN 1

#define LOG_HTTP_EN    1

#define LOG_UPLOAD_EN   1

#define LOG_SNTP_EN    1

#define LOG_TIMER_EN   1

#define LOG_PROCES_EN   0

#define LOG_LED_DRIVE_EN 0

#define LOG_LED_BOARD_EN 0

#define LOG_OTA_EN    1

#define LOG_UDPLOG_EN   0

#define LOG_FACTORY_EN  1

#define LOG_KEY_EN    1

#define LOG_LOG_EN    1

#define LOG_IR_EN     1

#define LOG_PRODUCT_EN  1

#endif

//product config

#define IS_WYRGB

// #define IS_WY

// #define IS_STRIP

#if defined IS_STRIP

#define HARDWARE_TYPE      "_STRIPE"

#elif defined IS_WYRGB

#define DEVIVE_NAME_PREFIX   "Light_"

#define HARDWARE_TYPE      "_DT-WYRGB"

#define PIN_LED_R    27

#define PIN_LED_G    13

#define PIN_LED_B    26

#define PIN_LED_W    4

#define PIN_LED_Y    16

#elif defined IS_WY

#define HARDWARE_TYPE      "_DT-WY"

#else

#define HARDWARE_TYPE      "_LED"

#endif



  //doit config



#define FW_VERSION       "1.1.0"

#define DEF_SSID_PREFIX     "DoHome_"

#define DEF_HOSTNAME      "DoHome"

 

#define ORGANIZATION      "_DOIT"

#define CHIP_TYPE        "_ESP32"

 

#define REMOTE_SERVER_IP    "115.28.78.23"   

 

#deine REMOTE_SRV_HOST     "led_iot.doit.am"

#define REMOTE_SRV_PORT     8899//6007

 

#define UPLOAD_SRV_HOST     "dohome.doit.am"

#define UPLOAD_SRV_PORT     8008

 

#define NTP_SERVER_HOST     "xinfeng.doit.am"

#define NTP_SERVER_PORT     80

 

#define UPLOAD_SRV_URL     "http://dohome.doit.am:8008"

#define NTP_SERVER_URL     "http://xinfeng.doit.am/iot_api/get_iot_time.php"

 

#define MAX_STA_NUM       3

#define TCP_SRV_PORT      5555

 

#define SPI_FLASH_SEC_SIZE   4096

 

#define UDP_BROADCAST_INFO_PORT 6095

#define UDP_SRV_PORT      6091

 

#define WEB_SRV_PORT      80

#define DNS_SRV_PORT      53

 

#define OTA_TCP_PORT      6093

#define OTA_TCP_ECHO_PORT    6094

 

#define HTTP_UPO

#define WIFI_DEF_MAGIC     0x03

 

#define KEEPALIVE_TIME     601000

 

#define RESTART_TRIGGER_COUNT   3

 

#define EXT_UPLOAD_PERIOD      (60)    //second    

#define BASE_UPLOAD_PERIOD     (50)    //second

 

#define SYNC_TIME_PERIOD      (3060)     //second

 

#define MIN_TIMEZONE_OFFSET   0

#define MAX_TIMEZONE_OFFSET   23

 

#define TIMER_NUM        7    // you can setup at most TIMER_NUM timer

 

#define SEQ_SIZE        (16  5)

#define POWERUP_COLOR_MAX_NUM  16

#define MAX_CUSTOM_COLOR    16

 

#define OTA_PKG_SIZE      240

#define HB_SEND_MAX_COUNT    8

 

#define SSID_PASS_LEN      64

#define SSID_SSID_LEN      32

 

#define COLOR_MAX        1000

#define LIGHT_GRA_STEP     10

 

#define USE_WM_HTTP       0

#ifndef IS_STRIP_WS2812

#define USE_RTC_TIME      1

#endif

 

#define RESTART_REASON_RESET_NULL          0

#define RESTART_REASON_RESET_DEV          1

#define RESTART_REASON_REBOOT_REQ          2
```

为了稳定的配网，此方案使用ap配网，通过连接开发板产生的热点，手机app把路由器wifi名称密码发送给开发板完成配网：

```
int wifi_setup_ap(void)

{

  LOGI(TAG, "wifi_setup_ap");

  char def_ap_ssid[33] = {"BL602_AP"};

  memset(def_ap_ssid, 0x00, sizeof(def_ap_ssid));

  get_default_ssid(def_ap_ssid);

 

  wifi_interface_t wifi_interface_ap = wifi_mgmr_ap_enable();

  dhcpd_set_server_gw("192.168.4.1");

  wifi_mgmr_ap_start(wifi_interface_ap, def_ap_ssid, 0, NULL, 1);

  return 1;

}
```

连上服务器后开始发送心跳包：

```
static void vTimerCallback(TimerHandle_t timer)

{

  //服务器连接上了,开始发送心跳

  if (b_start_keep_alive) {

​    char keep_msg[256];

​    memset(keep_msg, 0x00, sizeof(keep_msg));

​    sprintf(keep_msg, "cmd=keep&device_id=%s&device_key=%srn", dev_id, dev_key);

​    send(g_client_fd, keep_msg, strlen(keep_msg), 0);

​    LOGI(TAG, "keepalive buff: %s", keep_msg);

  } else {

​    // LOGI(TAG, "tcp client disconnect=====");

  }

}
```

处理下发的数据进行设备控制：

```
//处理tcp服务下发的数据

static void parse(int socket, char buff, int len)

{

  // LOGI(TAG, "tcp_package: %s", buff);

  if (strstr(buff, "cmd=subscribe") != NULL) {

​    char pstart = strstr(buff, "res=");

​    if (pstart != NULL) {

​      pstart += strlen("res=");

​      int r = pstart - '0';

​      if (r == 1) {

​        LOGI(TAG, "register device on remote server OK");

​      } else {

​        LOGI(TAG, "register device failed!");

​      }

​    } else {

​      LOGI(TAG, "result not found!");

​    }

  } else if (strstr(buff, "cmd=publish") != NULL) {

​    char pstart = strstr(buff, "message=");

​    if (pstart != NULL) {

​      pstart += strlen("message=");

​      char ret_buf[256];

​      parse_dohome_protocol(pstart, len - (pstart - buff), ret_buf);

​    } else {

​      LOGI(TAG, "message not found!");

​    }

  } else if (strstr(buff, "cmd=keep") != NULL) {

​    LOGI(TAG, "send heartbeat OK");

  } else {

​    LOGI(TAG, "no such command");

  }

}
```

将程序编译好后烧录到芯片中，手机下载Dohome APP，添加设备，按提示进行设备的配网

APP测试

1. 扫码下载APP

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps59.jpg) 

2.进入APP点击右上角添加设备，选择彩色灯

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps60.jpg) 

2. 按APP提示进行配网操作

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps61.jpg) ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps62.png)

4.添加设备成功，能从Dohome  APP控制设备

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps63.jpg) ![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps64.png)

配网成功后，可使用app控制，也可以绑定智能音箱控制。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps65.jpg) 

绑定完智能音箱的账号后，就可以使用我们自己的智能音箱进行控制。

### 6.2. dolphin蓝牙跳蛋

通过PWM控制震动马达的转速实现不同的震动强度变化，通过蓝牙连接设备，APP下发蓝牙指令实现设备的控制。

项目地址：https://github.com/SmartArduino/Doiting_BL/tree/master/examples/dolphin

蓝牙初始化：

```
void do_ble_init(void){

  // Initialize BLE controller

  LOGI(TAG, "do_ble_init ");

  ble_controller_init(configMAX_PRIORITIES - 1);

  //Initialize BLE Host stack

  hci_driver_init();

  bt_enable(bt_ready_cb);

  bt_set_name("LVS-Lush122-XT");

  bt_gatt_service_register((struct bt_gatt_service )&dis);

  notify_attrs = &ble_attrs[1];

  bt_conn_cb_register(&conn_callbacks);

  ble_start_advertise();

}
```

蓝牙接收到的数据处理：

//蓝牙处理函数

```
static void ble_reve_cb(struct bt_conn conn, const char buf, u16_t len){  
  char cmd[30] = "";
  char data[15] = "";
  char ret_str[20] = "OK";
  //LOGI(TAG, "ble_reve_buf: %s", buf);
  //do_ble_notify(conn, ret_str, strlen(ret_str));
  char dp = strchr(buf,';');
  if(dp == NULL){
​    return;
  }else{
​    dp = '0';
  }
  LOGI(TAG, "ble_reve_buf: %s", buf);
  char p = strchr(buf,':');
  if(p != NULL){
​    strncpy(cmd, buf, p-buf);
​    strncpy(data, p+1, len-(int)(p-buf)-2);
  }else{
​    strcpy(cmd, buf);
​    cmd[len-1] = '0';
  }
  LOGI(TAG, "cmd: %s data: %s", cmd, data);
  if(CDM_CMP(cmd, "Status")){
​    LOGI(TAG, "get Status");
​    do_ble_notify(conn, ret_str, strlen(ret_str));
  }
  else if(CDM_CMP(cmd, "Vibrate")){      //蓝牙在线模式控制
​    LOGI(TAG, "set Vibrate");
​    vibrate = atoi(data);
​    Preset=0;
​    current_Preset=0;
​    //do_ble_notify(conn, ret_str, strlen(ret_str));
  }
  else if(CDM_CMP(cmd, "Preset")){      //9种预设模式选择
​    LOGI(TAG, "set Vibrate");
​    Preset = atoi(data);
  }
  else if(CDM_CMP(cmd, "Battery")){      //获取电量
​    int32_t percent=get_battery();      //电池百分比
​    if(percent==100) {ret_str[0]='1';ret_str[1]='0';ret_str[2]='0';}
​    else{
​    int8_t shiwei= percent/10; int8_t gewei= percent%10;
​    ret_str[0]='0';
​    ret_str[1]=shiwei+'0';
​    ret_str[2]=gewei+'0';
  }
​    ret_str[3]=';';
​    do_ble_notify(conn, ret_str, strlen(ret_str));//设备蓝牙回复当前电量
  }
  else if(CDM_CMP(cmd,"Light")){   //灯光闪烁开关
​    if(data[0]=='o'&&data[1]=='n'){ 
​    light_flag=true;
​    if(ble_connect) bl_gpio_output_set(LED_STATUS, 0);
​    }
​    if(data[0]=='o'&&data[1]=='f'&&data[2]=='f'){
​    light_flag=false;
​    }
  }
  else if(CDM_CMP(cmd,"PowerOff")){  //关闭设备
​    sleep_start();  
  }
  else if(CDM_CMP(cmd,"OTA")){     //蓝牙发送 OTA;  进入OTA
  LOGI(TAG, "OTA");
  ota_flag=true;
  flash_storage_init();
  wifi_init(wifi_event_handler);
  vTaskDelay(500 / portTICK_RATE_MS);
  wifi_setup_sta();
  ota_time= hal_timer_now_s();     //记录OTA开始的时间
  char ota_ret[20]="OTA_START";
  do_ble_notify(conn, ota_ret, strlen(ota_ret));
  }
  else if(CDM_CMP(cmd,"WIFI")){     //蓝牙配网指令： "WIFI:账号，密码;"
  LOGI(TAG, "SET WIFI ");
  user_ssid_t wifi_info = flash_get_user_ssid_config();
  memset(wifi_info->ssid, 0, sizeof(wifi_info->ssid));
  memset(wifi_info->password, 0, sizeof(wifi_info->password));
  flash_ssid_config_write();
  char p = strchr(data,',');
   if(p != NULL){
​    strncpy(wifi_info->ssid, data, p-data);
​    strncpy(wifi_info->password, p+1, len-(int)(p-data)-2);
​    flash_ssid_config_write();
​    char ret[20]="SET_WIFI";
​    do_ble_notify(conn, ret, strlen(ret));
​    do_ble_notify(conn, wifi_info->ssid, strlen(wifi_info->ssid));
​    do_ble_notify(conn, wifi_info->password, strlen(wifi_info->password));  
  LOGI(TAG,"saved SSID: %s, passwd: %s", wifi_info->ssid, wifi_info->password);
  }
  }
  vTaskDelay(100 / portTICK_RATE_MS);
  //do_ble_notify(conn, ret_str, strlen(ret_str));
}
void sleep_task(void arg){      //大于1200S无震动，进入休眠模式
static int times=0;
while(1){
//LOGI(TAG, "start sleep");
  if(Grade==0&&vibrate==0&&(charge_status == DISCHARGE)&&Preset==0) times++;
  else times=0;
  if(ota_flag) times =0;
  //LOGI(TAG, "times:%d",times);
  while(times>1200) {    
​    hal_hbn_init(&key_weakup_pin, 1);
​    hal_hbn_enter(0);}
  while(ota_flag&&(hal_timer_now_s()-ota_time>300)){
​    hal_hbn_init(&key_weakup_pin, 1);
​    hal_hbn_enter(0);
  }
​    vTaskDelay(1000 / portTICK_RATE_MS);
}
}
```

对蓝牙下发的指令进行解析，根据解析后的指令经行震动马达和灯光的控制：

```
void mada_task(void arg){     //mada模式

 

uint32_t duty = 0;

int i=0;

while(1){

  if(!ble_connect&&(charge_status == DISCHARGE)){            //四档离线模式

​    if(Grade==0) motor_g_set_vibrate(0);

​    if(Grade==1) motor_g_set_vibrate(8);

​    if(Grade==2) motor_g_set_vibrate(12);

​    if(Grade==3) motor_g_set_vibrate(16);
​    if(Grade==4) motor_g_set_vibrate(20);
  }
  else if(ble_connect&&(charge_status == DISCHARGE)&&Preset==0){     //蓝牙在线模式
​    motor_g_set_vibrate(vibrate);
​    if(vibrate==0)led_status_flash(0);                   
  }
  else if(ble_connect&&(charge_status == DISCHARGE)&&Preset!=0){
​    memcpy(currentPreMod,presetMod[Preset-1],8);
​    for(i=0;i<8;i++){
​    duty =currentPreMod[i]100;
​    motor_g_set_duty(duty);
​    current_Preset=currentPreMod[i];
​    if(light_flag){led_status_flash(115-current_Preset);}          //9种预设模式灯光，在此实现跟马达同时变化
​    vTaskDelay(300 / portTICK_RATE_MS);
​    LOGI(TAG, "presetMod:%d",currentPreMod[i]);
  }
  }
  else {motor_g_set_vibrate(0);Grade=0;vibrate=0;}
  vTaskDelay(100/portTICK_RATE_MS);
}
}
```

9种预设模式变化频率，可以在此调整每个模式下的震动频率变化

```
const uint8_t presetMod[9][8] =

{

​    { 100, 20, 100, 20, 100, 20, 100, 20 },   //Mod1

​    { 50, 100, 50, 100, 50, 100, 50, 100 },   //Mod2

​    { 40, 60, 80, 100, 100, 80, 60, 40 },    //Mod3

​    { 100, 25, 100, 25, 100, 25, 100, 25 },   //Mod4

​    { 75, 100, 75, 100, 75, 100, 75, 100 },   //Mod5

​    { 20, 100, 60, 100, 60, 100, 30, 60 },   //Mod6

​    { 75, 30, 20, 30, 100, 30, 25, 60 },    //Mod7

​    { 100, 100, 100, 100, 100, 100, 100, 100 }, //Mod8

​    { 38, 100, 80, 47, 28, 20, 28, 44 },    //Mod9

};
```

将程序编译好后烧录到芯片中，手机下载APP，连接设备蓝牙控制震动马达。

1.扫码下载APP

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps66.jpg) 

2.连接设备

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps67.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps68.jpg) 

3. APP控制设备，可在APP选择多种震动模式

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps69.png) 

## 6.3.AT指令

BL602/BL604模组都支持AT固件进行快速开发，AT固件的demo在SDK目录下的customer_appbl602_demo_at，本例程通过AT指令实现一些wifi和ble的一些操作。

编译完成后，在烧录前需要最烧录工具下的一个文件就修改，打开该文件，找到uart部分将两组uart所用的引脚互换，修改后保存，保存后烧录固件到模块。

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps70.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps71.jpg) 

 

复位模块，选择波特率为115200，发送AT返回OK则说明AT固件运行正常

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps72.jpg) 

 

TCP server测试

1.设置wifi模式：AT+CWMODE=1

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps73.jpg) 

2.连接wifi：AT+CWJAP=Doit,doit3305

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps74.jpg) 

3.设置自动连接: AT+CWAUTOCONN=1

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps75.jpg) 

5.建立TCP server: AT+CIPSERVER=1,80

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps76.jpg) 

6.用TCP测试工具进行通讯测试，

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps77.jpg) 

客户端的串口输出：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps78.jpg) 

 

 

 

 

TCP CLITNT测试

1.设置wifi模式：AT+CWMODE=1

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps79.jpg) 

2.连接wifi：AT+CWJAP=Doit,doit3305

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps80.jpg) 

3.设置自动连接: AT+CWAUTOCONN=1

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps81.jpg) 

4.在测试工具中新建一个TCP server

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps82.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps83.jpg) 

5.查询PC的IP地址，用于连接TCP server,进入CMD窗口，输入ipconfig

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps84.jpg) 

6.连接TCP server: AT+CIPSTART=1,TCP,192.168.9.146,80

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps85.jpg) 

 

 7.收据收发测试

服务器发送数据到模块：

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps86.jpg) 

模块发送数据到TCP server:

1.发送数据指令：AT+CIPSEND=1,11

表示即将向 id 为 1 的连接发送 11 字节的数据

2.发送需要发送的数据

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhBouffaloLab/BL602/DevelopmentTutorial/wps87.jpg) 

 

AT指令的其他开发，可根据BL602AT指令集进行开发。

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