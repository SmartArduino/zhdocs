<center><font size=10> W800 Iperf测试工具使用指导 </center></font>
<center> From SZDOIT</center>

## 1 引言

### 1.1 编写目的

介绍 Iperf 测试工具在联盛德芯片上的使用发法，帮助使用者测试芯片的网络性能。

### 1.2 预期读者

相关开发人员和测试人员。

## 2 Iperf 工具简介

Iperf 是一个网络性能测试工具，Iperf 可以测试最大 TCP 和 UDP 带宽性能，可以报告带宽、延迟抖动和数据包丢失。固件中已经集成了 Iperf 测试功能，同时也提供了 PC 端的 Iperf 程序，两者可以配合进行测试。

### 2.1 使用方法

#### 2.1.1 固件中 Iperf 功能启用方法

默认的固件中是不包含 Iperf 测试功能的，如果需要使用固件的 Iperf 功能，需要使用者修改SDK\Src\App\iperf\iperf.h 中的 TLS_CONFIG_WIFI_PERF_TEST 宏，将其改为 CFG_ON，这时候重新编译生成的固件就具有了 Iperf 功能。

#### 2.1.2 固件中 Iperf 功能操作方法

目前固件中只提供使用 AT 指令进行控制 Iperf 操作，可用的 AT 指令如下：

AT+THT=<Ss>[,-i=interval]

AT+THT=<Cc,ip,UDP,-b=bandwidth,-t=time,-i=interval>

AT+THT=<Cc,ip,TCP,-l=blocksize,-t=time,-i=interval>

其参数代表的含义如下：

Ss：一个大写的 S 或者小写的 s 即可，表示作为 Server 端使用；

Cc：一个大写的 C 或者小写的 c 即可，表示作为 Client 端使用；

interval：信息打印频率，十进制表示，单位秒；

ip：服务端 ip 地址，点分十进制格式；

bandwidth：udp 测试带宽值，十进制表示，其单位可用设置如下：

![image-20201114135007345](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_Iperf/image-20201114135007345.png)

time：测试持续的总时长，十进制表示，单位秒；

blocksize：tcp分块大小，十进制表示，单位字节；

#### 2.1.3 PC 端 Iperf 工具操作方法

PC 端提供的 Iperf 测试工具为“wm_perf.exe”，可以通过使用“wm_perf.exe -h”得到其所有的用法：

![image-20201114135046869](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_Iperf/image-20201114135046869.png)

### 2.2 使用示例

#### 2.2.1 模块做 Server 测试

给模块发送指令“AT+THT=s,-i=1”即可，这时会有如下显示：

![image-20201114135123954](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_Iperf/image-20201114135123954.png)

#### 2.2.2 模块做 UDP 测试

如 果 用 作 Server 的 IP 地 址 为 192.168.19.102 ， 那 么 给 模 块 发 送 指 令“AT+THT=c,192.168.19.102,UDP,-b=5M,-t=10,-i=1”即可，这时会有如下显示：

![image-20201114135156276](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_Iperf/image-20201114135156276.png)

#### 2.2.3 模块做 TCP Client 测试

如 果 用 作 Server 的 IP 地 址 为 192.168.19.102 ， 给 模 块 发 送 指 令“AT+THT=c,192.168.19.102,TCP,-l=1024,-t=10,-i=1”即可，这时会有如下显示：

![image-20201114135227531](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_Iperf/image-20201114135227531.png)

#### 2.2.4 PC 端做 Server 测试

在 PC 端执行“wm_perf -s -i 1”即可，这时会有如下显示：

![image-20201114135247897](https://github.com/SmartArduino/zhdocs/raw/master/zhW_Series/W800/Docs/SDK_Develop/W800_Iperf/image-20201114135247897.png)

#### 2.2.5 PC 端做 TCP Client 测试

在 PC 端执行“wm_perf -c 192.168.19.102 -l 1024 -t 10 -i 1”即可。

#### 2.2.6 PC 端做 UDP 测试

在 PC 端执行“wm_perf -c 192.168.19.102 -u -b 5M -t 10 -i 1”即可。

## 3 注意事项

### 3.1 物理环境

理想的测试环境是在屏蔽室中进行测试，但是在实际测试中不同的使用环境会测得不同的结果，因为 WiFi 会受当前所在信道情况的影响比较大，如果当前信道比较忙且干扰毕竟严重，那么测试出来的网络性能就会比较低。

测试时所用的设备影响也会比较大，如 PC 使用网线连接路由器，那么会比 PC 也用无线连接路由器要好。测试所用的是笔记本电脑的话，尤其要注意使用电源给笔记本电脑供电，避免电池供电状态下的笔记本电脑无线网卡会使用节能而降低网络性能。

### 3.2 模块配置

通常情况下 CPU 频率越高，系统的吞吐率会越高，性能会越好。

### 3.3 PC 端防火墙

有些系统带有防火墙会造成 iperf 测试失败，这种情况下需要添加放行规则或者关闭防火墙。

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