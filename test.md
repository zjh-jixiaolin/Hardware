# 信步资料总结

[TOC]

戴尔G3 3590：HDMI 2.0

产品资料：192.168.1.199

测试部新人资料：\\192.168.10.3\Public\【工程测试部新人必学资料】

## 0. VGA、HDMI、DP接口的概念

### VGA

`VGA(Video Graphics Array)` 视频图形阵列由 `IBM` 于 `1987` 提出的一个使用[模拟信号](https://baike.baidu.com/item/模拟信号/706796?fromModule=lemma_inlink)的电脑显示标准。

`VGA` 接口是最普及的 **模拟接口**，计算机内部以 **数字** 方式生成显示图像信息，被显卡中的 **数字/模拟** 转换器转变为 `R、G、B` 三原色信号和行、场同步信号，信号通过电缆传输到显示设备上。

- 分辨率：640 * 480 ~ 2560 * 1600
- 帧率：1920*1080 60Hz（此分辨率最高支持的帧率）
- VGA接口是 模拟信号 传输，所以显示器的分辨率越高，图像就越模糊，且信号易受干扰
- VGA 无法传输声音

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
  - 帧率：1920 * 1080 `240Hz`（最高）/ 2560 * 1440  `144z`（最高）/ 3840 * 2160 `60Hz`（最高） 

- 带宽：`21.6 Gbps`

#### DP 1.4（支持动态HDR）

- 分辨率：1920 * 1080  ~ 7680*4320（8K）
- 帧率：1920 * 1080 `240Hz`（最高） / 2560 * 1440 `240Hz`（最高）/ 3840 * 2160 `120Hz`（最高）/  7680 * 4320 `60Hz`（最高）

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

<img src="https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230705085827225.png" alt="image-20230705085827225"  />



## 1. 机械硬盘、固态硬盘的概念与分类

参考链接①：https://hovertree.com/h/bjaf/ovy7u369.htm

参考链接②：https://baijiahao.baidu.com/s?id=1758812682458870950&wfr=spider&for=pc

参考链接③：https://zhuanlan.zhihu.com/p/466434191

参考链接④：https://zhuanlan.zhihu.com/p/491944861

### 机械硬盘 — 概念

机械硬盘（`HDD`）是一种利用 **旋转磁盘** 和 **读写头** 来存储和访问数据的存储设备。主要由 **磁盘、主轴、磁头（读写头）、电机和控制电路** 等组成，磁盘通常是一种 **铝合金** 或 **玻璃材质** 的圆盘，表面涂有磁性材料。磁头（读写头）则可在磁盘上读写数据，当马达电机旋转磁盘时，读写头可以在磁盘的不同位置读取和写入数据。

![image-20230705102139212.png](https://github.com/zjh-jixiaolin/map_strong/blob/main/image-20230705102139212.png?raw=true)

### 固态硬盘 — 概念

固态硬盘（`SSD`）是一种使用 **闪存芯片** （通常为 `NAND` 芯片） 来存储数据的高速、低功耗、无噪音、可靠性高的存储设备。主要由 **主控芯片、闪存颗粒、缓存单元** 组成，主控芯片的核心部件也是技术最高的部件。

许多制造商只负责制造 `SSD` 和 `NAND` 存储物理部分，但控制部分需要额外的芯片。不同的 `SSD ` 内置主控芯片 `FTL` 算法不同，数据压缩/解压算法不同，控制通道数也不同。`SSD` 主控芯片将直接影响其性。

- `SSD` **主控**芯片：`SSD`主控本身就是一个 `CPU`，负责**控制闪存**的**识别**和**读写**，`SSD` 主控制芯片几乎完成了固态磁盘中涉及的所有控制指令操作和数据读写操作。
- `SSD` **缓存**芯片：缓存就是 `CPU` 使用的**内存** `DRAM`，数据现在存储在这里，然后写入闪存颗粒，以缓冲数据交换。
- `SSD` 闪存芯片：实际上是 **数据存储** 的最终位置，从主控安排接受相应的数据并长期保存，根据不同的架构分为：`SLC` ，`MLC` ，`TLC` ，`QLC` 等。

![image-20230706173750012](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230706173750012.png)

### 机械硬盘 — 分类

#### 尺寸

机械硬盘的尺寸通常有 `3.5`英寸 和 `2.5`英寸两种，其中 `3.5`英寸硬盘常用于 **台式机**，`2.5` 英寸硬盘用于**笔记本电脑**和便携式设备。

![image-20230706182901498](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230706182901498.png)

#### 转速

机械硬盘的转速通常有 `5400 RPM` 、 `7200 RPM`、`10000 RPM`、`15000 RPM`，转速越高，读写速度和响应时间越快。

- 高转速的缺点：产生 **大噪音** 和 **热量**。

#### 接口类型

机械硬盘的接口类型有：`SATA`、`SCSI`、`SAS`、`IDE`，其中 `SATA` 接口是目前最常用的机械硬盘接口类型。`SCSI` 是一种高端机械硬盘接口类型，通常用于服务器等高性能场景，由于安装复杂很少使用。 `SAS` 是一种新型的机械硬盘接口，它是 `SATA` 和 `SCSI` 的结合体，它提供了高速数据传输和可靠性，同时支持热插拔，因此被广泛应用与企业级服务器和存储系统等一些场景。 `IDE`接口是一种老旧的机械硬盘接口类型，已经很少使用。

![image-20230708112410592](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230708112410592.png)

#### 缓存大小

机械硬盘通常会配备一定大小的缓存，缓存越**大**，读写速度也**越快**。

#### 存储密度

机械硬盘的存储密度也是一个重要的指标，指的是硬盘每平方英寸的存储容量，存储密度越大，硬盘容量也越大。



### 固态硬盘 — 分类

#### 接口协议类型

`SSD` 固态硬盘的 接口协议类型主要有 `SATA` 、`PCIe` 、`NVMe` 等几种，其中`NVMe`（非易失性存储器）是一种基于 `PCIe ` **总线**的高速接口，读写速度比 `SATA` 和 `PCIe AHCI` 接口更快。**现主流的M.2接口 SSD硬盘都为 NVMe 接口协议**

>`PCIe AHCI`接口指的是基于 `PCIe` 总线的 `AHCI`（高级主机控制器接口）协议。`AHCI` 是一种传输界面技术，用于连接计算机主板上的 `SATA` 接口，可以实现高速数据传输、热插拔和NCQ（原生指令排序）等功能。

![image-20230710154325487](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230710154325487.png)

#### SSD 格式类型

`SSD` 固态硬盘的格式类型包括 `2.5` 英寸 `SSD（SATA）`、`M.2` 、`U.2`、`AIC（PCIe卡式SSD）`  等几种，其中 `M.2` 是一种目前较为常用的格式类型，体积小（节省机箱空间）、可靠性高、速度快（采用 PCIe接口数据传输）。

- `2.5`英寸`SSD（SATA）`：一般用于 **笔记本、台式电脑、服务器、NAS** 设备上。
- `M.2 SSD`：一般用于 **笔记本、超极本（轻薄本）、一体机** 设备上。
- `U.2 SSD`：一种基于 `PCIe` 接口的高速固态硬盘，通常用于**服务器**、**工作站**等高性能计算设备中。U.2具有更高的传输速度和更高的容量，可用于**存储大量数据**、**高速数据库**、**虚拟化**等应用场景。
- `AIC（PCIe卡式SSD）`：`AIC` 是一种通过插入 `PCIe` 插槽来扩展系统存储的卡式设备，通常采用 `PCIe` 接口，具有高速传输、低延迟等优势。`AIC` 通常用于**高性能计算**、**数据中心**等场景中。

![image-20230710152942713](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230710152942713.png)

#### 存储芯片类型

`SSD` 的存储芯片类型（闪存存储技术）主要包括 `SLC`、`MLC`、`TLC` 和 `QLC` 等几种，下方解释常用的几种：

- `SLC`（单层存储单元）每个 `cell` **存储单元**只存储 **一个** 比特的数据，`SLC` 颗粒具有**高速**和**长寿命**的优点，但成本较高，一般多用于企业级高端产品，如**高端存储设备**、**嵌入式系统**和**工业控制**等。—— 理论擦写 `10` 万次以上。
- `MLC` （双层存储单元）每个 `cell` **存储单元**可存储 **两个** 比特的数据，`MLC` 颗粒**速度较快**，**寿命较长**，相对于 `SLC颗粒`，`MLC` 可以少用**一半**的颗粒写入同样的数据，因此成本更低，多用于家用高端产品，如 **高端笔记本电脑**、**智能手机**、**数码相机**等 。—— 理论擦写 `3000 - 5000` 次左右。
- `TLC`（三层存储单元）每个 `cell` **存储单元**可存储 **三个** 比特的数据，`TLC`颗粒 **速度较慢**，**寿命较短**，相对于 `MLC`颗粒，`TLC`可以少用**三分之二**的颗粒写入同样的数据，因此成本较低，是目前市面上主流闪存颗粒，如**三星970 EVO**、**西部数据黑盘**、**海康威视C2000 Pro**—— 理论擦写 `1000 - 3000` 次左右。

![image-20230710175802331](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230710175802331.png)

#### 写入寿命:

`SSD`的写入寿命是指它可以写入的数据量，通常用 `TBW`（`Terabytes Written`）来衡量，写入寿命越高，寿命越长。



### SATA 和 M.2 的性能

#### SATA 接口分类（SATA 1.0、SATA 2.0、SATA 3.0）

`SATA` 是一种常用于计算机存储设备的接口标准，它有三种常见的分类：

- `SATA 1.0`：`SATA 1.0` 是第一代 `SATA` 接口标准，于 `2003` 年发布。它提供了最高传输速率为 `1.5 Gbps`（即 `150 MB/s`）
- `SATA 2.0`：`SATA 2.0` 是第二代 `SATA` 接口标准，于 `2004` 年发布。它提供了最高传输速率为 `3 Gbps`（即 `300 MB/s`）
- `SATA 3.0`：`SATA 3.0` 是第三代 `SATA` 接口标准，于 `2009` 年发布。它提供了最高传输速率为 `6 Gbps`（即 `600 MB/s`），并与 `SATA 1.0` 和 `SATA 2.0` 相互兼容。

![image-20230711092827491](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711092827491.png)

>**速率计算：**
>
>​	`SATA 3.0` 最高传输速率为 `6 Gbps`（千兆比特每秒）转换为 `Mbps`（兆比特每秒），则为 `6 * 1000 = 6000 Mbps`
>
>由于 **1 字节等于8个比特**，即 `6000 Mbps / 8 = 750 MB/s`，因此 `SATA 3.0`理论值可达到 `750 MB/s`。
>
>**总结：**
>
>​	`SATA 1.0` 和 `SATA 2.0` 接口常用于**机械硬盘**（`HDD`） 和**光盘驱动器**（`CD/DVD/Blu-ray`等），`SATA 3.0` 接口常用于 **固态硬盘**（`SSD`）与 **机械硬盘**（`HHD`），许多现代的固态硬盘都支持 `SATA 3.0` 接口，因此 `SATA 3.0` 接口也被认为是现代固态硬盘的标准接口之一。
>
>​	`SATA 3.0`理论传输速率为 `750 MB/s`，但由于实际过程中需考虑协议开销和数据传输等因素，实际 `SATA 3.0`接口能达到最大传输数量为 `550 MB/s ~ 600 MB/s`。

#### M.2 接口分类（B Key 、M Key、B&M Key ）

`M.2 SSD` 常见的类型有三种：`2230`、`2240`、`2280`，通常用 `Type xxyy`的方式表示，`xx`表示 **宽度**，`yy` 表示长度，单位为 **毫米**。举个例子 `Type 2230`表示其 **宽度22mm，长度30mm**;

![image-20230711101529296](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711101529296.png)

`M.2` 接口规范定义了多种不同的 **键位（Key）** 类型，以支持不同协议和功能，按照接口类型，可分为 `B Key` 和 `M Key`：

- `B Key` ：支持 `SATA` 协议和 `PCIe * 2`通道，常用于连接 `SATA SSD（M.2 SATA协议 SSD）` ；

- `M Key`：支持`PCIe ×4` 通道和 `SATA` 协议，通常用于连接 `PCIe NVMe SSD`；

![image-20230711104235781](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711104235781.png)

`B Key` 的防呆键位于插槽的**左方**，`M Key`则在**右方**。两种类型的插槽其短边接脚数量有所差异，具体如下：

- `B Key` 左侧有 `6` 个触点，`M Key` 右侧有 `5` 个触点。

一开始，`B Key`只能在`B Key`的插槽接口中，`M Key`只能在`M Key`的插槽接口中，随着 `M Key` 接口的普及，越来越多电脑主板只`M Key` 接口，`B Key` 的 `SSD` 根本插不上去，于是厂商们又设计了一个 `B & M Key `接口的 `SSD`。

- `B & M Key`：支持 `SATA` 协议和 `PCIe * 2`通道，由于 `M Key`的普及，`B & M Key`只是弥补了`M Key`不支持 `B Key`的不足，因此通常用于连接`SATA SSD（M.2 SATA协议 SSD）`；

>注意：`SSD` 金手指有 `B Key` 、`M Key`、`B&M Key` 三种，但**主板**上的 `M.2` 接口只有 `B Key` 和 `M Key` 两种。

![image-20230711104437234](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711104437234.png)

![image-20230711105103035](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711105103035.png)

![image-20230711105229991](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711105229991.png)

#### M.2 SSD 协议

按照[固态硬盘接口协议类型](####接口协议类型)分类，可以把硬盘分为 走`SATA` 通道的`SSD` 和 走`PCIe` 通道的`SSD`。 

![image-20230711113409489](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711113409489.png)

这里只讨论 `M.2`接口的 `SSD`，`SSD`即使是 `M.2`接口的，也分走`SATA`通道和 `PCIe`通道。

![image-20230711114220712](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711114220712.png)

首先要知道，`NVMe`和 `AHCI`是硬盘的接口协议。`NVMe`协议是专门为`PCIe`通道的固态硬盘设计的。而`ACHI`是专门为 `SATA`通道的硬盘设计的，现如今很多人把 `ACHI`协议叫做`SATA` 协议，因此下方距离就用 `SATA`协议这个名称。

`M.2`接口有两种，一种是走`SATA（ACHI）`协议的，另外一种是走 `PCIe（NVMe）`的。

- 走 `SATA`的**速度**跟传统 `SATA`接口没区别，就是接口变为 `M.2`，具体如下：

![image-20230711134700199](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711134700199.png)

- 走 `PCIe` 的就是常说的 `NVMe` ，**性能** 比 `SATA` 强了很多倍。

![image-20230711134952818](https://raw.githubusercontent.com/zjh-jixiaolin/map_strong/main/image-20230711134952818.png)

>**总结：**
>
>根据上方对 `M.2`接口型号的了解，得出如下：
>
>- `B Key` 支持 `SATA`协议 和 `PCIe * 2`通道
>- `M Key` 支持 `SATA` 协议 和  `PCIe * 4`通道
>- `B & M Key` 支持 `SATA`协议 和 `PCIe * 2`通道
>
>在市面上可购买的 `SSD` 中，绝大多数的 `B & M Key`的 `SSD` 都是不支持 `NVMe`协议的，只支持 `SATA` 协议。而 `M Key`的 `SSD` 都支持 `NVMe`协议（对于 `B Key`目前已经被淘汰）；



























