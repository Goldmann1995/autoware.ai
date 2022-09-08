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

启动autoware

$ roslaunch runtime_manager runtime_manager.launch

新终端运行

$ rosparam set /use_sim_time true

再开一个新终端

$ rosbag play --clock  nsh_indoor_outdoor.bag /velodyne_points:=/points_raw 
这里存在雷达点云topic到autoware的点云topic的重映射
接着点击空格Pause


选择管理界面切换到setup分页
Localizer设置成Velodyne
点击TF按钮，再点击Vehicle Model
再切换到Computing分页
点击ndt_localizer下的ndt_mapping后面的app完成参数设置
点击ndt_mapping打勾

最后切换到rosbag play 的终端，按空格运行

等图像建图完成后，再切换到Computing分页
点击ndt_localizer下的ndt_mapping后面的app，选择要导出的PCD的路径，点击Ref进行选择。

再查看导出的地址路径，就可以看到导出对应名称的pcd文件了。


## 定位

启动autoware

$ roslaunch runtime_manager runtime_manager.launch

新终端运行

$ rosparam set /use_sim_time true

再开一个新终端

$ rosbag play --clock  nsh_indoor_outdoor.bag /velodyne_points:=/points_raw 
这里存在雷达点云topic到autoware的点云topic的重映射
接着点击空格Pause

在[Setup]菜单下点击[TF]按钮，并确定Localizer选项位于[Velodyne]处，同时确保参
数配置正确。
点击TF按钮，再点击Vehicle Model

在[Map]菜单栏中加载之前建⽴的pcd地图和TF⽂件并加载⽣效。

在[Sensing]菜单栏下找到右边[voxel_grid_filter]选项并勾选。

找到[Computing]左菜单栏下的[ndt_matching]选项，打开[app]，确保[topic:/config/
ndt]选项处于[Initial_Pose]处，如果有GPU则把[Method_Type]更改为[pcl_anh_gpu]，退
出并勾选ndt_matching。

找到[Computing]左菜单栏下的[vel_pose_connect]，打开[app]并确保选项
[Simulation_Mode]没有被勾选，退出并勾选vel_pose_connect。

打开[Rviz],在[file]菜单中的[open config]选择路径为
：/home(User)/Autoware/ros/src/.config/rviz/default.rviz的⽂件。


最后切换到rosbag play 的终端，按空格运行

切换到rviz就能看到定位了，如果存在点云加载不出来的问题可以，点击左侧的map重新加载。



## 相关仓库

- [Install Readme](https://github.com/Goldmann1995/ubuntu18.04-Autoware1.14---GPU-/READ.md) — 安装教程
- [Mapping](https://www.ncnynl.com/archives/201910/3412.html)  — 建图教程
- [Localization](https://blog.csdn.net/m0_45388819/article/details/108702182)  — 定位教程

