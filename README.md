# ESP32 入门笔记


[toc]

教程：[Bilibili](https://www.bilibili.com/video/BV1QL411673n/?spm_id_from=333.337.top_right_bar_window_default_collection.content.click&vd_source=2b2e11f865a586a3d07499be6cc466af)

官网&文档：[[ESP32官网]](https://www.espressif.com/zh-hans/products/socs/esp32)  [[PDF]](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32e_esp32-wroom-32ue_datasheet_cn.pdf)

## 0. ESP32 简介

`ESP32` 是一款由乐鑫科技（`Espressif`）推出的低成本、低功耗、高级程度的微控制器，采用了双核 `CPU` 架构，主频高达 `240MHz`，并且有 `Wi-Fi` 和 蓝牙通信功能，广泛应用于物联网、智能家居、机器人等领域。

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202305301022058.png" alt="image-20230530102055658" style="zoom: 80%;" />

### ESP32 特性

`ESP32` 支持基于 `ESP-IDF（物联网开发框架）` 的 `C/C++` 编程，也支持 `Arduino` 编程。

|     硬件规格     |                             特性                             |
| :--------------: | :----------------------------------------------------------: |
| 处理器（`CPU` ） | `Tensilica Xtensa` 双核 `32` 位 `LX6` 微处理器，支持高达 `240MHz` 时钟频率 |
|    片上存储器    | `ROM:448KB`（用于引导和核心功能）/  `SRAM:520 KB`（用于数据和指令）/ `RTC SRAM:16KB`（用于深度睡眠模式） |
|                  |                                                              |
|                  |                                                              |
|     `Wi-Fi`      |                                                              |
|       蓝牙       |                                                              |
|       外设       |                                                              |

