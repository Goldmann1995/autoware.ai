# autoware.ai
Project with Ubuntu 18.04 for autoware.ai

# 运行警告处理
 vehicle_model.launch 文件中将robot_state_publisher的 name pkg type都改成 robot_state_publisher

##  运行不同数据包
在autoware的图形界面中，运行不同的数据包可以通过Simulation来加载，通过launch方法也在demo.launch中写入。

### 1. Localizer 

在运行前需要将Localizer设置成Velodyne。 可运行 rosparam set localizer velodyne
或者
launch文件中  param name = "localizer"  value = "velodyne" 来实现。
并且同上将 use_sim_time 设置为true，代表允许离线调试。
与此同时，将雷达的标定位置输入设置。

### 2.Load Vefhicle Model
加载小车模型。



