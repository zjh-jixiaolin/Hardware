# ESP32 入门笔记


[toc]

教程：[Bilibili](https://www.bilibili.com/video/BV1QL411673n/?spm_id_from=333.337.top_right_bar_window_default_collection.content.click&vd_source=2b2e11f865a586a3d07499be6cc466af)

官网&文档：[[ESP32官网]](https://www.espressif.com/zh-hans/products/socs/esp32)  [[PDF]](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32e_esp32-wroom-32ue_datasheet_cn.pdf)

硬件仿真平台：[Wokwi](https://wokwi.com)

在线交互电路平台：[Falstad](https://www.falstad.com/circuit/circuitjs.html?ctz=CQAgjCAMB0l3BWcMBMcUHYMGZIA4UA2ATmIxAUgoqoQFMBaMMAKADcQM8AWEQ-TjxDc4UMSOpUp0BCwDu4NFRFUwSvgMgswhFMgx6Vi0Ub0ATOgDMAhgFcANgBcG9umfBjpkVgCcQxfmFRMEgJI1U4eXAQ3n48QVjNKJjlYMgDIKlk9Tjo0I14rQBnBMz-FHjwjxt7Iroo4gqygNSsoA)

## 0. ESP32 简介

`ESP32` 是一款由乐鑫科技（`Espressif`）推出的低成本、低功耗、高级程度的微控制器，采用了双核 `CPU` 架构，主频高达 `240MHz`，并且有 `Wi-Fi` 和 蓝牙通信功能，广泛应用于物联网、智能家居、机器人等领域。

|         ESP32         |                           配置                            |
| :-------------------: | :-------------------------------------------------------: |
| `Flash`（闪存存储器） |           `4MB`，用于存储程序代码、数据和文件等           |
|    `SRAM`（内存）     |          `520KB`，用于存储程序和数据的运行时内存          |
| 时钟速度（运行速度）  | `240MHz`，ESP32芯片的主频，用于控制处理器和外设的运行速度 |

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301022058.png" alt="image-20230530102055658" style="zoom: 80%;" />

### ESP32 特性

`ESP32` 支持基于 `ESP-IDF（物联网开发框架）` 的 `C/C++` 编程，也支持 `Arduino` 编程。

|                   硬件规格                   |                             特性                             |
| :------------------------------------------: | :----------------------------------------------------------: |
|               处理器（`CPU` ）               | `Tensilica Xtensa`  **双核** `32` 位 `LX6` 微处理器，支持高达 `240MHz` 时钟频率 |
|                  片上存储器                  | `ROM:448KB`（用于引导和核心功能）/  `SRAM:520 KB`（用于数据和指令）/ `RTC SRAM:16KB`（用于深度睡眠模式） |
|                   `Wi-Fi`                    | `HT40` 数据速率为 `150.0 Mbps` / 工作信道中心频率范围：`2412 ~ 2484MHz` |
|                     蓝牙                     | 蓝牙 `V4.2 BR/EDR` 和蓝牙 `LE` 标准（经典蓝牙 和 [BLE](https://so.csdn.net/so/search?q=BLE&spm=1001.2101.3001.7020) 低功耗蓝牙） |
|                     外设                     | `SD`卡、`UART`、`SPI`、`SDIO`、`I2C`、`LED PWM`、电机`PWM`、`I2S`、`IR`、脉冲计数器、`GPIO`、电容式触摸传感器、`ADC`、`DAC`、`TWAI`(兼容ISO 11898-1.即 CAN 规范 2.0) |
|                   内置按钮                   |          `RESET`（重启） 和 `BOOT`（烧录模式） 按钮          |
|                  内置`LED`                   |      内置红色`LED`通电即亮；内置蓝色`LED`连接到`GPIO2`;      |
| `USB` 到 `UART` 桥（计算机与嵌入式设备通信） | `cp210x`芯片，负责`开发板`和`电脑`进行通信。驱动下载：[链接](https://www.qutaojiao.com/997.html) |

![image-20230530114918997](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301149283.png)



<br />



## 1. 代码基础 — 进阶

### 1.1 基础程序结构

---

```c
// 头文件 ——> Arduino工具箱
#include <Arduino.h>  

// 初始化函数（只执行一次，一般用于初始化变量和引脚模式）
void setup() {

}

// 循环执行函数（重复执行，Arduino的主体）
void loop() {

}

// 上方两个函数为Arduino固定函数，可理解为代码运行入库，每次开机都从setup开始运行。
```

### 1.2 注释

---

```c
# 单行 注释使用 
// 注释主体

# 多行 注释使用 
/* 
注释主体1
注释主体2
*/
```

### 1.3 数据类型 - 变量 

---

当我们需要芯片存储一些可能会变化的值时，这时就需要使用变量。

#### 变量声明（2种写法）

数据类型 变量名；

数据类型 变量名 = 赋值；

![image-20230530120534125](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301205643.png)

#### 变量赋值

变量名 = 赋值；

![image-20230530120737068](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301213713.png)

#### 变量命名要求

- 命名变量时建议使用 **小写字母 + 下划线命名。**

- 变量名的 **第一个** 字符必须是 **字母、下划线（_）。**

  ```c
  #include <Arduino.h>  
  
  // 展示命名
  uint8_t my_age;
  long my_money = 1000000;
  float my_height = 1.88;
  ```

  



### 1.4 数据类型

---

使用变量时，需要根据存储的数据范围，选择不同的数据类型。

`32` 位芯片中，数据类型方范围如下：

| 数据类型（有符号整形） |                      范围                       |
| :--------------------: | :---------------------------------------------: |
|         `chat`         |       `-128 ~ 127` ，内存占用 `1`  个字节       |
|        `short`         |      `-32768 ~ 32767`，内存占用 `2` 个字节      |
|         `int`          | `-2147483648 ~ 2147483647`，内存占用 `4` 个字节 |

|    数据类型（无符号整形）     |       范围       |
| :---------------------------: | :--------------: |
|  `unsigned char` / `uint8_t`  |    `0 ~ 256`     |
| `unsigned short` / `uint16_t` |   `0 ~ 65536`    |
|  `unsigned int` / `uint32_t`  | `0 ~ 4294967295` |

| 数据类型（小数） |                             范围                             |
| :--------------: | :----------------------------------------------------------: |
|     `float`      | 单精度浮点数，内存占 `4` 个字节，有效数字 `8` 位，表示范围 `-3.40E+38~3.40E+38`。 `3.40E+38=3.4×10`的`38`次方 |
|     `double`     | 双精度浮点数，内存占 ` 8` 个字节，有效数字 `16` 位，表示范围是 `-1.79E+ 308~-1.79E+308` |

>`float` 与 `double` 数据类型两者处理速度不同，`CPU`处理`float`的速度比处理`double`快。`double`的精度高，`double`消耗内存是`float`的两倍。
>
>根据实际需要装的数据大小、类型进行申请即可，例如：
>
>纸币面额： `1、5、10、20、50、100` 可以使用 `uint8_t`
>
>你的账户余额：`uint32_t `
>
>室外温度：`-20.1 ~ 40.5` 可以使用 `float`

<br />



#### 数据输出格式


| 输出格式 |     作用     |
| :------: | :----------: |
|   `%d`   |     整形     |
|   `%s`   |    字符串    |
|   `%f`   | 单精度浮点型 |

#### 案例：

```c
#include <Arduino.h>  

uint8_t my_age;
long my_money = 1000000;
float my_height = 1.88;

void setup() {
    //初始化串口，波特率位9600
    Serial.begin(9600);
    //打印“setup”字符到电脑，\n为换行符
    my_age = 19;
    Serial.printf("setup\n");
    Serial.printf("age = %d\n",my_age );
    Serial.printf("money = %d\n",my_money );
    Serial.printf("height = %.2f\n",my_height );
}

void loop() {

}
----------------------------------------------------------
# 输出结果
setup
age = 19
money = 1000000
height = 1.88
```



<br />



### 1.5 数据类型 — 常量与宏定义

---

需要芯片帮我们存储永远**固定不变**的值，这时候需使用 **常量** 或 **宏定义**。

#### 常量

![image-20230530163816486](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301725370.png)

#### 宏定义

![image-20230530163959693](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301725828.png)

#### 案例

```c
#include <Arduino.h>  

// 常量
const float PI_NUM1 = 3.1415;

// 宏定义
#define PI_NUM2 3.1415926

void setup() {
    //初始化串口，波特率位9600
    Serial.begin(9600);
    Serial.printf("setup\n");
    // 常量
    Serial.printf("Const_PI = %f\n",PI_NUM1);
    // 宏定义
    Serial.printf("Define_PI = %f\n",PI_NUM2);

}

void loop() {

}
----------------------------------------------------------
# 输出结果setup
setup
Const_PI = 3.141500
Define_PI = 3.141593
```



<br />



### 1.6 运算符

---

在程序中如何使用算数来操作变量的运算？直接使用运算符即可。

| 运算符 |    作用     |
| :----: | :---------: |
|  `+`   |     加      |
|  `-`   |     减      |
|  `*`   |     乘      |
|  `/`   |    整除     |
|  `%`   |    取余     |
| `a ++` | `a = a + 1` |
| `a --` | `a = a - 1` |

#### 案例

```c
#include <Arduino.h>  

uint8_t a = 10;
uint8_t b = 5;
uint8_t c = 0;


void setup() {
    //初始化串口，波特率位9600
    Serial.begin(9600);
    // 加 
    c = a + b;
    Serial.printf("c = %d\n",c); // 结果：15

    // 减
    c = a - b;
    Serial.printf("c = %d\n",c); // 结果：5

    // 乘
    c = a * b;
    Serial.printf("c = %d\n",c); // 结果：50

    // 整除
    c = b / 2;
    Serial.printf("c = %d\n",c); // 结果：2

    // 取余
    c = b % 2;
    Serial.printf("c = %d\n",c); // 结果：1

    // a++
    a++;
    Serial.printf("a = %d\n",a); // 结果：11

    // b--
    b--;
    Serial.printf("b = %d\n",b); // 结果：4

}

void loop() {

}
```



<br />



### 1.7 控制循环 — 判断、循环

---

让芯片拥有逻辑执行能力，如当温度大于多少时，打印信息提醒。

#### If 判断

```c
// IF 判断
if(a > b){
    
} else{
    
}
```

#### While 循环

```c
// while 循环
while(a > b){
    
}
```

#### For 有限循环

```c
（初始值，判断是否满足条件，满足条件执行下方{}内容并进行++或--操作）
for(uint8_t i = 0； i < 24; i++)
{
    
}
```

#### 案例

```c
-------------------------------------------------- # if - 判断
#include <Arduino.h>  

// 温度
uint8_t temperature = 25;

void setup() {
    // 初始化串口，波特率位9600
    Serial.begin(9600);

}

void loop() {
    // if 判断语句
    if(temperature >= 30){
      Serial.printf("温度 = %d\n",temperature);
      Serial.printf("温度过高，请开空调\n");
      temperature = 25;
    } else{
      delay(1000);
      Serial.printf("温度 = %d\n",temperature);
      temperature ++;
    } 
}

-------------------------------------------------- # while - 循环
#include <Arduino.h>  

// 时间
uint8_t c_time = 0;

void setup() {
    //初始化串口，波特率位9600
    Serial.begin(9600);
    
    // while循环语句
    while (c_time <= 24)
    {
      if(c_time >= 24){
        c_time = 0;
      } 
      Serial.printf("现在是%d点\n",c_time);
      c_time ++; 
      delay(1000);  
    }
}

void loop() {

}
-------------------------------------------------- # for 有限循环
#include <Arduino.h>  

void setup() {
    // 初始化串口，波特率位9600
    Serial.begin(9600);
    // for 有限循环
    for (uint8_t ctime = 0; ctime < 24; ctime++)
    {
      Serial.printf("现在的时间是%d点\n",ctime);
      delay(100);
    }
    
}

void loop() {
    
}
```



<br />



### 1.8 函数

---

如何把某个块代码集合到一起，复用起来呢？

函数是一组完成某个功能的语句。

`setup` 和 `loop` 都是一个函数，我们也可定义自己的函数，这样程序结构才能更清晰，不同函数有不同的作用域。

#### 函数

```c
返回值类型 函数名(参数){
    函数实现;
    return 返回值;
}
```

#### 案例

```c
#include <Arduino.h>  

u_int32_t result;

u_int32_t add(u_int32_t x,u_int32_t y){
  uint32_t sum = x + y;
  return sum;
}

void setup() {
    // 初始化串口，波特率位9600
    Serial.begin(9600);
    result = add(3,4);
    Serial.printf("The Result is %d",result);

}

void loop() {
    
    
}
```



<br />



### 1.9 局部变量和全局变量

---

```c
#include <Arduino.h>  

// 全局变量
uint8_t a = 10;

void setup() {
    // 初始化串口，波特率位9600
    Serial.begin(9600);
    // 局部变量
    uint8_t a = 11;

}

void loop() {
    // 结论：改变局部变量的值不会影响全局变量的值。
    Serial.printf("a = %d\n",a); // 结果：10
}
```

>对于**局部变量**来说，它们的作用域仅限于定义它们的函数体内部使用。
>
>对于**全局变量**来说，它们的作用域在程序的任何位置都可以访问和修改全局变量。



<br />



## 2. LED 进阶

`LED` 应用场景：

![image-20230531001440674](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305310014231.png)

### 2.1 点灯原理：

`LED` 灯有着不同的封装，根据不同的应用场景，有的需要 **插件**`LED` 或 **贴片**`LED`，统称 **发光二极管**。

**插件`LED`** 灯珠 **长**引脚为 **正极**，**短**引脚为 **负极**。完全亮起电流是 `20mA` 左右。

**贴片`LED`** 完全亮起电流是 `5mA` 左右。

![image-20230531001858687](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305310019719.png)

`LED（发光二极管）` 两端存在 **电压差**，有一定的电流流过时会亮起。电流可以理解为水流，电压差可以理解为水位差，当两个点水位高度不一样时，水流会从高水位流向低水位。

![image-20230531002850834](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305311806450.png)

需注意：流过 `LED` 的电流需要在一定范围内，否则会烧坏 `LED`，一般小于 `20mA`，所以我们就需要**串联电阻分压**，那串联的电阻需要多大阻值？

#### 插件LED的限流电阻计算

![image-20230531012857458](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305310129518.png)

例如：供电电压为 `3.3V`，黄色插件`LED`。

根据公式 `V = I * R`，则 `R=(3.3 - 1.8) / 0.02`（`20mA`= `0.02A`）,则`R = 75Ω`

但很多时候你看到别人设计的电路中，`LED` 串联的电阻去到**几百欧**或**几千欧**都有，是设计错了吗？

实际上这是非常合理的，因为大多数电路中，`LED` 只是一个 提示灯，对亮度没有要求，反而希望把功耗降低，所以需要增大限流电阻来实现超低电流，像产品中的贴片LED去到 `0.5ma`也是能看清楚灯光的。

![image-20230531180649816](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305311806436.png)

#### 代码实现

```c
# 通过以下函数控制 IO引脚的输出电平高低
pinMode(引脚编号，输出/输入)
digitalWrite(引脚编号，电平高/底)
--------------------------------------------------
// 头文件
#include <Arduino.h>  

// 定义LED灯引脚为常量
#define PIN_LED 23

void setup() {
    // 初始化引脚为输出
    pinMode(PIN_LED,OUTPUT);
}

void loop() {
    // 设置为高电平(3.3V)，1s后设置为低电平(0V)，再1s后重复
    digitalWrite(PIN_LED,HIGH);
    delay(1000);
    digitalWrite(PIN_LED,LOW);
    delay(1000);
}
```



![image-20230531015625365](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305310156683.png)



<br />



## 3. 串口通信

### 3.1 串口

---

串行通讯端口，简称 **串口**，也称 `COM` 口。用于设备与设备、设备与电脑间的通信。

串行接口的数据是通过一条线一位位地顺序传送的。

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305311801824.png" alt="image-20230531180113470" style="zoom: 80%;" />![download_image](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305311802463.gif)

>串口模块：以太网、`WiFi`、蓝牙、`Zigbee`、`Lora`等串口模块。

#### 应用场景

与电脑上位机软件通信、与Android工控机通讯。

![image-20230531180348592](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305311803882.png)



### 3.2 串口波特率

---

波特率（`bandrate`），指串口通信的速率，也就是串口通信时每秒钟可传输多少个二进制位，如每秒钟可以传输 `9600` 个二进制（传输一个二进制位需要的时间是 `1/9600` 秒，也就是`104us（1s = 1000000us）`），波特率则为 `9600`。

串口的通信波特率不能随意设定，一般常见的波特率为 `9600` 或 `115200`（低端的单片机如 `51` 常用 `9600` ，高端的单片机如 `stm32` 和嵌入式`SOC` 一般用 `115200` ）。

![image-20230531193651626](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305311936681.png)

数据位：`1010 1010 —> 0xaa（10*16+10） —> 170`

即我们可以通过控制引脚按上面的高低电平。每 `104us` 改变一次，可完成一个字节的传输。但芯片已帮我们做好了这些操作，我们只需配置好波特率，填写数据即可

>`Arduino` 与 电脑进行通讯时，需要传输数据需满足 `2` 个条件：
>
>1. `Arduino` 将发送的数据转化为**二进制**，随后逐个发出。
>2. 确定 `Arduino` 与 电脑之间的波特率**相同**，才能进行通讯。







