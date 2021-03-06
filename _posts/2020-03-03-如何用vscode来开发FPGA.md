---
layout:     post
title:      如何用vscode来开发FPGA
subtitle:   如何用vscode来开发FPGA（vivado）
date:       2020-03-03
author:     Sterben
header-img: img/post-bg-4.jpg
catalog: true
tags:
    - FPGA开发教程(环境篇)
---

# 前言内容

之前一直是使用的sublime，轻量，好看的高亮加对Verilog非常友好的支持，使得我快速上手之后就爱不释手，期间也体验了vscode，不过不幸的是发现vscode对Verilog支持很不友好，（感觉IC工程师被孤立了），要是配全功能得装好几个插件，插件功能参差不齐体验极差，之后就放弃了。

不过随着开发的深入，对编辑器有可以能配置成全功能的IDE的需求出现了，再加上对git的使用深入，最后还是开始了vscode之旅。还有就是当时想对自己的社团的小部员做一个更加全面方便的开发工具，显然sublime不适合（虽然他们之后并不care，有点小伤心），就使用了vscode插件的形式来实现fpga开发专用插件，整合设计需求（在此再次感谢vscode开源社区，以及已经开源的插件和前辈们），简化操作，从而节省开发无效时间。

废话不多说开始我们的操作

注：本博客所使用的插件是为本人自制，由于时间和经验限制暂时只支持vivado的开发，quartus和modelsim的相关指令会在充分试验后再发布。

# 更换Vivado自带文本编辑器

## 打开Vivado 再Tool菜单中 打开Settings

![截图setting.png](https://i.loli.net/2020/08/28/2pRUsqm3XSKz1vi.png)

## 在Settings里更换默认的文本编辑器

![截图code路径.png](https://i.loli.net/2020/08/28/E9tPqRVw5bfCzBl.png)

`【注】`：这里需要键入的表达式是:`C:/Program Files/Microsoft VS Code/Code.exe [file name] -[line number]`前面是VsCode应用程序的绝对路径(填写你自己安装的vscode的路径)。[Linux下如果是在环境变量中，可以直接写Code 但是Windows下好像不可以]。

最后双击工程下面的文件，Vivado会自动使用vscode打开文件。

# 配置环境变量

有三个环境变量值需要添加到系统环境变量中，在win下的“环境变量”界面，有用户变量和系统变量两种，用户变量用来定义软件临时文件夹路径，系统变量用于指定应用程序路径。如果觉得不放心可以在两个变量里都添加。Ubuntu的添加方法这里就不详细说明。
需要添加的变量如下(**添加一定要添加绝对路径，我写相对路径的形式只是告知需要添加哪些**)

* 1， ./Vivado/2018.3/bin

* 2， ./SDK/2018.3/bin

* 3， ./Microsoft VS Code/bin

最后要求安装python，并且在安装过程中请选择自动添加到环境变量。需要自动编写testbench的还需安装chardet包，安装方式**pip install chardet**。

# 开始食用

## 语法检测配置

首先打开vscode，在extensions商店中搜索**FPGA Develop Support**进行安装。安装好后就可以支持fpga开发的大部分语言了，如：**vhdl**，**Verilog**，**systemvVerilog**，**TCL**，**xdc**，**sdc**。接下来就是语法检查的配置：

打开设置，选择HDL configuration->Verilog -> Linting: Linter,选择xvlog，这样就可以使用vivado自带的语法检查了。

![screenShot.png](https://i.loli.net/2020/03/03/ytXcDPUYLsEuNzo.png)

同理，如果你想使用的语法纠错插件来自modelsim,quatus，选择他们对应的linter即可。就我个人的使用经验，各个软件的语法排错机制还是有一点细微的不同的，建议选择正确的解析器。设置完成之后，就能实现语法的纠错，在平常的工程中已经可以很给力的帮助你了。

注：编译器需要您手动保存，才会开启xvlog解析，也就是说观看最新错误之前，需要保存一下。

到此所有的配置内容就全部结束了。有关该插件的详细使用教程请转到[FPGA Develop Support]
