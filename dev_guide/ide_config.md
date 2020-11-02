# IDE 配置

## 配置IDE

1. 创建C++可执行项目。可以设置新项目的位置和语言标准。

    ![Image](../img/ide_config/new_project.png)

2. 点击 **File | Settings | Build,Execution,Deployment | Toolchains** 并填写相应的文件路径。

   ![Image](../img/ide_config/toolchain.png)

   > [!Note]
   >
   > 没有红色的警告信息则说明配置成功。

3. 点击 **Run | Edit Configurations**, 点击 **＋** 按钮并创建一个**CMake Application**。

    ![Image](../img/ide_config/debug_config.png)

4. 点击 **Run | Run 'Debug'** 以运行项目。如果输出结果与下图相同，则说明编译成功。

    ![Image](../img/ide_config/output.png)

## 远程开发

### 使用远程凭据创建工具链

1. 转到 **File | Settings | Build, Execution, Deployment | Toolchains** 并从工具链列表中选择 **Remote Host** ，或者单击![plus icon](https://www.jetbrains.com/help/img/idea/2020.2/artwork.studio.icons.common.add.svg)并从下拉菜单中选中 **Remote Host** ，以创建新的工具链。

2. 单击在 **Credentials** 右侧的 ![artwork.studio.icons.logcat.toolbar.settings.svg](https://www.jetbrains.com/help/img/idea/2020.2/artwork.studio.icons.logcat.toolbar.settings.svg) 标志。在打开的对话框中，创建 SSH 配置并提供用于访问远程计算机的凭据。现有 SSH 配置可从下拉列表中获得。

    ![Image](https://resources.jetbrains.com/help/img/idea/2020.2/cl_remote_toolchaincredentials.png)

    > [!Tip]
    >
    > 你还可以在 File | Settings / Preferences | Tools | SSH Configurations 中管理SSH配置。

3. 建立连接后，CLion 将尝试检测远程默认位置**/usr/bin/cmake** 和 **/usr/bin/gdb**中的工具（如果您手动提供了完整路径，则会在您给出的路径中检测工具）。检查成功完成后，工具链就可以使用了：![Image](https://resources.jetbrains.com/help/img/idea/2020.2/cl_remote_toolchainsuccess.png)

4. 您可以将新创建的工具链设置为**默认工具链**（可通过单击 ![move up](https://www.jetbrains.com/help/img/idea/2020.2/icons.actions.moveUp.svg)![move down](https://www.jetbrains.com/help/img/idea/2020.2/icons.actions.moveDown.svg)将远程工具链移动到列表顶部）。当远程工具链设置为默认工具链时，它将用于在 CLion 中创建和打开的所有项目。

    请注意，如果将远程工具链设置为默认工具链，则**默认的CMake配置文件**将自动连接到它，因此您不需要为它配置单独的 CMake 配置文件。 

### 创建相应的 CMake 配置文件

> [!Note]
>
> 如果您将远程工具链设置为默认工具链 ，请跳过此步骤。 

+ 转到 **File | Settings / Preferences | Build, Execution, Deployment | CMake**，单击 ![plus icon](https://www.jetbrains.com/help/img/idea/2020.2/artwork.studio.icons.common.add.svg)以创建新的CMake配置文件，并使用 **Toolchain** 将其链接到远程工具链：

    ![Image](https://resources.jetbrains.com/help/img/idea/2020.2/cl_remote_cmakeprofile.png)

### 检查和调整部署配置

+  转到**File | Settings / Preferences | Build, Execution, Deployment | Deployment**。当您为远程工具链创建实际连接时，CLion会将连接参数放入在该对话框下的[访问配置](https://www.jetbrains.com/help/clion/settings-deployment.html)列表中。

    使用 **Mappings** 选项卡更改代码自动同步的默认映射路径（例如，为复制的源代码设置一个特定的远程目录，而不是默认 **tmp** 文件夹）：

    ![path mapping for file synchronization](https://www.jetbrains.com/help/img/idea/2020.2/cl_remote_pathmappings.png)

+ 您可以在文件传输工具窗口中观察代码的**同步过程**（**View | Tool Windows | File Transfer**）：       

    ![file transfer tool window](https://www.jetbrains.com/help/img/idea/2020.2/cl_remote_filetransfer.png)

### 重新同步头文件搜索路径

+ 为了正确解析代码，CLion 将**头文件搜索路径**与远程计算机的所有内容同步到本地客户端。*例如，*即使标准库标头文件取自目标，您也可以导航到它们，就像在 CLion 编辑器中本地工作一样。

    但是，头文件搜索路径的同步可能非常耗时，因此 CLion 仅在初始文件传输时自动执行。之后，它不再由 CMake 重新加载触发。因此，每次切换编译器或在项目依赖项中进行更改时，请确保通过手动调用**Tools | Resync with Remote Hosts** 来更新头文件搜索路径。

    您也可以切换到自动同步：在注册表中设置*clion.remote.resync.system.cache*的值（转到**Help | Find Action**或按`Ctrl+Shift+A`，输入*Registry* 然后按名称搜索）。

### 生成，运行，调试

现在，您已经配置了远程工具链和相应的 CMake 配置文件，您可以通过在**Run/Debug** 配置切换器中选择正确的 CMake 配置文件，以完全远程的方式生成、运行和调试应用程序和测试：

![cmake profile for remote](https://www.jetbrains.com/help/img/idea/2020.2/cl_remote_profile.png)

此外，您可以使用[远程SSH 终端](https://www.jetbrains.com/help/clion/running-ssh-terminal.html)和[远程外部工具](https://www.jetbrains.com/help/clion/settings-tools-remote-ssh-external-tools.html)来完成运行/调试配置的**启动步骤**。       

下面提供一个演示，显示应用程序输出如何根据它运行的操作系统而变化。演示将 macOS 作为本地系统，远程连接到 Ubuntu 目标并检查 OS 名称。在此示例中，代码的输出结果取决于操作系统标识符，因此当我们切换 CMake 配置文件或[解析上下文时](https://www.jetbrains.com/help/clion/switching-resolve-context.html)，CLion 会突出显示相应的代码分支：

![image](A:/robomaster/RM-Software-Tutorial/img/ide_config/index.gif)