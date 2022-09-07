# autoware.ai

[![autoware.ai](https://www.autoware.org/autoware)](https://github.com/Goldmann1995/autoware.ai/edit/main/README.md)

Project with Ubuntu 18.04 for autoware.ai

本仓库包含以下内容：

1. 一个标准的 README 文件应该是什么样子的[规范](spec.md)。
2. 一个用于维护 README 文件的语法提示工具的链接 ([正在进行中](https://github.com/RichardLitt/standard-readme/issues/5))。
3. 一个创建标准 README 的[生成器](https://github.com/RichardLitt/generator-standard-readme)。
4. 一个指向该规范的[徽章](#徽章)。
5. [标准 README 的实例](example-readmes/) - 比如你正在读的这个文件。
标准 Readme 是为了开源组件设计的。尽管它的[背景](#背景)是为了服务于 Node 和 npm 项目, 它同时也可以应用到其他编程语言和包管理器中去。

## 内容列表

- [背景](#背景)
- [安装](#安装)
- [使用说明](#使用说明)
- [示例](#示例)
- [相关仓库](#相关仓库)

## 2022.09
本项目是为了实现autoware在无人车上的应用。

这个仓库的目标是：

1. 记录项目中的工程修改以及实现。

## 安装

这个项目使用 [node](https://github.com/Goldmann1995/ubuntu18.04-Autoware1.14---GPU-) 请确保你本地安装了它们。

## 使用说明

### 运行警告处理
 vehicle_model.launch 文件中将robot_state_publisher的 name pkg type都改成 robot_state_publisher

####  运行不同数据包
在autoware的图形界面中，运行不同的数据包可以通过Simulation来加载，通过launch方法也在demo.launch中写入。

##### 1. Localizer 

在运行前需要将Localizer设置成Velodyne。 可运行 rosparam set localizer velodyne
或者
launch文件中  param name = "localizer"  value = "velodyne" 来实现。
并且同上将 use_sim_time 设置为true，代表允许离线调试。
与此同时，将雷达的标定位置输入设置。

##### 2.Load Vefhicle Model
加载小车模型。


## 示例

想了解我们建议的规范是如何被应用的，请参考 [example-readmes](example-readmes/)。

## 相关仓库

- [Install Readme](https://github.com/Goldmann1995/ubuntu18.04-Autoware1.14---GPU-/READ.md)
- [open-source-template](https://github.com/davidbgk/open-source-template/) — 一个鼓励参与开源的 README 模板。



