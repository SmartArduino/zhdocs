<center><font size=10> Arduino传感器认识与应用 </center></font>
<center> From SZDOIT</center>

## 1. 按钮开关

![image-20201021152159434](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021152159434.png)

![image-20201021152304963](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021152304963.png)

```
 int Led=13;       //定义LED 接口
 int buttonpin=3； //定义按键开关传感器接口
 int val;          //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义按键开关传感器为输入接口
 }
 void loop()
 {
     val=digitalRead(buttonpin);//将数字接口3的值读取赋给val
     if(val==HIGH)              //当按键开关传感器检测有信号时，LED 闪烁
     {
     	digitalWrite(Led,HIGH)
     }
     else
     {
     	digitalWrite(Led,LOW)
     }
 }
```

## 2. 无源蜂鸣器

![image-20201021152454242](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021152454242.png)

![image-20201021152511506](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021152511506.png)

```
int buzzer=8;//设置控制蜂鸣器的数字IO脚
void setup()
{ 
	pinMode(buzzer,OUTPUT);//设置数字IO脚模式，OUTPUT为输出
}
void loop()
{ 
	unsigned char i,j;     //定义变量
    for(i=0;i<80;i++)      //辒出一个频率的声音
    {
        digitalWrite(buzzer,HIGH); //发声音
        delay(1);                  //延时1ms
        digitalWrite(buzzer,LOW);  //不发声音
        delay(1);                  //延时ms
    }
    for(i=0;i<100;i++)  //输出出另一个频率的声音
    { 
        digitalWrite(buzzer,HIGH); //发声音
        delay(2);                  //延时2ms
        digitalWrite(buzzer,LOW);  //不发声音
        delay(2);                  //延时2ms
    }
}
```

```
 int buzzer=8;               //设置控制蜂鸣器的数字IO脚
 void setup()
 { 
 	pinMode(buzzer,OUTPUT); //设置数字IO脚模式，OUTPUT为辒出
 }
 void loop()
 { 
     unsigned char i,j;     //定义变量
     for(i=0;i<100;i++)     //输出一个频率的声音
     { 
         digitalWrite(buzzer,HIGH);//发声音
         delayMicroseconds(40);    // 延时40微秒
         digitalWrite(buzzer,LOW); //不发声音
         delayMicroseconds(40);    //延时40微秒
     }
     for(i=0;i<250;i++)      //辒出另一个频率癿声音
     { 
         digitalWrite(buzzer,HIGH);//发声音
         delayMicroseconds(120);   //延时120微秒
         digitalWrite(buzzer,LOW); //不发声音
         delayMicroseconds(120);   //延时120微秒
     }
 }
```

## 3. 有源蜂鸣器

![image-20201021154550578](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021154550578.png)

```
 
 int speakerPin = 8; //控制喇叭的引脚
 int value = 10;     //控制喇叭响的时间，可自行更改
 void setup()
 {
 	pinMode(speakerPin, OUTPUT);
 }
 void loop()
 {
     digitalWrite(speakerPin, HIGH);
     delay(value);   //调节喇叭响的时间；
     digitalWrite(speakerPin, LOW);
     delay(value);  //调节喇叭不响的时间；
 }

```

## 4. 激光传感器

![image-20201021154729352](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021154729352.png)

```
实例程序
 void setup()
 {
 	pinMode(13, OUTPUT);      // 定义13脚为数字输出接口
 }
 void loop() 
 {
     digitalWrite(13, HIGH); // 打开激光头
     delay(1000);            // 延时一秒
     digitalWrite(13, LOW);  // 关闭激光头
     delay(1000);            // 延时一秒
 }
```

## 5. 光明传感器

![image-20201021154944918](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021154944918.png)

![image-20201021155014050](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021155014050.png)

```
 int sensorPin = 2;
 int value = 0;
 void setup()
 {
 	Serial.begin(9600); //串口波特率为9600
 }
 void loop()
 {
     value = analogRead(sensorPin); //读取模拟2端口
     Serial.println(value, DEC);    //十进制数显示结果并且换行
     delay(50);                     //延时50毫秒
 }
```

## 6. 倾斜开关

![image-20201021155157494](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021155157494.png)

