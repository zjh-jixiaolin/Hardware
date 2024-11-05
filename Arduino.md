# Arduino入门教程笔记

---

[TOC]

## 原理图

[原理图链接](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg-blog.csdnimg.cn%2Fimg_convert%2F5610153902d037b7289d9fd54048b64b.png&refer=http%3A%2F%2Fimg-blog.csdnimg.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1668409420&t=23d2270b7f35c3c77109f7870a25fb5d)

## 1、入门理论

### 什么是程序？

程序是指挥 计算机做事的一连串指令。

Arduino 的程序设计采用改良过的C语言，C语言是 控制硬件方面 几乎唯一普遍使用的高级语言。

C语言是由很多适合人阅读的`英文字母`和`符号`组成。而系统CPU只认得 0和1 组成的指令（称为`机器码`）。

所以我们得把`C语言`翻译成`计算机`能够读懂的`0和1`的`机器码`，CPU才能执行。这个翻译过程叫`编译`。

### 程序常量

HIGH 或 LOW，表示数字`I/O引脚`的`电平`;

HIGH 代表 高电平（1）;

LOW 代表 低电平（0）;

>当使用LED时，首先判断是`共阴`还是`共阳`。共阴是高电平亮，共阳是低电平亮。

INPUT 或 OUTPUT，表示数字`I/O引脚`的`方向`;

INPUT 表示输入(高阻态);

OUTPUT 表示输出（AVR能提供5V电压，40mA电流）;

TRUE 或者 FALSE，TRUE表示真(1),FALSE表示假(0);

### 程序结构

主要包括两部分，即void setup() 和 void loop()。

前者为声明`变量及引脚的名称`（如int val;int ledPin=13），在程序开始时使用，`初始化变量`和`引脚模式`。

- void set()函数全程只执行一次，只在初始设置时执行一次;

- void loop()用在setup()函数之后，不断`循环`执行，是Arduino的主体。

### 一、引脚工作模式 —— pinMode()函数

---

pinMode(pin,mode) 函数用于`配置引脚`以及设置`输出`和`输出`模式，是一个`无返回值`函数。

- pin 参数代表要 配置的引脚;
- mode 参数表示设置`引脚的模式` 为 `INPUT（输入）`或 `OUTPUT（输出）`
- 参数用英文`逗号，`隔开，用英文的`括号（）`括起来。

`INPUT` 用于``读取信号``，`OUTPUT`用于`输出控制信号`。

pin的范围是数字引脚的0到13，也可以把模拟引脚A0~A5作为`输入`时不需要设置，`输出`时需要设置。

### 二、输出数字信号 —— digitalWrite()函数

---

digitalWrite(pin,mode) 函数用于`控制`一个管脚的`电压高低`。> digital:数字的 Write:向外输出

- pin 参数代表要 操作的管脚;
- mode 参数代表设置 管脚的电压高低。`HIGH`代表输出`5V高电压`，`LOW`代表输出`0V低电压`。

### 三、读取数字信号 —— digitalRead()函数

---

digitalRead(pin) 函数用于`读取`数字引脚的`HIGH`（高电平）和`LOW`(低电平)。

- pin 参数代表被读取的引脚号码



### 四、延时操作 —— delay()函数

---

计算`CPU`执行指令的速度很快，如果我们要`观察`一些执行结果和现象，就要让它适当的时候停下来。

指令：`delay(毫秒数);`  



## 2、进阶函数

### 一、串口操作 —— Serial()函数

---

Serial.begin(speed) 用于`开启串口`，通常置于`setup()函数`中。

- speed:`波特率`，一般取值 300,1200,2400,4800,9600,14400,19200,28800,38400,57600,115200。

Serial.print(val) 用于串口输出数据函数，`写入字符串数据到串口`。

- val：打印的值，任意数据类型。

Serial.println(val) 写入`字符串数据`，并`换行`。

- val：打印的值，任意数据类型。



### 二、模拟输入输出

---

模拟输入引脚是带有 ADC`（模数转换器）`功能的引脚。

ADC是指`模拟信号`如`电压值`转换为`数字信号`。它可以将外部输入的模拟信号转换为芯片运算时可以识别的数字信号，从而实现`读入`模拟值的功能。

### 三、模拟量读取 —— analogRead函数

----

analogRead(pin) 用于`读取`引脚模拟值，并转换为`数字信号`。

- pin 参数代表被读取的引脚号码

> UNO开发板上，只有A0 — A5 引脚有`模拟信号`。
>
> Arduino Uno模拟输入功能有``10位精度``，即可以将`0～5V`的电压信号转换为`0～1023`的整数形式表示

