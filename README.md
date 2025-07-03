_此项目为重装后视觉版环境配置方法参考_

_此方法基于ubuntu22.04系统_

_此文档本意为了跑通视觉自瞄代码，亦可用于自己电脑环境配置_

###
###

**1.获取资源**

需要的资源有自瞄代码，clash，VScode，mindvision相机驱动，hik相机驱动，opencv，openvino，g2o，sophus

建议把这些资源整理到你的U盘里，部分资源可加我qq获取，我的qq：1423031539

###
###

**2.下载QQ**

安装QQ时，对deb文件进行下载，下载好后可使用如下命令进行安装
```
sudo dpkg -i （下载好的安装包名称）
```

###
###

**3.传输文件**

将下载好的资源包用QQ或其他方式传输至ubuntu系统

对于deb文件的安装，在此不做过多赘述，参考QQ的安装方式。

注意，对于梯子的安装可能产生以下报错

![b19d6b648a9febb6725acfb9032aba05_720](https://github.com/user-attachments/assets/8bde8dcc-bf0c-4714-8d11-70575ad113fe)

报错后输入这两个命令修复

```
sudo apt update
```

```
sudo apt install -f
```

下面介绍迈德威视相机包，opencv资源包，openvino资源包的安装方法

###
###

**4.下载cmake**

当我们直接使用sudo apt-get install cmake命令下载cmake时无法下载其最新版本，因此我们使用如下方法下载

```
sudo apt-get update
```
```
sudo apt-get -y install software-properties-common lsb-release
```
```
sudo apt-add-repository "deb https://apt.kitware.com/ubuntu/ $(lsb_release -cs) main"
```
```
wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc | sudo apt-key add -
```
```
sudo apt-get update
```
```
sudo apt-get install cmake
```

###
###

**5.opencv资源包**

解压opencv压缩包，进入该文件夹下创建build文件夹

![image](https://github.com/user-attachments/assets/c072e756-faa1-4946-a52f-e7692056c975)

然后在终端打开build文件夹依次输入

```
sudo cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..
```
```
sudo make 
```
```
sudo make install
```

至此opencv便安装好了

安装opencv时可能出现以下报错，原因是CMake没有找到可用的 C++ 编译器

![c3a54858f7865b7b65593c799a290374](https://github.com/user-attachments/assets/aba55f35-d52a-4121-a19d-a3e80b1c0c34)

运行以下命令便可解决

```
sudo apt update
```

```
sudo apt install build-essential
```

###
###

**6.openvino资源包**

在/计算机/opt文件路径下创建文件夹intel (打开终端输入sudo mkdir intel)

![image](https://github.com/user-attachments/assets/843f287f-787f-41a1-9a02-ffbb09a55363)


然后将解压好的openvino资源包移动到intel文件夹下 (可使用命令sudo cp -r （openino资源包路径）（intel文件夹路径）)

完成移动后打开该文件夹，再打开install_dependencies文件夹

![image](https://github.com/user-attachments/assets/5df0d378-9026-4a7b-ab74-c8afc9a57fda)


然后输入命令
```
sudo -E ./install_openvino_dependencies.sh
```

依赖安装完成后，在 主目录/.bashrc文件中添加如下环境变量（注意显示隐藏文件）

```
source /opt/intel/openvino_toolkit_2023.3.0(解压后的文件名)/setupvars.sh
```
![image](https://github.com/user-attachments/assets/14ec6be2-695f-410a-a89a-fc8c0bf8e8e9)

点击保存，至此openvino环境配置完毕

###
###

**7.迈德威视相机驱动安装**

解压Mindvision压缩包，进入该文件夹下

![image](https://github.com/user-attachments/assets/6ef6273e-4217-47f5-95b5-e675913be050)

然后输入以下命令

```
chmod +x install.sh
```
```
sudo ./install.sh
```

至此，迈德威视相机驱动就安装好了

###
###


**8.一键安装ros humble版本**

此处使用鱼香ros大佬的一键下载命令下载即可
```
wget http://fishros.com/install -O fishros && . fishros
```

###
###

**9.下载git**
```
sudo apt install git
```

###
###

**10.下载camera-info-manager包**

```
sudo apt install ros-humble-camera-info-manager
```
###
###

**11.下载xacro包**

```
sudo apt install ros-humble-xacro
```

###
###

**12.fmt库**
```
sudo apt install libfmt-dev
```
###
###

**13.Sophus库 (G2O库依赖)**
```
git clone https://github.com/strasdat/Sophus
```
```
cd Sophus
```
```
mkdir build && cd build
```
```
cmake ..
```
```
make 
```
```
sudo make install
```

###
###

**14.G2O库 (优化装甲板Yaw角度)**
```
sudo apt install libeigen3-dev libspdlog-dev libsuitesparse-dev qtdeclarative5-dev qt5-qmake libqglviewer-dev-qt5
```
```
git clone https://github.com/RainerKuemmerle/g2o
```
```
cd g2o
```
```
mkdir build && cd build
```
```
cmake ..
```
```
make 
```
```
sudo make install
```
###
###

**15.Ceres库 (能量机关曲线拟合)**

```
sudo apt install libceres-dev
```

###
###

**16.foxglove-bridge**

```
sudo apt install ros-humble-foxglove-bridge
```

###
###

_至此，环境配成！_

###
