# 安装
## 从Git上拉取
首先从github下clone仓库代码

    git clone https://github.com/QiayuanLiao/RM-Software.git

> [!Tip]
>
>该仓库包含了一个catkin_workspace, 需要在 `.bashrc` 中最后一行添加。

```source ~/RM-Software/rm_ws/devel/setup.bash```

初始化子模块

    git submodule update --init --recursive 

> [!Note]
>
>相机驱动和视觉算法两个节点以submodule形式管理。


常见问题：

初始化过程中，如出现```无法读取远程仓库。请确认您有正确的访问权限并且仓库存在```的错误，请参考[解决方案](https://blog.csdn.net/qq_36770641/article/details/88638573) 
## 依赖

- [Robot Operating System (ROS)](http://wiki.ros.org) (middleware for robotics),
- xxxxxx

安装ROS后，通过。

    sudo apt-get install ros-melodic-[依赖包名]


# 配置文件
## yaml文件
yaml文件所在目录：```~/RM-Software-master/rm_ws/src/rm_bringup/config```下的```joint_param.yaml```和``standard.yaml``

+ standard.yaml的内容：

```yaml
joint:
  [
  {name: "wheel_rf", bus: "can0", id: 0x201,
   type: "3508", ctrl: "speed" ,dir: false},
  {name: "wheel_lf", bus: "can0", id: 0x202,
   type: "3508", ctrl: "speed" ,dir: true},
  {name: "wheel_lb", bus: "can0", id: 0x203,
   type: "3508", ctrl: "speed" ,dir: true},
  {name: "wheel_rb", bus: "can0", id: 0x204,
   type: "3508", ctrl: "speed" ,dir: false},
  {name: "yaw", bus: "can0", id: 0x205,
   type: "6020", ctrl: "pd" ,dir: true},
  {name: "pitch", bus: "can1", id: 0x206,
   type: "6020", ctrl: "pd" ,dir: true},
  {name: "fiction_l", bus: "can1", id: 0x201,
   type: "3508_dir", ctrl: "speed" ,dir: true},
  {name: "fiction_r", bus: "can1", id: 0x202,
   type: "3508_dir", ctrl: "speed" ,dir: false},
  {name: "trigger", bus: "can0", id: 0x206,
   type: "2006", ctrl: "pd" ,dir: true},
  ]

imu:
  {type: "hi220", port: "/dev/usbImu", id: 0, rate: 200,
   frame_fixed: "yaw", frame_source: "odom", frame_target: "base_link"}

gpio:
  [
  {name: "switch", port: "can1", id: 0x300, dir: "input"},
  ]

plugins:
  - chassis_plugins::Standard
  - gimbal_plugins::Standard
  - shooter_plugins::Standard
  - imu_plugins::Hi220Uart
```



standard.yaml负责记录机器人上所有电机、IMU、GPIO和插件的信息

### joint:

| 参数名称 |   参数作用   |
| :------: | :----------: |
|   name   |  joint名字   |
|   bus    |   通讯方式   |
|    id    |    电机ID    |
|   type   |   电机类型   |
|   ctrl   |    控制器    |
|   dir    | 电机转动方向 |

### imu:陀螺仪

|   参数名称   |  参数作用  |
| :----------: | :--------: |
|     type     | 陀螺仪类型 |
|     port     |    端口    |
|      id      | 陀螺仪ID号 |
|     rate     |    速率    |
| frame_fixed  |  固定框架  |
| frame_source |   框架源   |
| frame_target |  框架目标  |

### GPIO

| 参数名称 |  参数作用  |
| :------: | :--------: |
|   name   |    名称    |
|   port   |   端口号   |
|    id    |     ID     |
|   dir    | 输入or输出 |

### plugins:插件
根据不同机器人的不同功能，加载不同的插件
### 示例：

假如我们现在要编写一辆仅具备移动功能的机器人，我们需要在joint下添加四个电机来控制轮子、一个陀螺仪来获取加速度信息：

+ 第一个name为wheel_lf、挂载在can0总线上、ID号为0x201、电机类型为3508、控制器为PD控制器、正向转动的左前轮电机。

+ 第二个name为wheel_rf、挂载在can0总线上、ID号为0x202、电机类型为3508、控制器为PD控制器、正向转动的右前轮电机。

+ 第三个name为wheel_lb、挂载在can0总线上、ID号为0x203、电机类型为3508、控制器为PD控制器、正向转动的左后轮电机。

+ 第四个name为wheel_rb、挂载在can0总线上、ID号为0x204、电机类型为3508、控制器为PD控制器、正向转动的右后轮电机。

+ 一个类型为hi220、端口为/dev/usbImu、ID号为1、速率为200hz、frame_fixed为yaw、frame_source为odom、frame_target为base_link的陀螺仪。

  

则示例standard.yaml文件如下：

```yaml
joint:
  [
  {name: "wheel_lf", bus: "can0", id: 0x201,
   type: "3508", ctrl: "pd" ,dir: true},
  {name: "wheel_rf", bus: "can0", id: 0x202,
   type: "3508", ctrl: "pd" ,dir: true},
  {name: "wheel_lb", bus: "can0", id: 0x203,
   type: "3508", ctrl: "pd" ,dir: true},
  {name: "wheel_rb", bus: "can0", id: 0x204,
   type: "3508", ctrl: "pd" ,dir: true},
  ]

imu:
  {type: "hi220", port: "/dev/usbImu", id: 1, rate: 200,
   frame_fixed: "yaw", frame_source: "odom", frame_target: "base_link"}
```


