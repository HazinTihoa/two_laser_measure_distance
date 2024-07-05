- [cn](#操作指南)
- [en](#Instructions)
# 操作指南

>此SDK仅适用于以下产品型号的激光雷达产品:
> -  LDROBOT LiDAR STP23
> -  LDROBOT LiDAR STP23L

## 1. 系统设置
- 将雷达连接到你的系统主板，设置雷达在系统中挂载的串口设备-x权限(以/dev/ttyUSB0为例)
	- 实际使用时，根据雷达在你的系统中的实际挂载情况来设置，可以使用`ls -l /dev`命令查看.

``` bash
sudo chmod 777 /dev/ttyUSB0
```

  - 修改`ros_app/src/ldlidar/launch/ .launch`文件中的port_name值，以`stp23.launch`和`/dev/ttyUSB0`为例，如下所示.

```xml
<launch>
<!-- ldldiar message publisher node -->
 <node name="STP23" pkg="ldlidar" type="ldlidar" output="screen" >
  <param name="product_name" value="LDLiDAR_STP23"/>
  <param name="topic_name" value="laser"/>
  <param name="port_name" value ="/dev/ttyUSB0"/>
  <param name="port_baudrate" value ="921600"/>
  <param name="frame_id" value="base_laser"/>
 </node>
 <!-- publisher tf transform, parents frame is base_link, child frame is base_laser -->
 <!-- args="x y z yaw pitch roll parents_frame_id child_frame_id period_in_ms"-->
 <node name="base_to_laser_stp23" pkg="tf" type="static_transform_publisher"  args="0.0 0.0 0.18 0 0.0 0.0 base_link base_laser 100"/>
</launch>
```
## 2. 编译方法

使用catkin编译，在readme文件所在目录下执行如下指令.

```bash
catkin_make
```
## 3. 运行方法

```bash
source devel/setup.bash
```
- 产品型号为 LDROBOT STP23

  - 启动STP23 node:
  ``` bash
  roslaunch ldlidar stp23.launch
  ```
  - 启动STP23 node并显示激光数据在Rviz上:
  ``` bash
  # if ROS_DISTRO in 'kinetic' or 'melodic'
  roslaunch ldlidar viewer_stp23_kinetic_melodic.launch
  # if ROS_DISTRO in 'noetic'
  roslaunch ldlidar viewer_stp23_noetic.launch
  ```

- 产品型号为 LDROBOT STP23L

  - 启动STP23L node:
  ``` bash
  roslaunch ldlidar stp23l.launch
  ```
  - 启动STP23L node并显示激光数据在Rviz上:
  ``` bash
  # if ROS_DISTRO in 'kinetic' or 'melodic'
  roslaunch ldlidar viewer_stp23l_kinetic_melodic.launch
  # if ROS_DISTRO in 'noetic'
  roslaunch ldlidar viewer_stp23l_noetic.launch
  ```
##   4. 可视化

> 代码支持ubuntu16.04 ROS kinetic、ubuntu18.04 ROS melodic、ubuntu20.04 ROS noetic版本下测试，使用rviz可视化。

- 新打开一个终端 (Ctrl + Alt + T),并通过Rviz工具打开rviz文件夹下面的rviz配置文件
```bash
rviz
```
![rviz_demo](../doc/stp_rviz.png)

[回到仓库简介](../README.md)

# Instructions

> This SDK is only available for lidar products of the following product models：
> -  LDROBOT LiDAR STP23
> -  LDROBOT LiDAR STP23L

## step 1: system setup
- Set the permission of serial port device mounted by LiDAR in the system(example:device name is /dev/ttyUSB0)
    - The actual use of the radar is based on the actual mounted on your system, you can use the `ls -l /dev` command to view. 

``` bash
sudo chmod 777 /dev/ttyUSB0
```
  -  Modify port_name value in the `ros_app/src/ldlidar/launch/` .launch  files,

   > for example `stp23.launch` and `/dev/ttyUSB0`.

``` xml
<launch>
<!-- ldldiar message publisher node -->
 <node name="STP23" pkg="ldlidar" type="ldlidar" output="screen" >
  <param name="product_name" value="LDLiDAR_STP23"/>
  <param name="topic_name" value="laser"/>
  <param name="port_name" value ="/dev/ttyUSB0"/>
  <param name="port_baudrate" value ="921600"/>
  <param name="frame_id" value="base_laser"/>
 </node>
 <!-- publisher tf transform, parents frame is base_link, child frame is base_laser -->
 <!-- args="x y z yaw pitch roll parents_frame_id child_frame_id period_in_ms"-->
 <node name="base_to_laser_stp23" pkg="tf" type="static_transform_publisher"  args="0.0 0.0 0.18 0 0.0 0.0 base_link base_laser 100"/>
</launch>
```
## step 2: build

Run the following command in the directory where the readme file resides.

```bash
catkin_make
```
## step 3: run

```bash
source devel/setup.bash
```
- The product is LDROBOT STP23

  - Start STP23 node:
  ``` bash
  roslaunch ldlidar stp23.launch
  ```
  - Start STP23 node and show laser data on the Rviz tool:
  ``` bash
  # if ROS_DISTRO in 'kinetic' or 'melodic'
  roslaunch ldlidar viewer_stp23_kinetic_melodic.launch
  # if ROS_DISTRO in 'noetic'
  roslaunch ldlidar viewer_stp23_noetic.launch
  ```

- The product is LDROBOT STP23L

  - Start STP23L node:
  ``` bash
  roslaunch ldlidar stp23l.launch
  ```
  - Start STP23L node and show laser data on the Rviz tool:
  ``` bash
  # if ROS_DISTRO in 'kinetic' or 'melodic'
  roslaunch ldlidar viewer_stp23l_kinetic_melodic.launch
  # if ROS_DISTRO in 'noetic'
  roslaunch ldlidar viewer_stp23l_noetic.launch
  ```
## step 3: visuallization

> The code was tested under ubuntu16.04 ROS kinetic、ubuntu18.04 ROS melodic、ubuntu20.04 ROS noetic, using rviz visualization.

- new a terminal (Ctrl + Alt + T) and use Rviz tool,open the rviz config file below the rviz folder
```bash
rviz
```
![rviz_demo](../doc/stp_rviz.png)

[ Back to the introduction ](../README.md)

