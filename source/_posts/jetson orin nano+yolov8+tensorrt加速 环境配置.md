---
title: jetson orin nano+yolov8+tensorrt加速 环境配置
date: 2024-2-3 17:47:27
categories:
  - jetson
tags:
  - jetson orin nano
  - yolov8
  - tensorrt加速
description: jetson orin nano+yolov8+tensorrt加速 全流程环境配置
cover: https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/jetson-orin-nano.5ijm82fw4o00.webp
---

# jetson orin nano+yolov8+tensorrt加速 环境配置

### 1.烧录系统（不做示范，网上有很多教程）

硬件环境：

jetson orin nano 8G

jetpack：5.1.1



### 2.安装jetpack（包含CODA和cudnn）

```
sudo apt update
sudo apt install nvidia-jetpack
```



### 3.安装jtop

```
sudo apt-get install python3-pip
sudo pip3 install -U pip
sudo pip install -U jetson-stats
```



### 4.下载miniforge

下载地址： https://github.com/conda-forge/miniforge

选择**Linux aarch64**（arm64）版本，运行`shell`（sh）文件，再两次选择*yes*完成安装。

```
创建虚拟环境
conda create -n yolov8 python=3.8
激活环境
conda activate yolov8
我们将在虚拟环境中安装

-------------------------------------------拓展------------------------------------------
删除环境
conda remove -n yolo --all
查看所有环境
conda info --envs
```



#### 5.Ultralytics安装

安装Ultralytics、onnx、lapx 以及调整numpy为1.23.1。下载速度慢的可以使用使用清华源。

```
pip install ultralytics onnx lapx numpy==1.23.1 -i https://pypi.tuna.tsinghua.edu.cn/simple
```

运行指令后`pip list`发现torch已安装，但是Ultralytics自带的torch版本是不支持GPU，所以我们需要手动安装torch



### 6.torch、torchvision安装(已打包)

#### 6.0如何判断我们需要的版本

通过jetpack版本判断我们需要的torch版本，再通过torch版本找到对应的torchvision版本

jetpack对应torch： https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

torch对应torchvision：https://github.com/pytorch/vision

下载torchvision：

```
（whl） ：https://download.pytorch.org/whl/torchvision/

（源代码编译）：https://github.com/pytorch/vision
点main按钮，选择Tags，找到需要的版本，下载就可以。
```

我最终选择：torch2.0.0+nv23.05、torchvision0.15.1 （已打包）

#### 6.1安装torch

##### 6.1.1安装系统支持包

```
sudo apt-get -y update; 

sudo apt-get -y install autoconf bc build-essential g++-8 gcc-8 clang-8 lld-8 gettext-base gfortran-8 iputils-ping libbz2-dev libc++-dev libcgal-dev libffi-dev libfreetype6-dev libhdf5-dev libjpeg-dev liblzma-dev libncurses5-dev libncursesw5-dev libpng-dev libreadline-dev libssl-dev libsqlite3-dev libxml2-dev libxslt-dev locales moreutils openssl python-openssl rsync scons python3-pip libopenblas-dev;
```

因为国内网络环境原因，失败了就多执行几次。

##### 6.1.2 配置环境变量

```
#注意，我们安装的JetPack 5.1.1，所以找对版本对应
export TORCH_INSTALL=https://developer.download.nvidia.cn/compute/redist/jp/v511/pytorch/torch-2.0.0+nv23.05-cp38-cp38-linux_aarch64.whl
```

##### 6.1.3在线安装（推荐先进行在线安装，实在不行选择本地安装）

```
python3 -m pip install --upgrade pip; python3 -m pip install aiohttp numpy=='1.19.4' scipy=='1.5.3' export "LD_LIBRARY_PATH=/usr/lib/llvm-8/lib:$LD_LIBRARY_PATH"; python3 -m pip install --upgrade protobuf; python3 -m pip install --no-cache $TORCH_INSTALL
```

报错没关系，多尝试几次，肯定成功

显示`successful install .....................`

##### 6.1.4本地安装

（1）把打包好的torch拉取到jetson上

（2）cd到拉取目录

pip安装：

```
pip3 install  torch-2***********.whl
```

##### 6.1.5测试是否安装成功

返回版本号说明成功

```
test_torch.pt

#输入库

import torch

#查看版本

print(torch.__version__)

#查看gpu是否可用

print(torch.cuda.is_available())

#返回设备gpu个数

print(torch.cuda.device_count())

# 查看对应CUDA的版本号

print(torch.backends.cudnn.version())

print(torch.version.cuda)

#退出python

quit()

```

##### 6.1.6卸载torch（按需执行）

```
pip uninstall torch
```



#### 6.2安装torchvision

（1）把打包好的torchvision拉取到jetson上

（2）cd到拉取目录

##### 6.2.1方式一：whl安装

```
pip3 install torchvision***********.whl
```

##### 6.2.2方式二：源代码编译

```
unzip vision-0.15.1.zip

cd vision-0.15.1

export BUILD_VERSION=0.15.1

python3 setup.py install --user
如果失败多尝试几次
```

##### 6.2.3测试是否安装成功

返回版本号说明成功

```
import torchvision

print(torchvision.__version__)
```



### 7.安装tensorrt

我已经打包好了，拉取到jetson即可

```
pip install tensorrt*********.whl
```

最后检测环境

```
pip list
查看环境是否包含torch、torchvision、tensorrt。
```

### 8.安装vscode

直接去vscode官网，点更多版本，下载linux arm64版本的.deb安装包，下载后在当前路径输入命令安装

```
sudo dpkg -i 文件名
```

vscode配置:

安装python插件，等待加载，自动检测设备的所有python环境，我们选择刚刚创建的yolov8环境，最后运行脚本

### 9.TensoRT加速

我们在PC训练好的best.pt模型上传到Jetson上，再利用TensorRT将转换为`.engine`模型。

```
pt2engine.py
from ultralytics import YOLO

# Load a model
model = YOLO('best.pt')  # load a custom trained
#/home/nvidia/Desktop/install_text/model/
# Export the model
model.export(format='engine',half=True,simplify=True)
```

推理脚本：

```
import cv2
from ultralytics import YOLO
from cv2 import getTickCount, getTickFrequency
# 加载 YOLOv8 模型
model = YOLO("best.engine",task='segment')


# 获取摄像头内容，参数 0 表示使用默认的摄像头
cap = cv2.VideoCapture(0)



while cap.isOpened():
    loop_start = getTickCount()
    success,frame = cap.read()  # 读取摄像头的一帧图像
    
#,imgsz=(736,1280)

    if success :
        results = model.predict(frame,conf=0.8) # 对当前帧进行目标检测并显示结果  
    annotated_frame = results[0].plot(boxes=False)#

    # 中间放自己的显示程序
    loop_time = getTickCount() - loop_start
    total_time = loop_time / (getTickFrequency())
    FPS = int(1 / total_time)
    # 在图像左上角添加FPS文本
    fps_text = f"FPS: {FPS:.2f}"
    font = cv2.FONT_HERSHEY_SIMPLEX

    font_scale = 1
    font_thickness = 2
    text_color = (0, 255, 0)  # 绿色
    text_position = (10, 30)  # 左上角位置

    cv2.putText(annotated_frame, fps_text, text_position, font, font_scale, text_color, font_thickness)
    cv2.namedWindow("img",cv2.WINDOW_NORMAL)
    cv2.imshow('img', annotated_frame)
    # 通过按下 'q' 键退出循环
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()  # 释放摄像头资源
cv2.destroyAllWindows()  # 关闭OpenCV窗口
```

