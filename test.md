# 信步资料总结

[TOC]

戴尔G3 3590：`HDMI 2.0`

产品资料：`192.168.1.199`

测试部新人资料：`192.168.10.3/Public`

## 0. VGA、HDMI、DP接口的概念

### VGA

`VGA(Video Graphics Array)` 视频图形阵列由 `IBM` 于 `1987` 提出的一个使用[模拟信号](https://baike.baidu.com/item/模拟信号/706796?fromModule=lemma_inlink)的电脑显示标准。

`VGA` 接口是最普及的 **模拟接口**，计算机内部以 **数字** 方式生成显示图像信息，被显卡中的 **数字/模拟** 转换器转变为 `R、G、B` 三原色信号和行、场同步信号，信号通过电缆传输到显示设备上。

- 分辨率：640 * 480 ~ 2560 * 1600
- 帧率：1920*1080 60Hz（此分辨率最高支持的帧率，高于以上会模糊）

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230704151734926.png" alt="image-20230704151734926" style="zoom:67%;" />

### HDMI

`HDMI` 高清晰度多媒体接口，能高品质传输**未经压缩**的音频信号及视频信号。`HDMI` 是首个在单数字接口中集成不压缩的高清晰度视频、多声道音频和智能格式与命令数据的数字接口。（下方数据为 `8bit 100%sRGB`下能支持的数据）

#### HDMI 1.4

- 分辨率：1920 * 1080 ~ 3840 * 2160（4K）

- 帧率：1920 * 1080 `144Hz`（最高）/ 2560 * 1440  `75Hz`（最高）/ 3840 * 2160 `30Hz`（最高）

- 带宽：`10.2 Gbps`

#### HDMI 2.0

  - 分辨率：1920 * 1080 ~ 3840 * 2160（4K）
  - 帧率：1920 * 1080 `240Hz`（最高）/ 2560 * 1440  `144Hz`（最高）/ 3840 * 2160 `60Hz`（最高） 
  - 带宽：`18 Gbps` 

#### HDMI 2.1（支持动态HDR）

- 分辨率：1920 * 1080  ~ 10240×4320（10K）
- 帧率：1920 * 1080 `240Hz`（最高）/ 2560 * 1440  `240Hz`（最高）/ 3840 * 2160 `144Hz`（最高）/  7680 * 4320 `30Hz`（最高）
- 带宽：`48 Gbps`

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230704151823953.png" alt="image-20230704151823953" style="zoom:67%;" />



### DP

`DP` 接口即 `DisplayPort` 接口，是一种用于数字视频和音频传输的计算机显示接口标准。`DP` 接口在技术上支持**高分辨率、高刷新率和深色位**的视频传输，同时还支持**多通道音频传输**，包括**高质量**的无压缩音频和多声道音频。

#### DP 1.2

- 分辨率：1920 * 1080 ~ 3840 * 2160（4K）
  - 帧率：1920 * 1080 `240Hz`（最高）/ 2560 * 1440  `165Hz`（最高）/ 3840 * 2160 `75Hz`（最高） 

- 带宽：`21.6 Gbps`

#### DP 1.4（支持动态HDR）

- 分辨率：1920 * 1080  ~ 7680*4320（8K）
- 帧率：1920 * 1080 `240Hz`（最高） / 2-560 * 1440 `240Hz`（最高）/ 3840 * 2160 `240Hz`（最高）/  7680 * 4320 `60Hz`（最高）

- 带宽：`32.4 Gbps`

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230704170555580.png" alt="image-20230704170555580" style="zoom:67%;" />

>**HDMI 带宽计算：**
>
>​	例如，想知道 `HDMI 1.4` 是否支持 `4k 60Hz` 的屏幕。`HDMI 1.4` 最高支持带宽为 `10.2 Gbps`，而 `4K 60Hz`屏幕所需的带宽为 `3840x2160(分辨率)x8(bpc)x3(像素倍数)x60(刷新率)/0.8(hdmi采用的8b/10b编码)/1024的3次 = 13.9046Gbps`，则 `HDMI 1.4` 目前所能传输的**最大峰值带宽**是无法支持 `4K 60Hz` 的屏幕。

### HDMI、DP 输出参数表

#### HDMI 参数表

![image-20230705085852726](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230705085852726.png)

![image-20230705090132534](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230705090132534.png)

#### DP 参数表

![image-20230705085827225](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230705085827225.png)






