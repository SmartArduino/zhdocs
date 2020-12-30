<center><font size=10> 4WD麦克纳姆轮小车 </center></font>
<center> From SZDOIT</center>

## 1. 简介

该小车采用铝合金底盘，具有全方位运动、速度快、载重大等特点，支持arduino、51、STM32、Raspberry pie开发板，可以使用WiFi、蓝牙、PS2手柄三种控制方式，非常适用DIY、ROS和飘移研究

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps1.jpg)

## 2. 安装说明

### 2.1 发货清单

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps2.jpg) 

### 2.2 安装电机固定支架

取出M3*8和M3螺母各16颗，按下图所示方式将 支架固定在底盘上

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps3.jpg) 

### 2.3  固定电机

取出12颗M3*8螺丝，按下图所示方式将电机固定在支架上

 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps4.jpg) 

### 2.4 安装麦克纳轮

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps5.jpg) 

注意：固定电机的螺丝方向要对准电机轴平整那面

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps6.jpg) 

### 2.5 注意要点

由于麦轮可以全方位的转动，所以要指定安装方向，具体如下图所示

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps7.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps8.jpg) 

### 2.6 安装LED灯

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps9.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps10.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps11.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps12.jpg) 

![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps13.jpg)![img](https://github.com/SmartArduino/zhdocs/raw/master/zhSmartCAR/WheatWheelCar/4WDWheatWheelCar/wps14.jpg) 

## 3. 源码

如果编译程序的时候报错显示找不到库文件，请下载对应库文件解压到Arduino IDE安装目录下的libraries文件夹下：y：https://github.com/SmartArduino/Arduino-Third-party-Libraries

### 3.1 WiFi/Bluetooth 

APP控制软件（仅支持Android手机）：https://github.com/SmartArduino/SmartArduino.github.io/blob/master/docs/Robot/Controller/app/base.apk

源程序下载：https://github.com/SmartArduino/Arduino-Code/blob/master/McNameeWheelCar.rar

特殊说明：WiFi和蓝牙共用一个程序

```
//材料：UNO+Doit电机驱动板+蓝牙模块

/****************************IO引脚定义*****************************/
//电机引脚
#define PWMD 3 //D电机转速
#define DIRD 2 //D电机转向

#define PWMC 5 //C电机转速
#define DIRC 4 //C电机转向

#define PWMB 6 //B电机转速
#define DIRB 7 //B电机转向

#define PWMA 9 //A电机转速
#define DIRA 8 //A电机转向

//控制电机运动    宏定义
// #define MOTOR_GO_FORWARD  {digitalWrite(DIRA,HIGH);analogWrite(PWMA,200);digitalWrite(DIRB,LOW);analogWrite(PWMB,200);digitalWrite(DIRC,HIGH);analogWrite(PWMC,200);digitalWrite(DIRD,LOW);analogWrite(PWMD,200);} //车体前进                             
// #define MOTOR_GO_BACK   {digitalWrite(DIRA,LOW);analogWrite(PWMA,200);digitalWrite(DIRB,HIGH);analogWrite(PWMB,200);digitalWrite(DIRC,LOW);analogWrite(PWMC,200);digitalWrite(DIRD,HIGH);analogWrite(PWMD,200);}   //车体后退
// #define MOTOR_GO_LEFT   {digitalWrite(DIRD,LOW);analogWrite(PWMD,255);digitalWrite(DIRB,LOW);analogWrite(PWMB,255);digitalWrite(DIRA,LOW);analogWrite(PWMA,255);digitalWrite(DIRC,LOW);analogWrite(PWMC,255);}  //车体左转
// #define MOTOR_GO_RIGHT    {digitalWrite(DIRA,HIGH);analogWrite(PWMA,255);digitalWrite(DIRC,HIGH);analogWrite(PWMC,255);digitalWrite(DIRD,HIGH);analogWrite(PWMD,255);digitalWrite(DIRB,HIGH);analogWrite(PWMB,255);}  //车体右转
// #define MOTOR_GO_STOP   {digitalWrite(DIRA,LOW);analogWrite(PWMA,0);digitalWrite(DIRB,LOW);analogWrite(PWMB,0);digitalWrite(DIRC,HIGH);analogWrite(PWMC,0);digitalWrite(DIRD,LOW);analogWrite(PWMD,0);}       //车体静止

//车体前进
void motor_go_forward()
{
  digitalWrite(DIRA,HIGH);
  digitalWrite(DIRB,HIGH);
  digitalWrite(DIRC,LOW);
  digitalWrite(DIRD,LOW);

  analogWrite(PWMA,255);
  analogWrite(PWMB,255);
  analogWrite(PWMC,255);
  analogWrite(PWMD,255);

}
//车体前进后退
void motor_go_back()
{
  digitalWrite(DIRA,LOW);
  digitalWrite(DIRB,LOW);
  digitalWrite(DIRC,HIGH);
  digitalWrite(DIRD,HIGH);

  analogWrite(PWMA,255);
  analogWrite(PWMB,255);
  analogWrite(PWMC,255);
  analogWrite(PWMD,255);
}
//车体左转
void motor_go_left()
{
  digitalWrite(DIRA,HIGH);
  digitalWrite(DIRB,LOW);
  digitalWrite(DIRC,LOW);
  digitalWrite(DIRD,HIGH);

  analogWrite(PWMA,255);
  analogWrite(PWMB,255);
  analogWrite(PWMC,255);
  analogWrite(PWMD,255);
}
//车体右转
void motor_go_right()
{
  digitalWrite(DIRA,LOW);
  digitalWrite(DIRB,HIGH);
  digitalWrite(DIRC,HIGH);
  digitalWrite(DIRD,LOW);

  analogWrite(PWMA,255);
  analogWrite(PWMB,255);
  analogWrite(PWMC,255);
  analogWrite(PWMD,255);
}

//车体停止
void motor_go_stop()
{
  digitalWrite(DIRA,LOW);
  digitalWrite(DIRB,LOW);
  digitalWrite(DIRC,LOW);
  digitalWrite(DIRD,LOW);

  analogWrite(PWMA,0);
  analogWrite(PWMB,0);
  analogWrite(PWMC,0);
  analogWrite(PWMD,0);
}
//车体左平移
//
void motor_pmove_left()
{
  digitalWrite(DIRA,HIGH);
  digitalWrite(DIRB,LOW);
  digitalWrite(DIRC,HIGH);
  digitalWrite(DIRD,LOW);

  analogWrite(PWMA,200);
  analogWrite(PWMB,200);
  analogWrite(PWMC,200);
  analogWrite(PWMD,200);

}
//车体右平移
void motor_pmove_right()
{
  digitalWrite(DIRA,LOW);
  digitalWrite(DIRB,HIGH);
  digitalWrite(DIRC,LOW);
  digitalWrite(DIRD,HIGH);

  analogWrite(PWMA,200);
  analogWrite(PWMB,200);
  analogWrite(PWMC,200);
  analogWrite(PWMD,200);

}

//串口接收处理
#define MAX_PACKETSIZE 32  //串口接收缓冲区
char buffUART[MAX_PACKETSIZE];
unsigned int buffUARTIndex = 0;
unsigned long preUARTTick = 0;
//小车转向
enum DN
{
  GO_ADVANCE,
  GO_LEFT,
  GO_RIGHT,
  GO_BACK,
  STOP_STOP,
  PMOVE_LEFT,//Parallel movement to the left
  PMOVE_RIGHT,//Parallel movement to the right
  DEF
} Drive_Num = DEF;

//电机控制标志量
bool flag1 = false;
bool stopFlag = true;
bool JogFlag = false;
uint16_t JogTimeCnt = 0;
uint32_t JogTime = 0;

//小车电机控制
void CAR_Control()
{
  switch (Drive_Num)
  {
  case GO_ADVANCE:motor_go_forward(); JogFlag = true; JogTimeCnt = 1; JogTime = millis(); break;
  case GO_LEFT:   motor_go_left();    JogFlag = true; JogTimeCnt = 1; JogTime = millis(); break;
  case GO_RIGHT:  motor_go_right();   JogFlag = true; JogTimeCnt = 1; JogTime = millis(); break;
  case GO_BACK:   motor_go_back();    JogFlag = true; JogTimeCnt = 1; JogTime = millis(); break;
  case STOP_STOP: motor_go_stop();    JogTime = 0; JogFlag = false; stopFlag = true; break;
  case PMOVE_LEFT:  motor_pmove_left();   JogFlag = true; JogTimeCnt = 1; JogTime = millis(); break;
  case PMOVE_RIGHT: motor_pmove_right();  JogFlag = true; JogTimeCnt = 1; JogTime = millis(); break;
  default: break;
  }
  Drive_Num = DEF;
  //小车保持姿态210ms
  if (millis() - JogTime >= 210)
  {
    JogTime = millis();
    if (JogFlag == true)
    {
      stopFlag = false;
      if (JogTimeCnt <= 0)
      {
        JogFlag = false; stopFlag = true;
      }
      JogTimeCnt--;
    }
    if (stopFlag == true)
    {
      JogTimeCnt = 0;
      motor_go_stop();
    }
  }
}
//串口数据接收处理
void UART_Control()
{
  char Uart_Date = 0;
  if (Serial.available()) //串口收到数据
  {
    Uart_Date = Serial.read();
  }
  if (buffUARTIndex > 0 && (millis() - preUARTTick >= 100)) //超过100ms没接到数据，则认为已经接收到完整指令
  { //data ready
    buffUART[buffUARTIndex] = 0x00;
    if ((buffUART[0] == 'C') && (buffUART[1] == 'M') && (buffUART[2] == 'D')) //若发送指令非法，则忽略
    {
      ;
    }
    else Uart_Date = buffUART[0];
    buffUARTIndex = 0;
  }
  switch (Uart_Date)    //串口控制指令
  {
  case '2': Drive_Num = GO_ADVANCE; break;
  case '4': Drive_Num = GO_LEFT;    break;
  case '6': Drive_Num = GO_RIGHT;   break;
  case '8': Drive_Num = GO_BACK;    break;
  case '5': Drive_Num = STOP_STOP;  break;
  case 'Y': Drive_Num = PMOVE_LEFT; break;
  case 'y': Drive_Num = PMOVE_RIGHT;break;
  default: break;
  }
}
//IO初始化
void IO_init()
{
  pinMode(DIRA, OUTPUT);
  pinMode(PWMA, OUTPUT);
  pinMode(DIRB, OUTPUT);
  pinMode(PWMB, OUTPUT);
  pinMode(DIRC, OUTPUT);
  pinMode(PWMC, OUTPUT);
  pinMode(DIRD, OUTPUT);
  pinMode(PWMD, OUTPUT);
  motor_go_stop();
}
/////////////////////////////////////////////////////////////////////////////
void setup()
{
  Serial.begin(9600);
  IO_init();
}
void loop()
{
  UART_Control();//串口接收处理
  CAR_Control();//小车控制
}
```



### 3.2 PS2手柄程序

```
#include <PS2X_lib.h>  //for v1.6

/******************************************************************
 * set pins connected to PS2 controller:
 *   - 1e column: original
 *   - 2e colmun: Stef?
 * replace pin numbers by the ones you use
 ******************************************************************/
//PS2手柄引脚；
#define PS2_DAT        13
#define PS2_CMD        11
#define PS2_SEL        10
#define PS2_CLK        12

// 电机控制引脚；
#define PWMD 3
#define DIRD 2
#define PWMC 5
#define DIRC 4
#define PWMB 6
#define DIRB 7
#define PWMA 9
#define DIRA 8


char speed = 100;    //小车速度

enum DN
{
  GO_FORWARD,
  GO_BACK,
  GO_LEFT,
  GO_RIGHT,
  GO_PLEFT,
  GO_PRIGHT,
  GO_STOP,
  DEF
}Drive_Num = DEF;

/******************************************************************
 * select modes of PS2 controller:
 *   - pressures = analog reading of push-butttons
 *   - rumble    = motor rumbling
 * uncomment 1 of the lines for each mode selection
 ******************************************************************/
// #define pressures   true
#define pressures   false
// #define rumble      true
#define rumble      false

PS2X ps2x; // create PS2 Controller Class

//right now, the library does NOT support hot pluggable controllers, meaning
//you must always either restart your Arduino after you connect the controller,
//or call config_gamepad(pins) again after connecting the controller.

int error = 0;
byte type = 0;
byte vibrate = 0;

void (* resetFunc) (void) = 0;

//初始化
void setup() {

  pinMode(PWMA, OUTPUT);
  pinMode(DIRA, OUTPUT);
  pinMode(PWMB, OUTPUT);
  pinMode(DIRB, OUTPUT);
  pinMode(PWMC, OUTPUT);
  pinMode(DIRC, OUTPUT);
  pinMode(PWMD, OUTPUT);
  pinMode(DIRD, OUTPUT);

  Serial.begin(9600);
  delay(300) ; //added delay to give wireless ps2 module some time to startup, before configuring it
  //CHANGES for v1.6 HERE!!! **************PAY ATTENTION*************

  //setup pins and settings: GamePad(clock, command, attention, data, Pressures?, Rumble?) check for error
  error = ps2x.config_gamepad(PS2_CLK, PS2_CMD, PS2_SEL, PS2_DAT, pressures, rumble);

  if (error == 0) {
    Serial.print("Found Controller, configured successful ");
    Serial.print("pressures = ");
    if (pressures)
      Serial.println("true ");
    else
      Serial.println("false");
    Serial.print("rumble = ");
    if (rumble)
      Serial.println("true)");
    else
      Serial.println("false");
    Serial.println("Try out all the buttons, X will vibrate the controller, faster as you press harder;");
    Serial.println("holding L1 or R1 will print out the analog stick values.");
    Serial.println("Note: Go to www.billporter.info for updates and to report bugs.");
  }
  else if (error == 1)
  {
    Serial.println("No controller found, check wiring, see readme.txt to enable debug. visit www.billporter.info for troubleshooting tips");
    resetFunc();
    
  }

  else if (error == 2)
    Serial.println("Controller found but not accepting commands. see readme.txt to enable debug. Visit www.billporter.info for troubleshooting tips");

  else if (error == 3)
    Serial.println("Controller refusing to enter Pressures mode, may not support it. ");

//  Serial.print(ps2x.Analog(1), HEX);

  type = ps2x.readType();
  switch (type) {
  case 0:
    Serial.print("Unknown Controller type found ");
    break;
  case 1:
    Serial.print("DualShock Controller found ");
    break;
  case 2:
    Serial.print("GuitarHero Controller found ");
    break;
  case 3:
    Serial.print("Wireless Sony DualShock Controller found ");
    break;
  }
}
//小车运动定义

void turnLeft(int speed) { //小车左转
  digitalWrite(DIRA,HIGH);
  digitalWrite(DIRB,LOW);
  digitalWrite(DIRC,LOW);
  digitalWrite(DIRD,HIGH);
  analogWrite(PWMA, speed);
  analogWrite(PWMB, speed);
  analogWrite(PWMC, speed);
  analogWrite(PWMD, speed);
}

void turnRight(int speed) { //小车右转
  digitalWrite(DIRA,LOW);
  digitalWrite(DIRB,HIGH);
  digitalWrite(DIRC,HIGH);
  digitalWrite(DIRD,LOW);
  analogWrite(PWMA, speed);
  analogWrite(PWMB, speed);
  analogWrite(PWMC, speed);
  analogWrite(PWMD, speed);
}

void forward(int speed) { //小车前进
  digitalWrite(DIRA, HIGH);
  digitalWrite(DIRB, HIGH);
  digitalWrite(DIRC, LOW);
  digitalWrite(DIRD, LOW);
  analogWrite(PWMA, speed);
  analogWrite(PWMB, speed);
  analogWrite(PWMC, speed);
  analogWrite(PWMD, speed);
}

void back(int speed) { //小车后退
  digitalWrite(DIRA, LOW);
  digitalWrite(DIRB, LOW);
  digitalWrite(DIRC, HIGH);
  digitalWrite(DIRD, HIGH);
  analogWrite(PWMA, speed);
  analogWrite(PWMB, speed);
  analogWrite(PWMC, speed);
  analogWrite(PWMD, speed);
}
void stop() // 停止；
{
  digitalWrite(DIRA, LOW);
  digitalWrite(DIRB, LOW);
  digitalWrite(DIRC, LOW);
  digitalWrite(DIRD, LOW);
  analogWrite(PWMA, 0);
  analogWrite(PWMB, 0);
  analogWrite(PWMC, 0);
  analogWrite(PWMD, 0);
}

//车体左平移
//
void motor_pmove_left(int speed)
{
  digitalWrite(DIRA,HIGH);
  digitalWrite(DIRB,LOW);
  digitalWrite(DIRC,HIGH);
  digitalWrite(DIRD,LOW);

  analogWrite(PWMA,speed);
  analogWrite(PWMB,speed);
  analogWrite(PWMC,speed);
  analogWrite(PWMD,speed);

}

//车体右平移
void motor_pmove_right(int speed)
{
  digitalWrite(DIRA,LOW);
  digitalWrite(DIRB,HIGH);
  digitalWrite(DIRC,LOW);
  digitalWrite(DIRD,HIGH);

  analogWrite(PWMA,speed);
  analogWrite(PWMB,speed);
  analogWrite(PWMC,speed);
  analogWrite(PWMD,speed);

}

void loop() 
{
  PS2();
  Control();
}

void PS2()
{
    /* You must Read Gamepad to get new values and set vibration values
    ps2x.read_gamepad(small motor on/off, larger motor strenght from 0-255)
    if you don't enable the rumble, use ps2x.read_gamepad(); with no values
    You should call this at least once a second
  */
  if (error == 1) //skip loop if no controller found
    return;

  if (type == 2) { //Guitar Hero Controller
    return;
  }
  else  { //DualShock Controller
    ps2x.read_gamepad(false, vibrate); //read controller and set large motor to spin at 'vibrate' speed

// 电机正转；
    if (ps2x.Button(PSB_PAD_UP)) {
      Serial.println("Up held this hard: ");
      Drive_Num = GO_FORWARD;
    }

// 电机反转；
    else if (ps2x.Button(PSB_PAD_DOWN)) {
      Serial.print("Down held this hard: ");
      Drive_Num = GO_BACK;
    }

//左转；
    else if (ps2x.Button(PSB_PAD_LEFT)) {
      Serial.println("turn left ");
      Drive_Num = GO_LEFT;
    }

//右转；
    else if (ps2x.Button(PSB_PAD_RIGHT)) {
      Serial.println("turn right");
      Drive_Num = GO_RIGHT;
    }

// 左平移
    else if (ps2x.Button(PSB_PINK)) {
      Serial.println("motor_pmove_left");
      Drive_Num = GO_PLEFT;
    }
// 右平移
    else if (ps2x.Button(PSB_RED)) {
      Serial.println("motor_pmove_right");
      Drive_Num = GO_PRIGHT;
    }
    // Stop
    else
    {
      Drive_Num = GO_STOP;
    }
    delay(20);

  }
  if (ps2x.Button(PSB_L1) || ps2x.Button(PSB_R1)) { //print stick values if either is TRUE
    Serial.print("Stick Values:");
    Serial.print(ps2x.Analog(PSS_LY), DEC); //Left stick, Y axis. Other options: LX, RY, RX
    Serial.print(",");
    Serial.print(ps2x.Analog(PSS_LX), DEC);
    Serial.print(",");
    Serial.print(ps2x.Analog(PSS_RY), DEC);
    Serial.print(",");
    Serial.println(ps2x.Analog(PSS_RX), DEC);

    int LY = ps2x.Analog(PSS_LY);
    int LX = ps2x.Analog(PSS_LX);
    int RY = ps2x.Analog(PSS_RY);
    int RX = ps2x.Analog(PSS_RX);

    if (LY < 127) //前进
    {

      speed = 1.5 * (127 - LY);
      forward(speed);
      delay(20);
    }
    //后退
    if (LY > 127)
    {
      speed = 1.5 * (LY - 128);
      back(speed);
      delay(20);
    }
    //左转
    if (LX < 128)
    {
      speed = 1.5 * (127 - LX);
      turnLeft(speed);
      delay(20);
    }
    //右转
    if (LX > 128)
    {
      speed = 1.5 * (LX - 128);
      turnRight(speed);
      delay(20);
    }
    //如果摇杆居中
    if (LY >= 128 && LY <= 128 && LX >= 128 && LX <= 128)
    {
      stop();
      delay(20);
    }
  }
}

void Control()
{
  switch(Drive_Num)
  {
    case GO_FORWARD: forward(speed);           break;
    case GO_BACK:    back(speed);              break;
    case GO_LEFT:    turnLeft(speed);          break;
    case GO_RIGHT:   turnRight(speed);         break;
    case GO_PLEFT:   motor_pmove_left(speed);  break;
    case GO_PRIGHT:  motor_pmove_right(speed); break;
    case GO_STOP:    stop();                   break;
    default: break;
  }
}
```

## 4. 控制说明

有关详细信息，请参阅本文：https://gitnova.com/#/Robot/Controller/4Motor16ServoControlKit/4Motor16ServoControlKit



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