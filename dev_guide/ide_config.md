# IDE 配置

CLion的下载以及基本配置可参考[Install CLion](https://www.jetbrains.com/help/clion/installation-guide.html)。

## 自动格式化
+ 转到 **File | Settings | Plugins**，在 **Marketplace** 中搜索并安装 **Save Actions**
+ 重启IDE，转到 **File | Setttings | Save Actions**，勾选以下选项：

![save_actions](https://s3.ax1x.com/2020/11/16/Dk9fXD.png)

+ 转到 **File | Settings | Editor | Code Style | C/C++**，点击右侧的     **Set from...**  并选择  **Google**  


## ROS 配置

+ 转到 **File | Settings | Build, Execution, Deployment | CMake**
+ 将 **CMake options** 的值更改为 `-DCATKIN_DEVEL_PREFIX=../devel`
+ 将 **Build directory** 的值更改为`../build`

## 远程开发

+ 远程开发可参考[Full remote mode](https://www.jetbrains.com/help/clion/remote-projects-support.html)。
