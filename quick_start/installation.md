

# 安装 ubuntu 系统



先从一台能够制作启动盘的机器开始。
我制作引导盘的电脑是 win10 系统，联想拯救者Y7000,安装 Ubuntu 的电脑是拯救者Y7000

## 一、 准备镜像文件

下载Ubuntu18.04 LTS 系统
镜像下载地址
<https://releases.ubuntu.com/18.04/?_ga=2.4315507.1959284852.1603900682-415893344.1603546260>

下载后的文件：ubuntu-18.04.5-desktop-amd64.iso     

![Alt text](https://img-blog.csdnimg.cn/20200220113949183.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTQ0NTM0NDM=,size_16,color_FFFFFF,t_70)

## 二、制作U盘启动系统

启动盘制作工具，建议Ubuntu官网推荐的rufus，无需安装即可使用
Rufus
 [https://rufus.akeo.ie](https://rufus.akeo.ie/)

插入U盘后，直接双击下载的fufus.exe(绿色免安装)启动， 按照如图设置后，软件会把ubuntu-18.04.5-desktop-amd64.iso文件，写入U盘，制作系统启动盘。（根据图片来选择选项）

![](https://img-blog.csdnimg.cn/20200220143629910.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTQ0NTM0NDM=,size_16,color_FFFFFF,t_70)

选择时不要选错U盘，完成后U盘会格式化，小心操作

![](https://img-blog.csdnimg.cn/20190301131652108.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTQ0NTM0NDM=,size_16,color_FFFFFF,t_70)

<img src="https://img-blog.csdnimg.cn/2019030113171613.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTQ0NTM0NDM=,size_16,color_FFFFFF,t_70" style="zoom:80%;" />

![](https://img-blog.csdnimg.cn/20190301131748959.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTQ0NTM0NDM=,size_16,color_FFFFFF,t_70)

等待10分钟左右，Ubuntu启动盘就制作完成了。

## 三、磁盘分区

### 1.选择分区

在桌面右击 **计算机** ,选择管理，点击左侧**磁盘管理** 

<img src="https://pic1.zhimg.com/80/v2-abe37864e5f70dc43fd522712c20d804_720w.jpg" style="zoom: 67%;" />

<img src="https://pic4.zhimg.com/80/v2-c0e84a4c82d72a9cbdc960501e7cba7f_720w.jpg" style="zoom:67%;" />



### 2.压缩卷

在你的机械硬盘或固态硬盘上分出一个大于40G的空间（我分了60G）。具体为右击你要分区的磁盘，选择**压缩盘**，填入你要压缩的空间大小

<img src="https://pic4.zhimg.com/80/v2-ea5cb1e5e0e9a202ca00c9e01477f32b_720w.jpg" style="zoom: 80%;" />

**【输入压缩空间大小】**

例如：分100GB=1024MBX100+150MB=102550MB

点击 【压缩】

<img src="https://pic1.zhimg.com/80/v2-c7593d728e87a095b0d59bf2c95a36fc_720w.jpg" style="zoom:67%;" />

压缩出来一个 100.15GB的 【未分配】磁盘空间

<img src="https://pic4.zhimg.com/80/v2-7b24b0929710ba730f45ba487bde56a3_720w.jpg" style="zoom: 80%;" />

## 四、BIOS设置

### 1.关闭快速启动

1. 我们首先右击左下角开始图标
2. 在弹出的常用菜单中我们选择“电源选项

![](https://exp-picture.cdn.bcebos.com/1f9feadca039131fd7aca26de275f2c4ed990a94.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

3. 在“电源选项”中我们选择“选择电源按钮的功能”

![](https://exp-picture.cdn.bcebos.com/edd84743040148fe3f022cdf8fd149299b880294.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

4. 我们在设置中选择“更改当前不可用的设置

![](https://exp-picture.cdn.bcebos.com/4759c1dae43b3b8632613ee3185653bbf9207594.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

5. 这时候我们的“快速启动”我们就可以进行修改了。我们把前面的勾去掉。完成后我们选择“保存修改”

![](https://exp-picture.cdn.bcebos.com/52fae62064fb960b066174d58fa355e982ae6c94.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

### 2.修改启动项(修改BIOS)

1. 之后接上 U 盘，重启进入 BIOS 界面，如下图。注意各种型号电脑进入 bios 方式不同，具体可百度参考，本文电脑为联想 拯救者Y7000，所以在重启时长按 F2 即可进入 BIOS 界面。

2. 直到进入BIOS，点击方向箭头→ 移动到Security，再按↓移动到Secure Boot上，点击**回车键**，选择Disable

<img src="https://upload-images.jianshu.io/upload_images/11037888-3018f929a665a835.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp" style="zoom: 67%;" />

> 附上其他电脑参考：
>
> 戴尔笔记本：F12 	神舟笔记本：F12   华硕笔记本：ESC   方正笔记本：F12  	清华同方笔记本：F12     联想 Thinkpad：F12   三星笔记本：F12  苹果笔记本：长按“option”键  

3. 当然，最好去Boot里面看看USB Boot是否为 **Enabled**

<img src="https://upload-images.jianshu.io/upload_images/11037888-3884606d11a079b1.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp" style="zoom:67%;" />

4. 需要在BIOS中将SATA Controller Mode选为ACHI模式，最后，按 **F10** 保存退出。

## 五、安装Ubuntu到电脑

### 1.安装流程

1. 重启进去你的电脑品牌界面时，一直狂戳**F12**,在出现的界面选择你的U盘，如我的这里有个明显的"USB 3.0"，请自行甄别。

   <img src="https://upload-images.jianshu.io/upload_images/11037888-a18a325be9810453.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp" style="zoom: 80%;" />

2. 等待一会便进入启动选项，不用动，就选择 Try ubuntu whthout install，可以先看看Ubuntu在你的电脑上的运行状况再安装。

3. 进入Ubuntu后，如果你觉得正常，便可以点击左上角的 Install Ubuntu 18.04LTS

   <img src="https://upload-images.jianshu.io/upload_images/11037888-fb59726dd32d7913.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp" style="zoom: 67%;" />

4. 首先选择语言为中文(简体)，点继续

   <img src="https://upload-images.jianshu.io/upload_images/11037888-5409a708aafec5c1.png?imageMogr2/auto-orient/strip|imageView2/2/w/976/format/webp" style="zoom:80%;" />

5. 键盘布局已经自动选择好了，你可以选择不改变；

   <img src="https://upload-images.jianshu.io/upload_images/11037888-8b18a51afbc2cb64.png?imageMogr2/auto-orient/strip|imageView2/2/w/874/format/webp" style="zoom:80%;" />

6. 接着无线选项中，选择*我现在不想连接wifi无线网络*
   <img src="https://upload-images.jianshu.io/upload_images/11037888-145d0377872e561f.png?imageMogr2/auto-orient/strip|imageView2/2/w/878/format/webp" style="zoom:80%;" />

7. 在*更新和其他软件*中，选择*最小安装*以加快安装速度
   <img src="https://upload-images.jianshu.io/upload_images/11037888-c62b428b60bfcc29.png?imageMogr2/auto-orient/strip|imageView2/2/w/877/format/webp" style="zoom:80%;" />

8. 在安装类型中，选择*其他选项*
   <img src="https://upload-images.jianshu.io/upload_images/11037888-1896e2bb631233c5.png?imageMogr2/auto-orient/strip|imageView2/2/w/879/format/webp" style="zoom:80%;" />

9. 在出现的页面中找到并点击你之前分的空闲盘，我是根据大小寻找的，我之前分了60G，所以我找到大小60G左右的盘，双击该分区或者选中该分区后，点击左下角的 **+**

   <img src="https://upload-images.jianshu.io/upload_images/11037888-42d8757cc4cbe9ce.png?imageMogr2/auto-orient/strip|imageView2/2/w/861/format/webp" style="zoom:80%;" />

### 2.分区方案

我采用的是如下的方案

1. **EFI 分区，主空间，空间起始位置，大小512M**

   <img src="https://upload-images.jianshu.io/upload_images/11037888-a6e4390c1230aad8.png?imageMogr2/auto-orient/strip|imageView2/2/w/860/format/webp" style="zoom:80%;" />

2. **/ (根目录)，主分区，空间起始位置，大小为剩下空间的一半**

   <img src="https://upload-images.jianshu.io/upload_images/11037888-56a6d80555336850.png?imageMogr2/auto-orient/strip|imageView2/2/w/863/format/webp" style="zoom:80%;" />

3. **/ home(根目录)，主分区，空间起始位置，大小为剩下空间的一半**

### 3.安装

1. 在安装启动引导器中选择你刚刚分的EFI分区，然后点击现在安装，弹出选项点击确认就好，对于安装了Windows且上面没有分efi分区的用户来说，可以选择Windows的efi分区，也就是最后写着 Windows Boot Manager的分区

<img src="https://upload-images.jianshu.io/upload_images/11037888-2799260aca558a7a.png?imageMogr2/auto-orient/strip|imageView2/2/w/863/format/webp" style="zoom: 80%;" />



2. 接下来，时区选择以自动选择为东八区了，最后就是输入电脑的用户名、电脑名称和密码了，等待安装完成后，由于一些原因无法直接关机，只能长按电源键，之后开启电脑便会进入Ubuntu的启动引导，输入密码，你便进入了一个全新的世界！



# 安装ROS

## 一、软件中心配置

首先打开软件和更新对话框，具体可以在 Ubuntu 最左上角的搜索按钮中搜索。

打开后按照下图进行配置（确保你的"restricted"， "universe，" 和 "multiverse."前是打上勾的）：

<img src="http://images2015.cnblogs.com/blog/979377/201608/979377-20160817151652093-335406272.png" style="zoom:80%;" />

配置完成后就可以关闭该窗口了。

## 二、添加源

### 1.打开终端（Ctrl + Alt + T），输入如下指令：

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

### 2.设置秘钥:

```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

如果遇到连接到密钥服务器的问题，可以尝试在前面的命令中替换hkp://pgp.mit.edu:80 或 hkp://keyserver.ubuntu.com:80

```
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -

```


![](https://img-blog.csdn.net/20180508164913756)

### 3.安装ROS

首先，确保你的Debian软件包索引是最新的

```
sudo apt-get update
```

![](https://img-blog.csdn.net/20180508165136725)

在ROS中，有很多不同的库和工具。我们提供了四种默认的配置来帮助你开始。你也可以单独安装ROS包.

```
sudo apt-get install ros-kinetic-desktop-full
```

>**桌面完整版: (推荐)** : 包含ROS、[rqt](http://wiki.ros.org/rqt)、[rviz](http://wiki.ros.org/rviz)、机器人通用库、2D/3D 模拟器、导航以及2D/3D感知
>
>```
>sudo apt-get install ros-kinetic-desktop-full
>```
>
>**桌面版安装:** 包含ROS、[rqt](http://wiki.ros.org/rqt)、[rviz](http://wiki.ros.org/rviz)以及通用机器人函数库。
>
>```
>sudo apt-get install ros-kinetic-desktop
>```
>
>**基础版安装: (简版)** 包含ROS核心软件包、构建工具以及通信相关的程序库，无GUI工具。
>
>```
>sudo apt-get install ros-kinetic-ros-base
>```
>
>**单个软件包安装:** 你也可以安装某个指定的ROS软件包（使用软件包名称替换掉下面的PACKAGE）:
>
>```
>sudo apt-get install ros-kinetic-PACKAGE
>```

### 4.初始化 rosdep

在开始使用ROS之前你还需要初始化rosdep。rosdep可以方便在你需要编译某些源码的时候为其安装一些系统依赖，同时也是某些ROS核心功能组件所必需用到的工具

```
sudo rosdep init
rosdep update
```

### 5.环境配置

每次打开一个新的终端时ROS环境变量都能够自动配置好（即添加到bash会话中），那将会方便很多：

```
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 6.构建工厂依赖

```
sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential
```

## 三、小海龟例子 

一个终端

roscore

第二个终端

rosrun turtlesim turtlesim_node

再开起一个终端控制

rosrun turtlesim turtle_teleop_key

在第三个终端里键盘控制上下左右小海龟就能运动了。

如果自己测试出现了ERROR如下：

[ERROR] [1542765270.211635192]: [registerPublisher] **Failed to contact master at [localhost:11311].** Retrying...

![](https://img-blog.csdnimg.cn/20181121100517141.png)

那么首先检查是否打开roscore，执行命令如下:

![](https://img-blog.csdnimg.cn/20181121100636589.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hhaXlpbnNodXNoZQ==,size_16,color_FFFFFF,t_70)

然后再进行小海龟的测试

![](https://img-blog.csdnimg.cn/20181121100933945.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hhaXlpbnNodXNoZQ==,size_16,color_FFFFFF,t_70)



如果出现小海龟，则证明安装完成。

# 依赖包安装

更新源

<https://blog.csdn.net/u012308586/article/details/102953882>

1. 备份原始源文件 sources.list

   ```
   sudo  cp  /etc/apt/sources.list    /etc/apt/sources.list.bak
   ```

2. 修改源文件sources.list

   1. 终端执行命令：

      ```
      sudo   chmod   777   /etc/apt/sources.list
      ```

   2. 执行命令：

      ```
      sudo   gedit   /etc/apt/sources.list
      ```

   3. 删除原来的文件内容，复制下面的任意一个到其中并保存（我用的是阿里源）

      阿里源

   ```
   deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
   
   deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
   
   deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
   
   deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
   
   deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
   
   deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
   
   deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
   
   deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
   
   deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
   
   deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
   ```

   > ​		清华源
   >
   > ```
   > deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
   > 
   > deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
   > 
   > deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
   > 
   > deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
   > 
   > deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
   > 
   > deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
   > 
   > deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
   > 
   > deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
   > 
   > deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
   > 
   > deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
   > ```

3. 更新源

   终端执行命令：

   ```
   sudo apt update
   ```

其他换源方法：

   打开"软件更新器"，依次点击"设置"，"Ubuntu软件"，在"下载自"后面的窗口选择 "其它站点"在其中找到清华大学镜像站选择即可。
   修改完软件源后，更新软件列表和软件

   ```
sudo apt update
sudo apt upgrade
   ```

   