![image-20201021155215783](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021155215783.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义 倾斜开关传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义 倾斜开关传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin); //将数字接口3的值读取赋给val
     if(val==HIGH)               //当 倾斜开关传感器检测有信号时，LED 亮
     {
     	digitalWrite(Led,HIGH);
     }
     else
     {
    	 digitalWrite(Led,LOW);
     }
 }
```

## 7. 水银开关传感器

![image-20201021155544285](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021155544285.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义 倾斜开关传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义 倾斜开关传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin); //将数字接口3的值读取赋给val
     if(val==HIGH)               //当 倾斜开关传感器检测有信号时，LED 闪烁
     {
     	digitalWrite(Led,HIGH);
     }
     else
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 8. 魔术光环（一对）

![image-20201021155731452](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021155731452.png)

![image-20201021155746971](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021155746971.png)

```
 int LedPinA = 5;
 int LedPinB = 6;
 int ButtonPinA = 7;
 int ButtonPinB = 4;
 int buttonStateA = 0;
 int buttonStateB = 0;
 int brightness = 0;
 void setup()
 {
     pinMode(LedPinA, OUTPUT);
     pinMode(LedPinB, OUTPUT);
     pinMode(ButtonPinA, INPUT);
     pinMode(ButtonPinB, INPUT);
     }
  void loop()
 {
     buttonStateA = digitalRead(ButtonPinA); //读取A模块
     if (buttonStateA == HIGH && brightness != 255)
     { //当A模块检测到信号，且亮度不是最大时，亮度值增加
     	brightness ++;
     }
     buttonStateB = digitalRead(ButtonPinB);
     if (buttonStateB == HIGH && brightness != 0)
     { //当B模块检测到信号，且亮度不是最小时，亮度值减小
     	brightness --;
     }
     analogWrite(LedPinA, brightness);       // A慢漸暗
     analogWrite(LedPinB, 255 - brightness); // B慢漸亮
     delay(25);
 }
 //两者相加的和为255，亮度此消彼涨的关系
```

## 9. 震动开关

![image-20201021160127323](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160127323.png)

![image-20201021160138311](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160138311.png)

```
 int Led=13;   //定义LED 接口
 int Shock=3;  //定义震动传感器接口
 int val;      //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);  //定义LED 为输出接口
     pinMode(Shock,INPUT); //定义震动传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(Shock); //将数字接口3的值读取赋给val
     if(val==HIGH)           //当震动传感器检测有信号时，LED 闪烁
     {
        digitalWrite(Led,LOW);
     }
     else
     {
        digitalWrite(Led,HIGH);
     }
 }
```

## 10. 敲击传感器

![image-20201021160355193](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160355193.png)

```
 int Led=13;   //定义LED 接口
 int Shock=3;  //定义震动传感器接口
 int val;      //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);  //定义LED 为输出接口
     pinMode(Shock,INPUT); //定义震动传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(Shock); //将数字接口3的值读取赋给val
     if(val==HIGH)           //当震动传感器检测有信号时，LED 闪烁
     {
     	digitalWrite(Led,LOW);
     }
     else
     {
    	 digitalWrite(Led,HIGH);
     }
 }
```

## 11. 双色共阴LED模块

![image-20201021160602087](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160602087.png)

![image-20201021160621090](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160621090.png)

```
 int redpin = 11;  // 选择红灯引脚
 int greenpin =10; // 选择绿灯引脚
 int val;
 void setup()
 { 
     pinMode(redpin, OUTPUT);
     pinMode(greenpin, OUTPUT);
 }
 void loop()
 {
     for(val=255; val>0; val--)
     { 
         analogWrite(redpin, val);
         analogWrite(greenpin, 255-val);
         delay(15);
     }
     for(val=0; val<255; val++)
     { 
         analogWrite(redpin, val);
         analogWrite(greenpin, 255-val);
         delay(15);
     }
 }
```

## 12. 三色RGB模块（DIP封装）

![image-20201021160751192](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160751192.png)

```
 int redpin = 11; //select the pin for the red LED
 int bluepin =10; // select the pin for the blue LED
 int greenpin =9; // select the pin for the green LED
 int val;
 void setup()
 { 
     pinMode(redpin, OUTPUT);
     pinMode(bluepin, OUTPUT);
     pinMode(greenpin, OUTPUT);
 }
 void loop()
 { 
     for(val=255; val>0; val--)
     { 
         analogWrite(redpin, val);
         analogWrite(bluepin, 255-val);
         analogWrite(greenpin, 128-val);
         delay(2);
     }
     for(val=0; val<255; val++)
     { 
         analogWrite(redpin, val);
         analogWrite(bluepin, 255-val);
         analogWrite(bluepin, 128-val);
         delay(2);
     }
 }
