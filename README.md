# ESP32 入门笔记


[toc]

教程：[Bilibili](https://www.bilibili.com/video/BV1QL411673n/?spm_id_from=333.337.top_right_bar_window_default_collection.content.click&vd_source=2b2e11f865a586a3d07499be6cc466af)

官网&文档：[[ESP32官网]](https://www.espressif.com/zh-hans/products/socs/esp32)  [[PDF]](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32e_esp32-wroom-32ue_datasheet_cn.pdf)

仿真平台：[Wokwi](https://wokwi.com)

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

### 基础程序结构

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

### 注释

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

### 数据类型 - 变量 

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
  
  uint8_t my_age;
  long my_money = 1000000;
  float my_height = 1.88;
  ```

  



#### 数据类型

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

#### 数据输出格式

| 输出格式 | 作用 |
| :------: | :--: |
|          |      |
|          |      |
|          |      |



#### 



























