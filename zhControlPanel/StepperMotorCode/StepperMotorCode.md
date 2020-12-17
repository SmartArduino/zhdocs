<center><font size=10> 4步进电机控制程序 </center></font>
<center> From SZDOIT</center>

## 1 控制板

![wps1](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/StepperMotorCode/wps1.jpg)

这款板子的详细资料，请查阅：https://gitnova.com/#/zh/zhControlPanel/DOIT-ARM/DOIT-ARM

## 2 接线

![wps2](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/StepperMotorCode/wps2.png)

## 3 蓝牙WiFi控制软件

注：仅支持安卓手机

下载地址：https://github.com/SmartArduino/SmartArduino.github.io/blob/master/docs/Robot/Controller/app/base.apk

## 4 示例程序

WiFi/蓝牙示例程序：

```
#define X_EN   38
#define X_STEP A0
#define X_DIR  A1
#define Y_EN   A2
#define Y_STEP A6
#define Y_DIR  A7
#define Z_EN   A8
#define Z_STEP 46
#define Z_DIR  48
#define E_EN   24
#define E_STEP 26
#define E_DIR  28
#define MAX_PACKETSIZE 32  //串口接收缓冲区
char buffUART[MAX_PACKETSIZE];
unsigned int buffUARTIndex = 0;
unsigned long preUARTTick = 0;
int i;
enum DN
{
  GO_FORWARD,
  GO_BACK,
  GO_RIGHT,
  GO_LEFT,
  STOP,
  DEF
}Drive_Num=DEF;

void forward()
{
  Serial.println("forward");
  digitalWrite(X_DIR,HIGH);
  digitalWrite(Y_DIR,LOW);
  digitalWrite(Z_DIR,HIGH);
  digitalWrite(E_DIR,LOW);
  for(i=0;i<=100;i++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}
void turnleft()
{
  Serial.println("turnleft");
  digitalWrite(X_DIR,HIGH);
  digitalWrite(Y_DIR,HIGH);
  digitalWrite(Z_DIR,HIGH);
  digitalWrite(E_DIR,HIGH);
  for(i=0;i<=100;i++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}
void turnright()
{
  Serial.println("turnright");
  digitalWrite(X_DIR,LOW);
  digitalWrite(Y_DIR,LOW);
  digitalWrite(Z_DIR,LOW);
  digitalWrite(E_DIR,LOW);
  for(i=0;i<=100;i++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}
void back()
{
  Serial.println("back");
  digitalWrite(X_DIR,LOW);
  digitalWrite(Y_DIR,HIGH);
  digitalWrite(Z_DIR,LOW);
  digitalWrite(E_DIR,HIGH);
  for(i=0;i<=100;i++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}
void Stop()
{
  Serial.println("stop");
  digitalWrite(X_DIR,LOW);
  digitalWrite(Y_DIR,LOW);
  digitalWrite(Z_DIR,LOW);
  digitalWrite(E_DIR,LOW);
  digitalWrite(X_STEP,LOW);
  digitalWrite(Y_STEP,LOW);
  digitalWrite(Z_STEP,LOW);
  digitalWrite(E_STEP,LOW);
}
void BT()
{
   char Uart_Date;
   int char_to_int;
   if(Serial.available())
   { 
      char Uart_Date = Serial.read();
      Serial.println(Uart_Date);
      char_to_int = (int)Uart_Date;
      Serial.println(char_to_int);
   }
   if(buffUARTIndex > 0 && (millis() - preUARTTick >= 100))//超过100ms没接到数据，则认为已经接收到完整指令
   { //data ready
      buffUART[buffUARTIndex] = 0x00;
      if((buffUART[0]=='C') && (buffUART[1]=='M') && (buffUART[2]=='D')) //若发送指令非法，则忽略
      {
        ;
      }
      else Uart_Date=buffUART[0];
        buffUARTIndex = 0;
    }
    switch(char_to_int)
    {
      case '2': Drive_Num = GO_FORWARD; break;
      case '8': Drive_Num = GO_BACK;    break;
      case '4': Drive_Num = GO_RIGHT;   break;
      case '6': Drive_Num = GO_LEFT;    break;
      case '5': Drive_Num = STOP;       break;
      default: break;
    }
}
void Car_control()
{
  switch(Drive_Num)
  {
    case GO_FORWARD: forward();    break;
    case GO_BACK:    back();       break;
    case GO_LEFT:    turnleft();   break;
    case GO_RIGHT:   turnright();  break;
    case STOP:       Stop();       break;
    default: break;
  }
}

void setup() 
{
  Serial.begin(115200);
  pinMode(X_EN,  OUTPUT);
  pinMode(X_STEP,OUTPUT);
  pinMode(X_DIR, OUTPUT);
  pinMode(Y_EN,  OUTPUT);
  pinMode(Y_STEP,OUTPUT);
  pinMode(Y_DIR, OUTPUT);
  pinMode(Z_EN,  OUTPUT);
  pinMode(Z_STEP,OUTPUT);
  pinMode(Z_DIR, OUTPUT);
  pinMode(E_EN,  OUTPUT);
  pinMode(E_STEP,OUTPUT);
  pinMode(E_DIR, OUTPUT);
  digitalWrite(X_EN, LOW);
  digitalWrite(Y_EN, LOW);
  digitalWrite(Z_EN, LOW);
  digitalWrite(E_EN, LOW);
}
void loop() 
{
  BT();
  Car_control();
}
```



