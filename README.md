# autoware.ai

[![autoware.ai](https://www.autoware.org/autoware)](https://github.com/Goldmann1995/autoware.ai/edit/main/README.md)

Project with Ubuntu 18.04 for autoware.ai


## 2022.09
本项目是为了实现autoware在无人车上的应用。

这个仓库的目标是：

1. 记录项目中的工程修改以及实现。

## 安装

 [github](https://github.com/Goldmann1995/ubuntu18.04-Autoware1.14---GPU-) 可以跟着这个安装流程走。

## 使用说明

### 运行警告处理
 vehicle_model.launch 文件中将robot_state_publisher的 name pkg type都改成 robot_state_publisher

####  运行不同数据包
在autoware的图形界面中，运行不同的数据包可以通过Simulation来加载，通过launch方法也在demo.launch中写入。

##### 1. 设置
在运行前需要将Localizer设置成Velodyne。 可运行 rosparam set localizer velodyne
或者
launch文件中  param name = "localizer"  value = "velodyne" 来实现。
并且同上将 use_sim_time 设置为true，代表允许离线调试。
与此同时，将雷达的标定位置（x, y, z, yaw, pitch, roll）输入设置。
更重要的是加载从世界坐标系到图的位姿转换 /home/$user/autoware.ai/data/tf/tf.launch,这样才能跟踪定位。
##### 2. Localizer
运行/launch/rosbag_demo/my_localization.launch可以实现最基础的demo运行。


## 建图





## 相关仓库

- [Install Readme](https://github.com/Goldmann1995/ubuntu18.04-Autoware1.14---GPU-/READ.md) — 安装教程



