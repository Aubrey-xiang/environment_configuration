_此项目为重装后视觉版环境配置方法参考_

_此方法同时适用于ubuntu22与ubuntu24系统_

_对于其他系统的安装可以查看该仓库的其他分支_

_此文档本意为了跑通MA战队2026赛季视觉自瞄代码_

###
###

**1.主要**

需获取的资源有clash，VScode，mindvision相机驱动，hik相机驱动，openvino

建议安装顺序为QQ，clash，VScode，mindvision相机驱动，hik相机驱动，openvino, 其他（参考步骤2）

对于软件，驱动以及openvino的安装这里不再赘述，不会可以参考ma_vision_2025分支

注意，ubuntu22的clash的安装可能产生以下报错

![b19d6b648a9febb6725acfb9032aba05_720](https://github.com/user-attachments/assets/8bde8dcc-bf0c-4714-8d11-70575ad113fe)

报错后输入这两个命令修复

```
sudo apt update
```

```
sudo apt install -f
```


###
###


**2.其他**

```
sudo apt install -y \
    git \
    g++ \
    cmake \
    can-utils \
    libceres-dev \
    libopencv-dev \
    libfmt-dev \
    libeigen3-dev \
    libspdlog-dev \
    libyaml-cpp-dev \
    libusb-1.0-0-dev \
    nlohmann-json3-dev \
    openssh-server \
    screen
```


###
###