```

## 13. 三色RGB模块（SMD封装）

![image-20201021160916456](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021160916456.png)

## 14. 7彩自动闪烁LED模块

![image-20201021161020147](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161020147.png)

```
 void setup()
 {
 	pinMode(13, OUTPUT);
 }
 void loop()
 {
     digitalWrite(13, HIGH); // set the LED on
     delay(8000);            // wait for a second
     digitalWrite(13, LOW);  // set the LED off
     delay(1000);            // wait for a second
 }
```

## 15. 金属触摸传感器

![image-20201021161156278](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161156278.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义金属触摸传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);       //定义LED 为输出接口
     pinMode(buttonpin,INPUT);  //定义金属触摸传感器为输出接口
 }
 void loop()
 { 
     val=digitalRead(buttonpin); //将数字接口3的值读取赋给val
     if(val==HIGH)               //当金属触摸传感器检测有信号时，LED 亮
     {
    	 digitalWrite(Led,HIGH);
     }
     else
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 16. 火焰传感器

![image-20201021161329591](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161329591.png)

![image-20201021161341336](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161341336.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义 火焰传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义 火焰传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin); //将数字接口3的值读取赋给val
     if(val==HIGH)               //当火焰传感器检测有信号时，LED 亮，否则灭
     {
     	digitalWrite(Led,HIGH);
     }
     else
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 17. 手指测心跳模块

![image-20201021161505831](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161505831.png)

```
 int ledPin=13;     //显示灯在13引脚
 int sensorPin=0;   //传感器引脚在模拟输入第0脚
 double alpha=0.75; //修正值，用于增加平滑度
 int period=20;
 double change=0.0;
 void setup()
 {
 	pinMode(ledPin,OUTPUT);
 }
 void loop()
 {
     static double oldValue=0;
     static double oldChange=0;
     int rawValue=analogRead(sensorPin);               //读取传感器的值
     double value=alpha*oldValue+(1-alpha)*rawValue;
     change=value-oldValue;
     digitalWrite(ledPin,(change<0.0&&oldChange>0.0)); //输出

     oldValue=value;
     oldChange=change;
     delay(period);
 }
```

## 18. 红外避障传感器

![image-20201021161636492](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161636492.png)

![image-20201021161648672](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161648672.png)

```
 int buttonpin=3; //定义避障传感器接口
 int val;//定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);//定义LED 为输出接口
     pinMode(buttonpin,INPUT);//定义避障传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin);//将数字接口3的值读取赋给val
     if(val==LOW)//当避障传感器检测有障碍物时为低电平
     {
     	digitalWrite(Led,HIGH); //提示有障碍物
     }
     else
     {
     	digitalWrite(Led,LOW); //没有障碍物
     }
 }
```

## 19. 寻线传感器

![image-20201021161800378](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161800378.png)

![image-20201021161814468](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161814468.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义 寻线传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义 寻线传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin);//将数字接口3的值读取赋给val
     if(val==HIGH)              //当寻线传感器检测有反射信号时，LED 亮
     {
    	 digitalWrite(Led,HIGH);
     }
     else
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 20. 光折断传感器

![image-20201021161946778](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021161946778.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义光遮断传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);       //定义LED 为输出接口
     pinMode(buttonpin,INPUT);  //定义光遮断传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin);  //将数字接口3的值读取赋给val
     if(val==HIGH)                //当光遮断传感器检测有信号时，LED 亮
     {
     	digitalWrite(Led,HIGH);
     }
     else
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 21. 线性霍尔磁力传感器

![image-20201021162119834](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162119834.png)

![image-20201021162133418](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162133418.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义线性霍尔传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义线性霍尔传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin);//将数字接口3的值读取赋给val
     if(val==HIGH)              //当霍尔传感器检测没有磁场信号时，LED 亮
     {
     	digitalWrite(Led,HIGH);
     }
     else                       //当霍尔传感器检测到有磁场信号时，LED灭
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 22. 模拟霍尔传感器

![image-20201021162309106](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162309106.png)

![image-20201021162327087](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162327087.png)

```
 int sensorPin = 1;
 int value = 0;
 void setup()
 {
 	Serial.begin(9600);         //串口波特率为9600
 }
 void loop()
 {
     value = analogRead(sensorPin); //读取模拟1端口
     Serial.println(value, DEC);    //十进制数显示结果并且换行
     delay(50);                     //延时50毫秒
 }
