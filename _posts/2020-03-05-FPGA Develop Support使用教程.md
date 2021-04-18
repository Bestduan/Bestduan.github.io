---
layout:     post
title:      FPGA Develop Support使用教程 (环境篇)
subtitle:   FPGA Develop Support使用教程（vivado）
date:       2020-03-03
author:     Sterben
header-img: img/post-bg-5.jpg
catalog: true
tags:
    - FPGA开发教程
---

# 前言

该插件为个人开发一开始只是兴趣，仅为开源出一份力，但是随着后期开发的深入遇到了瓶颈以及越来越多自己无法解决的问题，同时自己还要面临再一次的研究生考试，后面半年内可能无法持续更进，由于插件内容功能太多，教程也无法持续补充，在此表示歉意，你可以自由使用。最后，若是你喜欢这个插件，喜欢数字开发欢迎和我一起交流。邮箱： sterben.661214@gmail.com  。

# 目录
- [前言](#前言)
- [目录](#目录)
- [FPGA_Develop_Support](#fpga_develop_support)
  - [目录](#目录-1)
  - [TODO LIST](#todo-list)
- [START GIF](#start-gif)
- [开发目的](#开发目的)
- [前期配置](#前期配置)
- [现有功能介绍](#现有功能介绍)
  - [前端开发辅助功能](#前端开发辅助功能)
    - [语言支持](#语言支持)
      - [语言高亮](#语言高亮)
      - [语法诊断](#语法诊断)
      - [文件标志](#文件标志)
      - [悬停提示](#悬停提示)
      - [自动补全](#自动补全)
      - [工程结构](#工程结构)
      - [定义跳转](#定义跳转)
      - [自动对齐](#自动对齐)
    - [仿真功能](#仿真功能)
      - [自动生成tb](#自动生成tb)
      - [iverilog快速仿真](#iverilog快速仿真)
      - [modelsim快速仿真](#modelsim快速仿真)
      - [Verilator快速仿真](#verilator快速仿真)
    - [常见功能库](#常见功能库)
  - [后端开发辅助功能](#后端开发辅助功能)
    - [启动方式](#启动方式)
    - [通用功能使用说明](#通用功能使用说明)
    - [vivado开发辅助](#vivado开发辅助)
    - [quartus开发辅助](#quartus开发辅助)
    - [icestorm开发辅助](#icestorm开发辅助)
  - [soc开发辅助](#soc开发辅助)
    - [ZYNQ开发辅助](#zynq开发辅助)
    - [RISC开发辅助](#risc开发辅助)
    - [Cortex-M开发辅助](#cortex-m开发辅助)
  - [调试开发辅助功能](#调试开发辅助功能)
- [其他用户配置说明](#其他用户配置说明)
- [鸣谢](#鸣谢)

# FPGA_Develop_Support

在vscode上的FPGA开发插件

如有问题的话欢迎在[issues](https://github.com/Bestduan/fpga_support_plug/issues)上发表。
另外喜欢的话请给个[star](https://github.com/Bestduan/fpga_support_plug)吧

## 目录
- [前言](#前言)
- [目录](#目录)
- [FPGA_Develop_Support](#fpga_develop_support)
  - [目录](#目录-1)
  - [TODO LIST](#todo-list)
- [START GIF](#start-gif)
- [开发目的](#开发目的)
- [前期配置](#前期配置)
- [现有功能介绍](#现有功能介绍)
  - [前端开发辅助功能](#前端开发辅助功能)
    - [语言支持](#语言支持)
      - [语言高亮](#语言高亮)
      - [语法诊断](#语法诊断)
      - [文件标志](#文件标志)
      - [悬停提示](#悬停提示)
      - [自动补全](#自动补全)
      - [工程结构](#工程结构)
      - [定义跳转](#定义跳转)
      - [自动对齐](#自动对齐)
    - [仿真功能](#仿真功能)
      - [自动生成tb](#自动生成tb)
      - [iverilog快速仿真](#iverilog快速仿真)
      - [modelsim快速仿真](#modelsim快速仿真)
      - [Verilator快速仿真](#verilator快速仿真)
    - [常见功能库](#常见功能库)
  - [后端开发辅助功能](#后端开发辅助功能)
    - [启动方式](#启动方式)
    - [通用功能使用说明](#通用功能使用说明)
    - [vivado开发辅助](#vivado开发辅助)
    - [quartus开发辅助](#quartus开发辅助)
    - [icestorm开发辅助](#icestorm开发辅助)
  - [soc开发辅助](#soc开发辅助)
    - [ZYNQ开发辅助](#zynq开发辅助)
    - [RISC开发辅助](#risc开发辅助)
    - [Cortex-M开发辅助](#cortex-m开发辅助)
  - [调试开发辅助功能](#调试开发辅助功能)
- [其他用户配置说明](#其他用户配置说明)
- [鸣谢](#鸣谢)

## TODO LIST

- [ ] 前端开发辅助功能 
  - [x] 语言支持
    - [x] 语言高亮
    - [x] 文件标志
    - [x] 定义跳转
    - [x] 悬停提示
    - [x] 工程结构
    - [x] 语法诊断
    - [x] 自动对齐
    - [x] 自动补全
  - [ ] 仿真功能
    - [x] 自动生成tb
    - [x] 快速例化
    - [x] vivado快速仿真
    - [x] iverilog快速仿真
    - [ ] modelsim快速仿真
    - [ ] Verilator快速仿真
  - [x] 常见功能库
- [ ] 后端开发辅助功能
  - [x] vivado开发辅助
  - [ ] quartus开发辅助
  - [ ] icestorm开发辅助
- [ ] soc开发辅助
  - [x] ZYNQ开发辅助
  - [ ] RISC开发辅助
  - [ ] Cortex-M开发辅助

# START GIF

* Start interface
![START GIF.gif](https://i.loli.net/2021/04/18/jVU4kwGf83zWFY1.gif)

# 开发目的
[返回目录](#目录)

本插件的开发目的首先在于为数字前端设计提供友好便捷的开发工具，在此之后，再在对FPGA的开发过程中进行去平台化，同时规范文件结构，完成完整统一友好的数字前端设计链。紧接着兼容多家FPGA原厂后端设计，完成一条完整的数字设计链。最后，提供在FPGA上的soc设计方案，兼容soc调试工具

# 前期配置
[返回目录](#目录)

1. 如果你需要自带串口调试工具请安装 **python3** 并将其添加到系统环境变量

2. 如果你需要兼容vivado相关功能（包括语法检查、工程搭建、功能仿真等）请添加如下变量
   
   注：(**添加一定要添加绝对路径，我写相对路径的形式只是告知需要添加哪些，同时注意版本号**)

* `./Vivado/2019.2/bin`
* `./Vitis/2019.2/bin` 或 `./SDK/2018.3/bin`

检测配置成功的方式：在shell中输入
- **xsct**
- **vivado -version**
- **python**
均能执行即为成功

【注】：目前暂时支持vivado开发，后期会兼容其他厂商的开发环境

# 现有功能介绍
[返回目录](#目录)

## 前端开发辅助功能
[返回目录](#目录)

----

### 语言支持
[返回目录](#目录)

----

提供前端代码设计所需的基本语言服务

#### 语言高亮
[返回目录](#目录)

----
![语言高亮.png](https://i.loli.net/2021/03/19/3qzOwZkIMay5rvD.png)
现支持以下语言的高亮

- Verilog
- SystemVerilog
- VHDL
- TCL（包括xdc、sdc、fdc约束文件）

#### 语法诊断
[返回目录](#目录)

----
![语法诊断.png](https://i.loli.net/2021/03/19/bSQFuNgZzaTknwD.png)
语法诊断使用的是外部编译器，因此在setting中配置对应的诊断设置之前请配置好相应的环境。

目前支持的诊断工具有 需要的环境 + setting中HDL.Linting.Linter的设置说明
1. xilinx系列     xvlog--检查Verilog以及systemVerilog  xvhdl--检查vhdl  xmixed--检查HDL语言。
2. modelsim系列   vlog--检查Verilog以及systemVerilog
3. iverilog      检查Verilog以及systemVerilog
4. verilator     检查Verilog以及systemVerilog

#### 文件标志
[返回目录](#目录)

----
![文件标志.png](https://i.loli.net/2021/03/19/42KuR8l5brX1Hz7.png)

#### 悬停提示
[返回目录](#目录)

----
![悬停提示.png](https://i.loli.net/2021/03/19/PXdTfWU7MkLYcSF.png)
【注】：悬停提示使用的是内置的简单Verilog解析器，目前暂时只支持Verilog以及systemVerilog

#### 自动补全
[返回目录](#目录)

----
![自动补全.png](https://i.loli.net/2021/03/19/gMWw3bBpycFDjmP.png)

#### 工程结构
[返回目录](#目录)

----
![工程结构.png](https://i.loli.net/2021/03/20/IJOAf4zqHLS6Zpr.png)

#### 定义跳转
[返回目录](#目录)

----
![定义跳转.gif](https://i.loli.net/2021/04/18/dgNytkS5r6Gqap1.gif)

#### 自动对齐
[返回目录](#目录)

----


### 仿真功能
[返回目录](#目录)

----

#### 自动生成tb
[返回目录](#目录)

----


#### iverilog快速仿真
[返回目录](#目录)

----

#### modelsim快速仿真
[返回目录](#目录)

----

#### Verilator快速仿真
[返回目录](#目录)

----

### 常见功能库
[返回目录](#目录)

----



## 后端开发辅助功能
[返回目录](#目录)

----

### 启动方式
[返回目录](#目录)

----

数字前端辅助功能是安装后即可使用，内置Verilog和vhdl的简单解析器，vhdl的支持后续有时间会完善。

数字后端辅助设计需要配置对应厂商的开发环境，相比于之前版本增加的功能不是很多，后期会继续补充。
现有支持vivado的辅助设计，使用方式如下：

* 步骤一：如果是新建工程则需要生成property文件，注明工程的相关配置
    `使用快捷键 ctrl+shfit+p/F1 打开命令框，输入 **generate property file** 来自动生成`

【注】：生成后进行配置，只有在保存后才会自动生成对应的文件结构。通过`使用快捷键 ctrl+shfit+p/F1 打开命令框，输入 **Overwrite the InitPropertyParam** `可以改写默认工程配置

* 步骤二：启动方式如下：
    1. `使用快捷键 ctrl+shfit+p/F1 打开命令框，输入 **FPGA:Launch** 来启动`
    2. `使用快捷键 Alt+z 打开启动命令`
    3. `从功能框中点击FPGA OPTIONS下的 Launch`


【注】：在设置Soc为非none时，文件结构会被更改，**在文件结构更改的时候如果从有soc结构改回none，文件夹Software会被强制删除，如有重要文件请妥善保存！！！！！**。


### 通用功能使用说明
[返回目录](#目录)

----

1. Refresh 功能，更新xilinx工程下所包含的文件，因为包含的形式是全包含，所以在./user/src和./user/sim下都会包含进去，所以你在src，data，sim下的文件就是你的工程已经包含的文件。更新机制是先全删除再全包含，所以你在文件夹里增删文件，选择**1) Refresh**后，工程里也会一起更新。

2. Build功能，完成综合，布局布线，你可以在Makefile下的**Showlog**里选择实时显示综合布线的日志。当出错的时候会自动跳出错误日志，在设置时如果出现**[CRITICAL WARNING]**时也会跳出，如果正常生成bit和bin文件则可以忽略。

3. Program功能，一键下载，只是下载，固化功能后续补上，不过有zynq的bin文件直接下载到SD卡上插入即可固化。

4. GUI功能，如果需要IP设计，sim时序仿真或者bd设计选择**5) GUI**,之后就会自动打开图形界面。
    【注】：打开GUI后，打开对应工程的vscode，以及对应的startfpga运行终端不能关闭，关闭后GUI会自动关闭


### vivado开发辅助
[返回目录](#目录)

----

### quartus开发辅助
[返回目录](#目录)

----

### icestorm开发辅助
[返回目录](#目录)

----

## soc开发辅助
[返回目录](#目录)

----

### ZYNQ开发辅助
[返回目录](#目录)

----

### RISC开发辅助
[返回目录](#目录)

----

### Cortex-M开发辅助
[返回目录](#目录)

----

## 调试开发辅助功能
[返回目录](#目录)

----

# 其他用户配置说明
[返回目录](#目录)


-----

# 鸣谢
[返回目录](#目录)

* [VHDL](https://github.com/puorc/awesome-vhdl)
* [TCL Language Support](https://github.com/go2sh/tcl-language-support)
* [Verilog HDL/SystemVerilog](https://github.com/mshr-h/vscode-verilog-hdl-support)
* [SystemVerilog - Language Support](https://github.com/eirikpre/VSCode-SystemVerilog)