![a494a0e03965c9052e6f6fc4f1c225d6.png](https://img-blog.csdnimg.cn/img_convert/a494a0e03965c9052e6f6fc4f1c225d6.png)

### 四、模拟量输入 —— analogWrite函数

---

analogWrite(pin,value)为`无返回值`函数，作用是通过`PWM的方式`将`模拟值`输入到`引脚`。

- pin 参数表示`输出PWM`的引脚（只支持`3、5、6、9、10、11`）。
- value 参数表示`PWM占空比`。

PWM输出位数为8，所以其范围在0-255，对应占空比为0-100%。带`PWM功能`的引脚标有`波浪线~`。













## 2、Arduino 入门主体代码

```c
# 注释使用 //
void setup() {
	}	// 只执行一次，初始化变量和引脚模式。

void loop() { 
	}		// 不断循环，这是Arduino的主体。

```

### ① 控制LED —— 示例：

```c
/*
	# LED灯是一个电阻很小的元件，不可以直接用线直接接过去（电太多，灯不住，可能导致烧掉）。
	# 用电阻分摊电压，消耗一些电能，避免被烧掉。
*/
void setup() {
  pinMode(13,OUTPUT); // 13引脚作为输出
  pinMode(12,OUTPUT); // 12引脚作为输出
}

void loop() {
  digitalWrite(13,HIGH); // 13引脚给高电平（亮）
  digitalWrite(12,LOW);	 // 12引脚给低电平（暗）
  delay(1000);	// 延迟1秒
  digitalWrite(13,LOW);  // 13引脚给低电平（暗）
  digitalWrite(12,HIGH); // 12引脚给高电平（亮）
  delay(1000);	// 延迟1秒

}
```

### ② 按钮控制LED —— 示例

```c
/*
	# 5V与GND 相互连接会导致电流过大，烧坏主板。解决方案（10K Ω的电阻）将电流降低
*/
int buttonState = 0;         // 定义按钮的全局变量（整型）

# 初始化设置  // 复制记得删除
void setup() {
  pinMode(13, OUTPUT);  //初始化LED引脚作为输出；
  pinMode(7, INPUT);  //初始化按钮引脚作为输入；
}

# 重复循环执行  // 复制记得删除
void loop() { 
  // 读取按钮的值，检测是否按下
  buttonState = digitalRead(7); // 数字的读取
    
  if (buttonState == HIGH) {
    // 当被按下，为高电平 —— 灯亮
    digitalWrite(13, HIGH);
  }
  else {
    // 当未被按下，为低电平 —— 灯灭
    digitalWrite(13, LOW);
  }
}

```



<img src="https://www.hualigs.cn/image/634126fc75bec.jpg" alt="1" style="zoom: 67%;" />



### ③ 按钮创建计算器 —— 示例

```c
/*
  - 创建按钮计算器
  - 发现有问题，开始Debounce（去抖器）
*/

int pushButton = 7;   // 按钮用到引脚7，所以设置此变量。
int buttonState = 0;  // 假设按钮状态为0。
int beforeState = 0; // 按钮之前的状态
int presstime = 0;  // 假设按下的总次数

void setup() {
  Serial.begin(9600); // 打开串口，设置速率为 96000 bps。
  pinMode(pushButton, INPUT); // 将引脚7设定为输入（即检测器）
}

void loop() {
  buttonState = digitalRead(pushButton);  // 从引脚7 检测 按钮的状态（1为按下）

  if (buttonState == 1 and beforeState==0) {   // 当之前没按到，现在按到了
    
    presstime = presstime + 1; 
    Serial.print("hi ~~ ");  // 不换行 输出
    Serial.println(presstime); // 换行 输出状况
  }
  if (buttonState != beforeState) { // 如果按钮的状态 不是 之前按下的状态（说明有被按下）
      delay(50)  // 延迟50毫秒
  }
      
  beforeState = buttonState;  // 检测 之前是从有按变成没按，还是没按变成有按

  delay(10);        // 延迟1毫秒
}

```

按钮是一种有弹性的东西，接触点也比较小。可能会由于按钮弹跳连续接触到好几下，弹跳导致电压不是瞬间起来。

由于物理元件的弹性会导致连续跳好几次，而出现DE`bounce`的感觉。

解决：当按下放开时，延迟20-50毫秒消除Debounce

<img src="https://www.hualigs.cn/image/63413dfae1a2b.jpg" style="zoom:50%;" />

## 2、Arduino 进阶主体代码

### ① 模拟信号输入 —— 实例

---

<img src="https://s1.xptou.com/2022/10/15/634a9507e0cf8.png" style="zoom: 50%;" />

```c
/*
  --可变电阻（电位器）的类比讯号输入
  --之后用可变电阻来扩展LED的点亮
*/
int sensor = A0;  // 设定sersor = A0的意思
int sensorRead = 0; //先设定serson读到的值为0
int newdata = 0; // 变化后的数值


void setup() {
  Serial.begin(9600); //打开串口，速率为 96000 bps
}

void loop() {
  sensorRead = analogRead(sensor); // 使用A0的引脚读取类比信号
  newdata = map(sensorRead, 0, 1023, 0,255); // 将 0~1023  映射 0~255
  Serial.println(sensorRead);  // 换行 输出
  analogWrite(3,newdata);  // 将模拟值输入到引脚（让灯随着模拟值的变化而变化）
  delay(200);
}
```



<img src="https://www.hualigs.cn/image/634a96132cacc.jpg" style="zoom:50%;" />

### ② 模拟信号控制舵机 —— 实例

```c
#include <Servo.h>  // 导入舵机函数库

Servo myservo;  // 定义舵机名称
int sensor = 0; // 电位器输入的模拟信号
int angle = 0;

void setup() {
  myservo.attach(9);  // 设置舵机的控制位的引脚是9号引脚。

}

void loop() {
  sensor = analogRead(A0);  // 从A0读取模拟信号
  angle = map(sensor, 0, 1023, 0, 180); // 映射
  myservo.write(angle);                  // 舵机转到90度
  delay(15);                           // 延迟
}

```



<img src="https://s1.xptou.com/2022/10/16/634b5d7a48de5.png" style="zoom: 67%;" />







