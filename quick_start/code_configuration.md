# 安装
## 从Git上拉取
首先从github下clone仓库代码

    git clone https://github.com/QiayuanLiao/RM-Software.git

> [!Tip]
>
>该仓库包含了一个catkin_workspace, 需要在 `.bashrc` 中最后一行添加。

```source ~/RM-Software-master/rm_ws/devel/setup.bash```

初始化子模块

    git submodule update --init --recursive 

> [!Note]
>
>相机驱动和视觉算法两个节点以submodule形式管理。

## 依赖

- [Robot Operating System (ROS)](http://wiki.ros.org) (middleware for robotics),
- xxxxxx

安装ROS后，通过。

    sudo apt-get install ros-melodic-[依赖包名]


# 配置文件
## yaml文件

## launch文件