```

## 23. 大磁簧传感器

![image-20201021162442863](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162442863.png)

![image-20201021162456674](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162456674.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义 磁环传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);      //定义LED 为输出接口
     pinMode(buttonpin,INPUT); //定义 磁环传感器为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin); //将数字接口3的值读取赋给val
     if(val==HIGH)               //当 磁环传感器检测有信号时，LED 亮
     {
     	digitalWrite(Led,HIGH);
     }
     else                        //没有信号则灭
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 24. 迷你磁环传感器

![image-20201021162628168](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162628168.png)

```
 int Led=13;      //定义LED 接口
 int buttonpin=3; //定义 磁环传感器接口
 int val;         //定义数字变量val
 void setup()
 {
     pinMode(Led,OUTPUT);     //定义LED 为输出接口
     pinMode(buttonpin,INPUT);//定义 磁环传感器为输入接口
 }
 void loop()
 {
     val=digitalRead(buttonpin);//将数字接口3的值读取赋给val
     if(val==HIGH)              //当 磁环传感器检测有信号时，LED 亮
     {
     	digitalWrite(Led,HIGH);
     }
     else
     {
     	digitalWrite(Led,LOW);
     }
 }
```

## 25. 旋转编码器

![image-20201021162745527](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162745527.png)

![image-20201021162802944](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162802944.png)

![image-20201021162841915](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021162841915.png)

```
 const int interruptA = 0; // 中断 Interrupt 0 在 pin 2 上
 int CLK = 2;              // PIN2 脉冲信号
 int DAT = 3;              // PIN3
 int SW= 4;                // PIN4 往下按压的开关信号
 int LED1 = 5;             // PIN5
 int LED2 = 6;             // PIN6
 int COUNT = 0;
 void setup()
 { 
     attachInterrupt(interruptA, RoteStateChanged, FALLING);
     // 高电平变为低电平触发 ，调用中断处理子函数RoteStateChanged（）
     pinMode(CLK, INPUT);
     digitalWrite(2, HIGH); // 上拉电阻
     pinMode(DAT, INPUT);
     digitalWrite(3, HIGH); // 上拉电阻
     pinMode(SW, INPUT);
     digitalWrite(4, HIGH); // 上拉电阻
     pinMode(LED1, OUTPUT);
     pinMode(LED2, OUTPUT);
     Serial.begin(9600);   //设置波特率为9600
 }
 void loop()
 { 
     if (!(digitalRead(SW)))           //如果按下按钮
     { 
         COUNT = 0;                        //计数清零
         Serial.println(“STOP COUNT = 0”); //串口输出清零
         digitalWrite(LED1, LOW);          //LED1灯灭
         digitalWrite(LED2, LOW);          //LED2灯灭
         delay (2000);                     //延时2秒
     }
     Serial.println(COUNT);         //如果没有按钮，输出计数值
 }
 void RoteStateChanged()           //当CLK下降沿触发的时候，进入中断
 { 
     if (digitalRead(DAT))         // 当DAT为高电平时，是前进方向
     { 
         COUNT++;                  //计数器累加
         digitalWrite(LED1, HIGH); // LED1亮
         digitalWrite(LED2, LOW);  //LED2 灭
         delay(20);
     }
     else                          // 当 DAT是低电平是反方向滚动
     { 
         COUNT--;                  //计数器累减
         digitalWrite(LED2, HIGH); // LED2亮
         digitalWrite(LED1, LOW);  // LED1灭
         delay(20);
     }
 }
