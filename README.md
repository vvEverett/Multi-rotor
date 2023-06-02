# 基本配置

## NUC

Ubuntu 18.04.6 LTS（[下载](https://releases.ubuntu.com/18.04.6/ubuntu-18.04.6-desktop-amd64.iso)|安装）

ROS Melodic（[安装](https://blog.csdn.net/jianlai_/article/details/123545130)）

Mavros

```bash
$ sudo apt install ros-melodic-mavros ros-melodic-mavros-extras     # for ros-melodic
$ wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
$ sudo chmod a+x ./install_geographiclib_datasets.sh
$ sudo ./install_geographiclib_datasets.sh							#这步需要装一段时间,请耐心等待PX4配置
```

查看串口

```
ls -l /dev/
```

