# rm_base模块

## 模块介绍

机器人驱动模块是连接各底层插件与电机的桥梁，从ros参数服务器中获得电机参数信息和插件信息，完成参数和插件的加载，然后以1000Hz的频率接受、处理can总线上的数据，再通过can总线实现对电机的控制。

模块文件目录如下所示

```bash
rm_base
├── CMakeLists.txt
├── include
│   ├── dbus_node.h
│   ├── referee_node.h
│   ├── rm_base.h
├── src
│   ├── dbus_node.cpp
│   ├── referee_node.cpp
│   ├── rm_base.cpp
│   ├── rm_base_ndoe.cpp
└── package.xml
```

在该模块的核心运行节点`rm_base`中，创建所需模块的插件（如底盘、云台）并加载参数到ros参数服务器后，即可正常执行通信任务。

## 编译与运行

### 编译

在ROS的工作区内编译

```shell
catkin_make  rm_base rm_base 
```

### 运行

执行roborts_base_node节点

```shell
rosrun rm_base rm_base
```