```

## 26. 麦克风声音传感器

![image-20201021163334891](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021163334891.png)

```
//数字输出
 nt Led=13;       //定义LED 接口
 int buttonpin=3  //定义传感器D0接口
 int val;         //定义数字变量val
 void setup()
 { 
     pinMode(Led,OUTPUT);       //定义LED 为输出接口
     pinMode(buttonpin,INPUT);  //定义传感器D0为输出接口
 }
 void loop()
 {
     val=digitalRead(buttonpin); //将数字接口3的值读取赋给val
     if(val==HIGH)               //当声音检测模块检测有信号时，LED 闪烁
     {
     	digitalWrite(Led,HIGH)
     }
     else
     {
     	digitalWrite(Led,LOW)
     }
 }
```

```
//模拟输出
 int sensorPin = A5;   // 选择模拟5输入端口
 int ledPin = 13;      // 选择LED显示端口
 int sensorValue = 0;  // 声音值变量
 void setup()
 { 
     pinMode(ledPin, OUTPUT);
     Serial.begin(9600);
 }
 void loop()
 { 
     sensorValue = analogRead(sensorPin); //读声音传感器的值
     digitalWrite(ledPin, HIGH);          //灯闪烁
     delay(50);
     digitalWrite(ledPin, LOW);           //灯闪烁
     delay(50);
     Serial.println(sensorValue, DEC);    //以10进制的形式输出声音值
 }
```

## 27. 高感度声音传感器

![image-20201021163920513](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021163920513.png)

## 28. 模拟式温度传感器

![image-20201021163956427](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021163956427.png)

```
 #include <math.h>
 double Thermister(int RawADC)
 { 
     double Temp; Temp = log(((10240000/RawADC) - 10000));
     Temp = 1 / (0.001129148 + (0.000234125 + (0.0000000876741 *
     Temp * Temp ))* Temp );
     Temp = Temp - 273.15;
     // 转换温度值;
     return temp;
 }
 void setup()
 {
 	Serial.begin(9600);
 }
 void loop()
 { 
     Serial.print(Thermister(analogRead(0))); // 输出转换好的温度值
     Serial.println("c");
     delay(500);
 }
```

## 29. 数字温度传感器

![image-20201021164115425](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164115425.png)

![image-20201021164129619](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164129619.png)

## 30. 温湿度传感器

![image-20201021164158738](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164158738.png)

![image-20201021164214125](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164214125.png)

```
 int DHpin = 8; //数字第8引脚读取
 byte dat[5]; //设置5个字节的数组
 byte read_data()
 { 
     byte data;
     for(int i=0; i<8; i++)
     { 
         if(digitalRead(DHpin) == LOW)
         { 
             while(digitalRead(DHpin) == LOW); //等待50us；
             delayMicroseconds(30);             //判断高电平的持续时间，以判定数据是‘0’还是‘1’；
             if(digitalRead(DHpin) == HIGH) data |= (1<<(7-i)); //高位在前，低位在后；
             while(digitalRead(DHpin) == HIGH);                 //数据‘1’，等待下一位的接收；
         }
     	return data;
 	}
 }
 void start_test()
 { 
     digitalWrite(DHpin,LOW); //拉低总线，发开始信号；
     delay(30);               //延时要大于18ms，以便DHT11能检测到开始信号；
     digitalWrite(DHpin,HIGH);
     delayMicroseconds(40);   //等待DHT11响应；
     pinMode(DHpin,INPUT);    //改为输入读取模式
     while(digitalRead(DHpin) == HIGH);
     delayMicroseconds(80);   //DHT11发出响应，拉低总线80us；
     if(digitalRead(DHpin) == LOW);
     delayMicroseconds(80);   //DHT11拉高总线80us后开始发送数据；
     for(int i=0;i<4;i++)     //接收温湿度数据，校验位不考虑；
     dat[i] = read_data();
     pinMode(DHpin,OUTPUT);   //改为输出模式
     digitalWrite(DHpin,HIGH);//发送完一次数据后释放总线，等待主机的下一次开始信号；
 }
 void setup()
 { 
     Serial.begin(9600);
     pinMode(DHpin,OUTPUT);
 }
 void loop()
 { 
     start_test();
     Serial.print("Current humdity = ");
     Serial.print(dat[0], DEC); //显示湿度的整数位；
     Serial.print('.');
     Serial.print(dat[1],DEC);  //显示湿度的小数位；
     Serial.println('%');
     Serial.print("Current temperature = ");
     Serial.print(dat[2], DEC); //显示温度的整数位；
     Serial.print('.');
     Serial.print(dat[3],DEC);  //显示温度的小数位；
     Serial.println('C');
     delay(700);
 }