PS2手柄示例程序：

程序里面使用到的第三方库，请自行下载：https://github.com/SmartArduino/Arduino-Third-party-Libraries

```
#include <PS2X_lib.h>  //for v1.6

//PS2手柄引脚；
#define PS2_DAT        13      
#define PS2_CMD        22
#define PS2_SEL        49  
#define PS2_CLK        12  

// 电机控制引脚；
#define X_EN   38
#define X_STEP A0
#define X_DIR  A1
#define Y_EN   A2
#define Y_STEP A6
#define Y_DIR  A7
#define Z_EN   A8
#define Z_STEP 46
#define Z_DIR  48
#define E_EN   24
#define E_STEP 26
#define E_DIR  28

enum DN
{
  GO_FORWARD,
  GO_BACK,
  GO_LEFT,
  GO_RIGHT,
  STOP,
  DEF
}Drive_Num=DEF;

/******************************************************************
 * select modes of PS2 controller:
 *   - pressures = analog reading of push-butttons 
 *   - rumble    = motor rumbling
 * uncomment 1 of the lines for each mode selection
 ******************************************************************/
#define pressures   true
//#define pressures   false
#define rumble      true
//#define rumble      false

PS2X ps2x; // create PS2 Controller Class

//right now, the library does NOT support hot pluggable controllers, meaning 
//you must always either restart your Arduino after you connect the controller, 
//or call config_gamepad(pins) again after connecting the controller.

int error = 0;
byte type = 0;
byte vibrate = 0;
int R;

void (* resetFunc) (void) = 0;

/******初始化******/
 void setup()
 {
  pinMode(X_EN,  OUTPUT);
  pinMode(X_STEP,OUTPUT);
  pinMode(X_DIR, OUTPUT);
  pinMode(Y_EN,  OUTPUT);
  pinMode(Y_STEP,OUTPUT);
  pinMode(Y_DIR, OUTPUT);
  pinMode(Z_EN,  OUTPUT);
  pinMode(Z_STEP,OUTPUT);
  pinMode(Z_DIR, OUTPUT);
  pinMode(E_EN,  OUTPUT);
  pinMode(E_STEP,OUTPUT);
  pinMode(E_DIR, OUTPUT);
  digitalWrite(X_EN, LOW);
  digitalWrite(Y_EN, LOW);
  digitalWrite(Z_EN, LOW);
  digitalWrite(E_EN, LOW);
   Serial.begin(115200);
   delay(300) ; //added delay to give wireless ps2 module some time to startup, before configuring it
   //CHANGES for v1.6 HERE!!! **************PAY ATTENTION*************

  //setup pins and settings: GamePad(clock, command, attention, data, Pressures?, Rumble?) check for error
  error = ps2x.config_gamepad(PS2_CLK, PS2_CMD, PS2_SEL, PS2_DAT, pressures, rumble);

  if(error == 0){
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
  else if(error == 1){
    Serial.println("No controller found, check wiring, see readme.txt to enable debug. visit www.billporter.info for troubleshooting tips");
    resetFunc();
  }
  else if(error == 2){
    Serial.println("Controller found but not accepting commands. see readme.txt to enable debug. Visit www.billporter.info for troubleshooting tips");
  }

  else if(error == 3){
    Serial.println("Controller refusing to enter Pressures mode, may not support it. ");
  }

 //  Serial.print(ps2x.Analog(1), HEX);

  type = ps2x.readType(); 
  switch(type) {
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

//定义小车运动方式

 void turnLeft()//左转
{
  digitalWrite(X_DIR,HIGH);
  digitalWrite(Y_DIR,HIGH);
  digitalWrite(Z_DIR,HIGH);
  digitalWrite(E_DIR,HIGH);
  for(R=0;R<=100;R++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}

 void turnRight()//右转
{
  digitalWrite(X_DIR,LOW);
  digitalWrite(Y_DIR,LOW);
  digitalWrite(Z_DIR,LOW);
  digitalWrite(E_DIR,LOW);
  for(R=0;R<=100;R++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}

void forward()//前进
{ 
  digitalWrite(X_DIR,HIGH);
  digitalWrite(Y_DIR,LOW);
  digitalWrite(Z_DIR,HIGH);
  digitalWrite(E_DIR,LOW);
  for(R=0;R<=100;R++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}

void back()//后退
{
  digitalWrite(X_DIR,LOW);
  digitalWrite(Y_DIR,HIGH);
  digitalWrite(Z_DIR,LOW);
  digitalWrite(E_DIR,HIGH);
  for(R=0;R<=100;R++)
  {
    digitalWrite(X_STEP,HIGH);
    digitalWrite(Y_STEP,HIGH);
    digitalWrite(Z_STEP,HIGH);
    digitalWrite(E_STEP,HIGH);
    delayMicroseconds(100);
    digitalWrite(X_STEP,LOW);
    digitalWrite(Y_STEP,LOW);
    digitalWrite(Z_STEP,LOW);
    digitalWrite(E_STEP,LOW);
    delayMicroseconds(100);
  }
}
void Stop() // 停止；
{
  digitalWrite(X_DIR,LOW);
  digitalWrite(Y_DIR,LOW);
  digitalWrite(Z_DIR,LOW);
  digitalWrite(E_DIR,LOW);
  digitalWrite(X_STEP,LOW);
  digitalWrite(Y_STEP,LOW);
  digitalWrite(Z_STEP,LOW);
  digitalWrite(E_STEP,LOW);
}
void ps2()
{
  /* You must Read Gamepad to get new values and set vibration values
     ps2x.read_gamepad(small motor on/off, larger motor strenght from 0-255)
     if you don't enable the rumble, use ps2x.read_gamepad(); with no values
     You should call this at least once a second
   */  
  if(error == 1) //skip loop if no controller found
    return; 

  if(type == 2) {//Guitar Hero Controller
  return;
  }
  else  { //DualShock Controller
    ps2x.read_gamepad(false, vibrate); //read controller and set large motor to spin at 'vibrate' speed


//start 开始运行，电机初PWM为100；
// 电机正转；
    if(ps2x.Button(PSB_PAD_UP)){
      Serial.println("Up held this hard: ");
      Drive_Num = GO_FORWARD;
    }

// 电机反转；
    else if(ps2x.Button(PSB_PAD_DOWN)){
      Serial.println("Down held this hard: ");
      Drive_Num = GO_BACK;
    }

 //左转；   
    else if(ps2x.Button(PSB_PAD_LEFT)){
       Serial.println("turn left ");
       Drive_Num = GO_LEFT;       
    }

//右转；
   else if(ps2x.Button(PSB_PAD_RIGHT))
   {
    Serial.println("turn right");
    Drive_Num = GO_RIGHT;
   }
   else
   {
      Drive_Num = STOP;
   }
  }
}
void Car_Control()
{
  switch(Drive_Num)
  {
    case GO_FORWARD: forward();   break;
    case GO_BACK:    back();      break;
    case GO_LEFT:    turnLeft();  break;
    case GO_RIGHT:   turnRight(); break;
    case STOP:       Stop();      break;
  }
}
void loop()
{
   ps2();
   Car_Control();
}
```



### 支持与服务

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