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

![image-20230530114918997](C:/Users/18279/AppData/Roaming/Typora/typora-user-images/image-20230530114918997.png)



<br />



## 1. C语言代码基础




























