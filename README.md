# 项目介绍

![structure](/Assets/structure.png)

# 基本配置

## NUC

### Ubuntu 18.04.6 LTS

[下载](https://releases.ubuntu.com/18.04.6/ubuntu-18.04.6-desktop-amd64.iso)|安装

### ROS Melodic

[安装](https://blog.csdn.net/jianlai_/article/details/123545130)

### Mavros

```bash
$ sudo apt install ros-melodic-mavros ros-melodic-mavros-extras		# for ros-melodic
$ wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
$ sudo chmod a+x ./install_geographiclib_datasets.sh
$ sudo ./install_geographiclib_datasets.sh		#这步需要装一段时间,请耐心等待PX4配置
```

### Realsense D435驱动

[realsense-ros/README.md at ros1-legacy · IntelRealSense/realsense-ros (github.com)](https://github.com/IntelRealSense/realsense-ros/blob/ros1-legacy/README.md#installation-instructions)

```bash
sudo apt-get install ros-$ROS_DISTRO-realsense2-camera
```



### Anaconda

[下载](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)|[安装](https://blog.csdn.net/KIK9973/article/details/118772450)

创建虚拟环境

```bash
conda create -n uav python=3.8
```

解决ROS Melodic不支持Python3问题：[ROS Melodic 上部署python3 环境 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/626511511)

某些奇怪问题的解决：[(61条消息) ROS编译PyKDL python3_RuiH.AI的博客-CSDN博客](https://blog.csdn.net/qq_41035283/article/details/125714646)

```bash
sudo apt update
sudo apt install python3-catkin-pkg-modules python3-rospkg-modules python3-empy
mkdir -p ~/catkin_ws/src; cd ~/catkin_ws
catkin_make
source devel/setup.bash
wstool init
wstool set -y src/geometry2 --git https://github.com/ros/geometry2 -v 0.6.5
wstool up
rosdep install --from-paths src --ignore-src -y -r
catkin_make --cmake-args -DCMAKE_BUILD_TYPE=Release             -DPYTHON_EXECUTABLE=/home/tian/anaconda3/envs/uav/bin/python3.8  -DPYTHON_INCLUDE_DIR=/home/tian/anaconda3/envs/uav/include/python3.8             -DPYTHON_LIBRARY=/home/tian/anaconda3/envs/uav/lib/libpython3.8.so -DPYTHON_LIBRARY=/home/tian/anaconda3/envs/uav/lib/libpython3.8.so
```

cmake指令

```bash
cmake .. -DCMAKE_BUILD_TYPE=Release             -DPYTHON_EXECUTABLE=/home/tian/anaconda3/envs/uav/bin/python3.8  -DPYTHON_INCLUDE_DIR=/home/tian/anaconda3/envs/uav/include/python3.8             -DPYTHON_LIBRARY=/home/tian/anaconda3/envs/uav/lib/libpython3.8.so -DPYTHON_LIBRARY=/home/tian/anaconda3/envs/uav/lib/libpython3.8.so -DCMAKE_INSTALL_RPATH=/home/tian/anaconda3/envs/uav/lib/PyDKL.so -DCMAKE_INSTALL_PREFIX=/home/tian/anaconda3/envs/uav
```



### 查看串口

```
ls -l /dev/
```

## CUAV V5+

### 接线

[快速布线](https://doc.cuav.net/flight-controller/v5-autopilot/zh-hans/quick-start/quick-start-v5+.html)

### 数传连接

> 3DR Radio Telemetry配对步骤
>
> 1. 给数传模块供电，绿灯闪烁。
>
> 2. 按住配对按钮3秒，红灯快闪，进入配对模式。配对模式持续时间10秒。
>
> 3. 在10秒内给另一个数传模块供电，绿灯常亮表示配对成功。

### 软件配置

[FMT](https://firmament-autopilot.github.io/FMT-DOCS/#/content_ch/introduction/quickstart)	 or	[PX4](http://docs.px4.io/main/zh/)

## 遥控器配置

遥控器型号 WFLY WFT90S2

# 项目进度

## 飞控

FMT和IO固件上传

传感器校准

遥控器成功连接；<u>*遥控器校准未完成*</u>

## 平台

接线，*<u>图传未连接</u>*

测试电机转向正确

GPS已连接

数传已连接

## 视觉

Ubuntu的下载和安装

ROS Melodic的安装

Mavros的安装

实现NUC与飞控的通信，收到来自飞控端的心跳包

# TO DO

1. 遥控器与电源的校准

2. 图传~~与数传~~的连接

3. 遥控器如何正确解锁

4. ROS与视觉算法结合并向飞控发送飞行指令

# Reference

[雷迅v5+产品说明书](https://www.cuav.net/wp-content/uploads/2019/09/V5%E8%AF%B4%E6%98%8E%E4%B9%A60709.pdf)

[FMT Mavros使用指南](https://github.com/vvEverett/Multi-rotor/blob/main/Reference/FMT%20Mavros%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97.pdf)

[NEO3 GPS使用指南](https://doc.cuav.net/gps/neo-series-gnss/zh-hans/neo-3.html)

[NEO3 GPS说明书](https://www.cuav.net/wp-content/uploads/2020/12/NEO-3%E8%AF%B4%E6%98%8E%E4%B9%A6.pdf)

[3DR数传 使用教程](https://doc.cuav.net/tutorial/copter/optional-hardware/radio/3dr-radio/3dr-radio.html)

[ROS-YOLO 使用教程](https://juejin.cn/post/7232173138804146232)
