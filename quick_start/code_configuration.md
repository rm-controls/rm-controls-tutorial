# 安装
## 软件依赖配置
默认安装ROS melodic，可参考ROS Wiki的[安装教程](http://wiki.ros.org/cn)安装ROS

安装ROS后，还需要下列依赖包。
- apriltag-ros
- behaviortree-cpp-v3

```
    sudo apt-get install ros-melodic-apriltag-ros              \
                         ros-melodic-behaviortree-cpp-v3       \
```
## 从Git上拉取与编译
+ 从github下clone仓库代码

    ```
    
    git clone https://github.com/QiayuanLiao/RM-Software.git
    
    ```

> [!Tip]
>
>该仓库包含了一个catkin_workspace, 需要在 `.bashrc` 中添加。

+ 初始化子模块

    电控代码：
    
    ```
    cd rm_software/
    git submodule update --init rm_msgs/ rm_common/
    
    ```
   
    全套代码：

    ```
    git submodule update --init --recursive 
    
    ```
   
    
> [!Note]
>
>相机驱动和视觉算法两个节点以submodule形式管理。


常见问题：

初始化过程中，如出现```无法读取远程仓库。请确认您有正确的访问权限并且仓库存在```的错误，请参考[解决方案](https://blog.csdn.net/qq_36770641/article/details/88638573) 

+ 编译
  ```
  cd RM-Software/rm_ws/
  catkin_make
  # 加载环境变量
  source devel/setup.bash
  ```
