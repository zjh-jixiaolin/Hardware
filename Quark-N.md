# &#x20;Quark-N Linux开发板 简介与烧录教程



[TOC]

**参考视频：**[link](https://www.bilibili.com/video/BV1bZ4y197R3/?spm_id_from=333.788.recommend_more_video.-1\&vd_source=2b2e11f865a586a3d07499be6cc466af)

**官方文档：**[link](https://wiki.seeedstudio.com/cn/Quantum-Mini-Linux-Development-Kit/)

**3D外壳文件：**[link](https://gitee.com/coolflyreg163/quark-n-3d)

## ① Quark-N 迷你开发板简介

​	[夸克迷你开发者套件](https://wiki.seeedstudio.com/cn/Quantum-Mini-Linux-Development-Kit/)是目前市面上最小的Linux卡片电脑，此套件搭载了`四核CPU的高度集成SOM核心板`，以及一个``多功能IO扩展底板``，使其可以在`40mm*35mm`的尺寸上运行`ARM-Linux`系统。您可以将它用于搭建 个人服务器、开发智能语音助手、智能机器人等。

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/img/202302220951637.png" alt="image-20230222095101515" style="zoom: 50%;" />

### 1、Quark-N SoM 核心板



​	开发板的核心是一块名为`Quark-N`的`SOM核心板（SOM：嵌入式控制核心模块）`，基于`Allwinner H3（全志H3）`，架构为`四核Cortex-A7 CPU + Mali400 MP2 GPU`，使用`6层高密度沉金`PCB设计，在`2*3`的空间集成了完整的`ARM-Linux系统（CPU、DDR、eMMC）    `；此外，`H3`上的绝大多数`GPIO`都通过 `M.2 Key-A`金手指接口引出。

>由于核心板Quark-N包含了eMMC，设计时可以不考虑SD卡，只需供电并添加一个用于终端交互的串口就能运行调试系统。

**Quark-N SoM 核心板技术规格：**

| 规格参数 |                             详情                             |
| :------: | :----------------------------------------------------------: |
|   CPU    |              Allwinner H3, 四核Cortex-A7 @ 1GHz              |
|   GPU    |                     ARM Mali400 MP2 GPU                      |
|   内存   |                       512MB LPDDR3 RAM                       |
|   存储   |                          16GB eMMC                           |
|   接口   |      以太网, SPI, I2C, UART, 可复用的GPIO, MIC, LINEOUT      |
|   GPIO   | 2.0mm间距26针式接头连接器，包括USB OTG，USB串口，I2C，UART，SPI，I2S，GPIO |
|   PCB    |                      6层高密度沉金设计                       |
| 工作温度 |                            0-80°C                            |
|   尺寸   |                          31mmx22mm                           |

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/img/202302221342757.png" alt="image-20230222134146779" style="zoom:67%;" />



### 2、Atom-N 扩展板



​	Atom-N，中文名为`原子`，是`Quark-N`的配套`扩展板`，通过`M.2`接口与Quark-N连接。Atom-N上搭载了`麦克风`、`MPU6050 IMU（加速度计和陀螺仪）`、`板载4个按键`、`1.35寸的IPS显示屏`、`Wi-Fi/蓝牙模块`、`喇叭功放`、`两个USB-A接口`、以及`2.0mm排针的额外GPIO（包含I2C、SPI、UART等）`。

**Atom-N Carrier Board（载板）技术规格：**

| 规格参数 |                             详情                             |
| :------: | :----------------------------------------------------------: |
|   插槽   |                       Quark-N的m.2接口                       |
|   USB    |                   USB 2.0 x 2  Type-C x 1                    |
| 无线连接 | RTL8723BU<br>Wi-Fi: IEEE 802.11 b/g/n @2.4GHz <br>蓝牙: BT V2.1/ BT V3.0/ BT V4.0 |
| 板载外设 | 麦克风x1<br/>MPU6050运动传感器(陀螺仪、加速度传感器)x1<br />按键x4(GPIO-KEY、Uboot、Recovery、Reset)<br />TFT显示屏x1 |
| 外部存储 |                        Micro SD卡插槽                        |
|   尺寸   |                          40mm*35mm                           |

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/img/202302221645140.png" alt="image-20230222164516893"  />

![image-20230223101250944](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202302261836966.png)



## ② 软件使用和烧录步骤



### 1、软件准备



① **系统镜像：** [Quark-N 迷你开发者套件 最新系统镜像](https://files.seeedstudio.com/wiki/Quantum-Mini-Linux-Dev-Kit/quark-n-21-1-11.zip)

② **格式化SD卡软件：** [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/sd-memory-card-formatter-for-windows-download/)

③ **烧录软件：** [Etcher]( )



### 2、烧录步骤



读卡器插入联网的计算机后：

① 使用 SD 协会的[SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/sd-memory-card-formatter-for-windows-download/) 格式化 microSD 卡（默认格式化即可）。

② 下载   [Quark-N 迷你开发者套件 最新系统镜像](https://files.seeedstudio.com/wiki/Quantum-Mini-Linux-Dev-Kit/quark-n-21-1-11.zip) 保存到自己知道的位置（Zip文件不用解压）。

③ 使用  [Etcher](https://www.balena.io/etcher) 将 [Quark-N 迷你开发者套件 最新系统镜像](https://files.seeedstudio.com/wiki/Quantum-Mini-Linux-Dev-Kit/quark-n-21-1-11.zip) 写入 microSD 卡（运行Etcher软件`右击管理员运行`）

- 第一，选择`Flash from file（从文件烧录）` 将 [Quark-N 迷你开发者套件 最新系统镜像](https://files.seeedstudio.com/wiki/Quantum-Mini-Linux-Dev-Kit/quark-n-21-1-11.zip)  进行写入 (直接选择zip文件)。
- 第二，选择 `Select drive（选择目标磁盘）` 选择插入的 `SD卡`。
- 第三，选择 `Flash（现在烧录）` 进行写入。
  

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202302231448991.png" alt="image-20230223144811722" style="zoom: 80%;" />

烧录成功效果：

![image-20230223145114233](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/202302231451013.png)