```

## 31. DS18b20 数字温度传感器模块

![image-20201021164745872](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164745872.png)

![image-20201021164759432](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164759432.png)

![image-20201021164819319](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164819319.png)

```
 #include <OneWire.h>
 #include <DallasTemperature.h>
 #define ONE_WIRE_BUS 2               // 数据线接数据口2
 OneWire oneWire(ONE_WIRE_BUS);       //实例化一个对象
 DallasTemperature sensors(&oneWire); //实例化一个对象
 void setup(void)
 { 
     Serial.begin(9600);             //串口波特率9600
     Serial.println("Dallas Temperature IC Control Library Demo");
     sensors.begin();                //调用该对象的方法，启动传感器初始化
 }
 void loop(void)
 {
     Serial.print(“Requesting temperatures...”);
     sensors.requestTemperatures();              // 发送命令去读取温度
     Serial.println("DONE");
     Serial.print(“Temperature for the device 1 (index 0) is: ”);
     Serial.println(sensors.getTempCByIndex(0)); //显示索引号为0的传感器温度。（可在总线上接多个传感器，根据索引号地址来区分）
 }
```

## 32. 红外发射

![image-20201021164954060](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021164954060.png)

![image-20201021165008895](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165008895.png)

```
//将红外S端接数字第3脚（PWM)
 #include <IRremote.h>
 IRsend irsend; //实例化一个对象
 void setup()
 {
 	Serial.begin(9600);
 }
 void loop()
 { 
     if (Serial.read() != -1)
     { 
         for (int i = 0; i < 3; i++)
         { 
             irsend.sendSony(0xa90, 12); // Sony TV power code
             delay(40);
         }
     }
 }
```

## 33. 红外接收

![image-20201021165121862](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165121862.png)

![image-20201021165136790](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165136790.png)

```
 #include <IRremote.h>
 int RECV_PIN = 11;       //定义红外接收器的引脚为11
 IRrecv irrecv(RECV_PIN); //实例化一个对象，并使用第11脚进行接收
 decode_results results;
 void setup()
 {
     Serial.begin(9600);
     irrecv.enableIRIn(); // 初始化红外接收器
 }
 void loop()
 {
     if (irrecv.decode(&results))
     { 
         Serial.println(results.value, HEX); //以16进制换行输出接收代码
         Serial.println(); 					 //为了便于观看输出结果增加一个空行
         irrecv.resume();                    // 接收下一个值
     }
 }
```

## 34. Joystick PS2 摇杆

![image-20201021165302402](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165302402.png)

![image-20201021165321726](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165321726.png)

![image-20201021165332165](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165332165.png)

```
 int Xaxis=A0; //定义X轴由模拟0端口读取
 int Yaxis=A1; //定义Y轴由模拟1端口读取
 int Zsw=A2;   //定义Z按钮由模拟2端口读取（因为开关最大值低于2.5V）
 int value = 0;//该变量读取模拟口的值
 void setup()
 {
 	Serial.begin(9600);
 }
 void loop()
 { 
     value = analogRead(Xaxis); //读取模拟端口0
     Serial.print("X:");
     Serial.print(value, DEC);
     value = analogRead(Yaxis); //读取模拟端口1
     Serial.print(" | Y:");
     Serial.print(value, DEC);
     value = analogRead(Zsw);   //读取模拟端口2
     Serial.print(" | Z: ");
     Serial.println(value, DEC);
     delay(100);
 }
```

## 35. 继电器

![image-20201021165444099](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165444099.png)

![image-20201021165455443](https://github.com/SmartArduino/zhdocs/raw/master/zhControlPanel/Sensor/image-20201021165455443.png)

```
 int relayPin=3;
 int buttonPin=4;
 void setup()
 { 
     pinMode(relayPin,OUTPUT); //定义端口属性为输出；
     pinMode(buttonPin,INPUT);//定义端口属性为输入；
 }
 void loop()
 { 
     if(digitalRead(buttonPin)==HIGH)
     	digitalWrite(relay,HIGH); //继电器导通；
     else
         digitalWrite(relay,LOW); //继电器开关断开；
         delay(1000);
 }
```

