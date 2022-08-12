# GR5515 Starter Kit

## 介绍

GR5515 Starter Kit（以下简称GR5515 SK）套件是基于GR551x芯片（支持Bluetooth 5.1）设计的开发平台，包含Starter Kit开发板（以下简称GR5515 SK板）、原理图和使用指南。用户可以在该平台上熟悉GR551x开发工具以及快速搭建自己的产品原型并验证相关功能。

开发板外观如下图所示：

![开发板外观](https://docs.goodix.com/zh/docimg/gr5515_starter_kit_user_guide/190/gr5515_starter_kit_V1.7/zh//images/board.png)

开发板硬件布局如下图所示：

![开发板硬件布局上](https://docs.goodix.com/zh/docimg/gr5515_starter_kit_user_guide/190/gr5515_starter_kit_V1.7/zh//images/board_top.svg)

![开发板硬件布局下](https://docs.goodix.com/zh/docimg/gr5515_starter_kit_user_guide/190/gr5515_starter_kit_V1.7/zh//images/board_bot.svg)

开发板功能框图如下图所示：

![开发板硬件功能框图](https://docs.goodix.com/zh/docimg/gr5515_starter_kit_user_guide/190/gr5515_starter_kit_V1.7/zh//images/board_blo_dia.svg)


## 开发板功能
*  支持Bluetooth 5.1的单模低功耗蓝牙SoC
*  多功能按键和LED指示灯
*  支持Arduino模块插接接口，IO电压可以通过level shift灵活配置
*  支持调试功能的SEGGER J-Link OB
*  UART转USB接口
*  Micro USB接口连接PC
*  1.44寸TFT彩色显示屏
*  板上集成QSPI Flash

## 开发板规格

| 器件类别	 |              开发板              |
| ---------- | -------------------------------- |
| CPU	      | ARM Cortex-M4F (64Mhz)            |
| RAM	      | 256KB SRAM                       |
| Flash	      | 1MB片内Flash + 8MB SPI Flash     |
| GPIO	      | 39                               |
| I2C	      | 2                                |
| I2S	      | 2                                |
| UART       | 2                                |
| SPI	      | 2                                |
| PWM	      | 6                                |
| LED	      | 2                                |
| Debug 	    | J-Link、CDC UART                 |
| ADC	      | 5 channel 13bit                   |
| Display	    | 1.44寸TFT彩色                    |
| 按键	      | up、down、left、right、ok、power |


## 关键特性
|     组件名	      |                                          能力介绍                                           |
| --------------- | ------------------------------------------------------------------------------------------ |
| BLE 服务	      | 提供蓝牙 BLE 功能。                                                                         |
| 模组外设控制	    | 提供操作外设的能力。包括：I2C、I2S、ADC、UART、SPI、GPIO、PWM、FLASH等。                     |
| 分布式软总线	    | 在OpenHarmony分布式网络中，提供设备被发现、数据传输的能力。                                   |
| 设备安全绑定  	 | 提供在设备互联场景中，数据在设备之间的安全流转的能力。                                        |
| 基础加解密	      | 提供密钥管理、加解密等能力。                                                                 |
| 系统服务管理	    | 系统服务管理基于面向服务的架构，提供了OpenHarmony统一化的系统服务开发框架。                   |
| 启动引导	      | 提供系统服务的启动入口标识。在系统服务管理启动时，调用boostrap标识的入口函数，并启动系统服务。 |
| 基础库  	      | 提供公共基础库能力。包括：文件操作、KV存储管理等。                                            |
| XTS	           | 提供OpenHarmony生态认证测试套件的集合能力。                                                  |
| HDF	           | 提供OpenHarmony硬件配置驱动的能力。                                                         |
| Kconfig	         | 提供内核配置能力。                                                                          |


## 引脚定义

参考datasheet: [GR5515RGBD BGA68引脚定义](https://docs.goodix.com/zh/online/detail/gr551x_datasheet_brief/V1.7/7a02161fefa917a1b63f3d5a8338e879)

## 准备工作

在使用GR5515 SK板前，建议完成以下准备工作。

* 硬件准备

|  名称  |           描述           |
| ------ | ------------------------ |
| 数据线 | Micro-USB 2.0数据线      |
| 开发板 | GR5515 Starter Kit开发板 |


* 软件准备

|     名称     |                                       描述                                       |
| ----------- | ------------------------------------------------------------------------------- |
| 操作系统     | Windows 7操作系统及以上版本或者Ubuntu 18.04 LTS版本                        |
| 串口助手     | 可打印串口日志的串口终端                                                          |
| GProgrammer | 固件下载工具 [点击下载](https://product.goodix.com/zh/software_tool/gprogrammer) |

* 供电和连接


如下图所示是GR5515 Starter Kit开发板的装配图。

![GR5515 Starter Kit开发板装配图](https://docs.goodix.com/zh/docimg/gr5515_starter_kit_user_guide/190/gr5515_starter_kit_V1.7/zh//images/board_assem.svg)

在使用GR5515 SK板之前，需按以下步骤完成供电和连接设置：
1. 使用Micro USB 2.0线连接GR5515 SK板和PC。Mirco USB用于供电以及通过J-Link进行编程。
2. 将电源开关S6切换到右端，设置为SK板LDO供电；将S6切换到左端，设置为锂电池供电。
3. 将电源开关S5切换到右端ON的位置，打开电源。
4. D102开始闪烁表示PC开始检测J-Link接口。检测成功后，D102不再闪烁，变成常亮。
5. D102常亮后，打开PC的设备管理器，检查设备管理器 > 端口（COM和LPT）列表中是否有JLINK。若出现，则供电和连接设置完成，可对GR551x进行编程下载；若未正确检测到JLINK设备，则需要检查是否正确安装了JLINK驱动，可以尝试重新安装最新版本的JLINK驱动。

提示：
1. 安装GProgrammer会自动安装JLINK驱动，如果PC未安装JLINK驱动，请先下载安装[GProgrammer](https://product.goodix.com/zh/software_tool/gprogrammer)。

2. 开发板通过Mirco USB连接到PC后，会在设备管理器中“端口(COM和LPT)”列表中出现一个"JLink CDC UART Port(COMX)"串口号，串口助手需使用该串口号观察开机log信息。

## 搭建开发环境

### 系统要求

1. Windows 7操作系统及以上版本，用于固件烧录;
2. Ubuntu 18.04 LTS版本, 用于代码编译。

### 工具要求

1.	Ubuntu18.04系统安装：

`sudo apt-get install build-essential gcc g++ make zlib* libffi-dev e2fsprogs pkg-config flex bison perl bc openssl libssl-dev libelf-dev libc6-dev-amd64 binutils binutils-dev libdwarf-dev u-boot-tools mtd-utils gcc-arm-linux-gnueabi`

2.	Ubuntu18.04安装python3：

```
sudo apt-get install python3.8
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8
```

3.	Ubuntu18.04安装pip3：

```
sudo apt-get install python3-setuptools python3-pip -y
sudo pip3 install --upgrade pip
```

4. Ubuntu18.04安装hb工具：

`python3 -m pip install --user ohos-build`

5.	Ubuntu18.04 配置arm-none-eabi-gcc 10.2.1：

下载网站：https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads 

选择：gcc-arm-none-eabi-10-2020-q4-major-x86_64-linux.tar.bz2
下载解压到指定目录，然后通过bashrc配置环境变量。

### 搭建过程

参考 [环境搭建步骤](https://gitee.com/openharmony/device_soc_goodix/blob/master/README.md)


## 编译调试

参考 [编译调试步骤](https://gitee.com/openharmony/device_soc_goodix/blob/master/README.md)


## 首个示例

代码默认有1个示例：
1. [BLE应用示例](https://gitee.com/openharmony/vendor_goodix/tree/master/gr5515_sk_iotlink_demo)
2. [XTS测试示例](https://gitee.com/openharmony/vendor_goodix/tree/master/gr5515_sk_xts_demo)

## 参考资源

为了更好的使用GR5515 Starter Kit套件，建议参考下表相关资料。

|            名称            |                                                                                       描述                                                                                        |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GR5515 Starter Kit用户指南 | 介绍GR5515 Starter Kit套件使用方法：[《GR5515 Starter Kit用户指南》]( https://docs.goodix.com/zh/online/detail/gr5515_starter_kit_user_guide/V1.7/42a03ba92cad1d63afd9baa8bb8c37df) |
| GR551x开发者指南           | GR551x软硬件介绍、快速使用及资源总览：[《GR551x开发者指南》]( https://docs.goodix.com/zh/online/detail/gr551x_develop_guide/V2.3/27f7d503bcd7ad1d63fa5b316b3bde4f)                    |
| J-Link用户指南             | J-Link使用说明：www.segger.com/downloads/jlink/UM08001_JLink.pdf                                                                                                                   |
| GR5515-SK-BASIC-RevC      | GR5515 Starter Kit开发板原理图：[《GR5515-SK-BASIC-RevC.pdf》]( https://product.goodix.com/zh/docview/GR5515-SK-BASIC-RevC_Rev.1.5?objectId=100&objectType=document&version=133)   |

## 联系

如果您在开发过程中有问题，请在仓库issues提问，或[开发社区](https://developers.goodix.com/zh/bbs/list?orderType=answer)提问。

[开发板信息获取](https://product.goodix.com/zh/kit/gr5515_starter_kit)