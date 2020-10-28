# Table of Contents

* 1 [代码编译](#代码编译)
  * 1.1 [编译](#编译)
  * 1.2 [常见问题](#常见问题)
* 2 [配置文件的修改](#配置文件的修改)
  * 2.1[.yaml文件的修改](#.yaml文件的修改)
  * 2.2[.launch文件的修改](#.launch文件的修改)
# markdown-toc
# 一、代码编译
## 编译
+ 首先从github下载所有代码

  ```sudo git clone 
  //主程序代码
  git clone https://github.com/QiayuanLiao/RM-Software.git
  //视觉部分代码
  git clone https://github.com/QiayuanLiao/rm_detection.git
  ```

+ 把视觉部分代码拷贝到主程序workspace（主程序暂不包含视觉部分代码）

  ```
  cp -r rm_detection/ RM-Software/rm_ws/src/
  ```

+ 编译代码

  ```
  cd RM-Software/rm_ws/
  catkin_make
  ```


+ 等待编译完成

  ![](https://img-blog.csdnimg.cn/20201025114033296.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0MDEwMDgy,size_16,color_FFFFFF,t_70#pic_center)

## 常见问题

+ 缺少依赖包

  ![](https://img-blog.csdnimg.cn/20201025114021180.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0MDEwMDgy,size_16,color_FFFFFF,t_70#pic_center)

解决：

```
//下载相对应的依赖包
sudo apt-get install ros-melodic-[依赖包名]
//重新编译
catkin_make
```
# 二、配置文件的修改
## .yaml文件的修改

## .launch文件的修改
