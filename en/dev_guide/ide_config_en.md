# IDE configuration

## Environment construction

1. Open a terminal and execute the following commands:

```bash
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install cmake
sudo apt-get install bison
sudo apt-get install library*
sudo apt-get install libncurses5-dev
sudo apt-get install g++
sudo apt-get install kdelibs5-dev
sudo apt-get install make
```

## Install CLion

1. [Download the tarball](https://www.jetbrains.com/clion/download/) **.tar.gz** .

2. Unpack the downloaded **CLion-*.tar.gz** archive. The recommended extract directory is /opt: 

   ```bash
   sudo tar xvzf CLion-*.tar.gz -C /opt/
   ```

   > [!Warning]
   >
   > Do not extract the tarball over an existing installation to avoid conflicts. Always extract to a clean directory.

3. Execute the **CLion.sh** from **bin** subdirectory to run CLion:

   ```bash
   sh /opt/clion-*/bin/clion.sh
   ```

   When you run CLion for the first time, some steps are required  to complete the installation, customize your instance, and start working with the IDE.     

   For more information, see [Run CLion for the first time](https://www.jetbrains.com/help/clion/run-for-the-first-time.html).

## Configure the IDE

1. Create a C++ Executable project. You can set the location and language standard of the new project.

    ![Image](../../img/ide_config/new_project.png)

2. Press **File->Settings->Build,Execution,Deployment->Toolchains** and fill the corresponding locations.

   ![Image](../../img/ide_config/toolchain.png)

   > [!Note]
   >
   > No red error indicates successful configuration.

3. Press **Run->Edit Configurations**, click the **＋** button and create a **CMake Application**.

    ![Image](../../img/ide_config/debug_config.png)

4. Press **Run->Run 'Debug'** to run the program. If the output is the same as below, the configuration is successful.

    ![Image](../../img/ide_config/output.png)


## Remote compilation

Suppose the name of the program you want to debug is 'Test', the server IP is 10.10.100.10, and the external service port is 8888. 

### Server configuration

1. Install gdbserver.

   ```bash
   sudo apt-get install gdbserver
   ```

2. Run gdbserver for remote compilation.  

   ```bash
   # gdbserver IP:PORT PROGRAM_NAME
   gdbserver 10.10.100.10:8888 /usr/Test/test
   ```

   > [!Note]
   >
   > Remote debugging depends on GDBSERVER. The program started by GDBSERVER will wait for the connection of remote debugging first, and then start the process after the connection is successful.

### Local configuration

#### Deployment configuration

​	Press **Tools->Deployment->Configuration**. 

1. Click the **＋** button and choose **SFTP** type to add a web server.

    ![Image](../../img/ide_config/deployment.png)

2. Click `...` and add a **SSH configuration**. Fill the server's **Host, Port, User name** and  **Password**. Press **Test Connection** to confirm the connection.

    ![Image](../../img/ide_config/ssh_config.png)

3. Switch to **Mappings**, fill the **Local path**(local code path) and **Deployment path**(remote code path).

    ![Image](../../img/ide_config/mapping.png)


#### Code synchronized

1. Press **Tools->Deployment->Upload to Server/Download from Server**.

2. Enable **Tools->Deployment->Automatic Upload** to ensure that code is automatically synchronized to the server.

    ![Image](../../img/ide_config/auto_upload.png)

#### Debug configuration

1. Press **Run->Edit Configuration**.

2. Click the **＋** button and create a **GDB Remote Debug**.

3. Setting **'target remote' args** and **Path mappings**.

    ![Image](../../img/ide_config/debug_config_remote.png)

4. Press **Run->Run 'Debug'** to run the program remotely.

