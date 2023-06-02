# 项目介绍



# 基本配置

## NUC

Ubuntu 18.04.6 LTS（[下载](https://releases.ubuntu.com/18.04.6/ubuntu-18.04.6-desktop-amd64.iso)|安装）

ROS Melodic（[安装](https://blog.csdn.net/jianlai_/article/details/123545130)）

Mavros

```bash
$ sudo apt install ros-melodic-mavros ros-melodic-mavros-extras		# for ros-melodic
$ wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
$ sudo chmod a+x ./install_geographiclib_datasets.sh
$ sudo ./install_geographiclib_datasets.sh		#这步需要装一段时间,请耐心等待PX4配置
```

查看串口

```
ls -l /dev/
```

## CUAV V5+

### 接线

[快速布线](https://doc.cuav.net/flight-controller/v5-autopilot/zh-hans/quick-start/quick-start-v5+.html)

### 软件配置

[FMT](https://firmament-autopilot.github.io/FMT-DOCS/#/content_ch/introduction/quickstart)	 or	[PX4](http://docs.px4.io/main/zh/)

# 项目进度

## 飞控

FMT和IO固件上传

传感器校准

遥控器成功连接；<u>*遥控器校准未完成*</u>

## 平台

接线，*<u>数传图传未连接</u>*

测试电机转向正确

## 视觉

Ubuntu的下载和安装

ROS Melodic的安装

Mavros的安装

实现NUC与飞控的通信，收到来自飞控端的心跳包

# TO DO

1. 遥控器与电源的校准

2. 图传与数传的连接

3. 遥控器如何正确解锁

4. ROS与视觉算法结合并向飞控发送飞行指令

# Reference

[雷迅v5+产品说明书](https://www.cuav.net/wp-content/uploads/2019/09/V5%E8%AF%B4%E6%98%8E%E4%B9%A60709.pdf)

[FMT Mavros使用指南](https://github.com/vvEverett/Multi-rotor/blob/main/Reference/FMT%20Mavros%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97.pdf)