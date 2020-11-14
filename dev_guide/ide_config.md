# IDE 配置

CLion的下载以及基本配置可参考[Install CLion](https://www.jetbrains.com/help/clion/installation-guide.html)。

## ROS 配置

+ 转到 **File | Settings | Build, Execution, Deployment | CMake**
+ 将 **CMake options** 的值更改为 `-DCATKIN_DEVEL_PREFIX=../devel`
+ 将 **Build directory** 的值更改为`../build`

## 远程开发

+ 远程开发可参考[Full remote mode](https://www.jetbrains.com/help/clion/remote-projects-support.html)。