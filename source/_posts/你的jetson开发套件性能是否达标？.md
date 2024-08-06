---
title: 你的jetson开发套件性能是否达标？
date: 2024-8-6 16:11:11
categories:
  - jetson
tags:
  - jetson
cover: https://sm.ms/delete/fkgy1IXq5UQErABdaJ9LDWFNc3
---

# 你的jetson开发套件性能是否达标？

本人在做项目时使用jetson orin nano 觉得性能不够，于是购买了某国内三字品牌的jetson orin nx，部署项目后发现性能还是没有太大的提升。于是，我在多个设备的测试下，发现不同品牌的同一种开发套件存在性能不达标情况，建议刚入手的可以测测性能，不达标可以马上退货。下面是测试方法：

## jetson benchmarks

这个是nvidia官方给出的一个基准测试方法，github地址：https://github.com/NVIDIA-AI-IOT/jetson_benchmarks

我们可以利用这个方法跑出分数再与nvidia给出的各设备分数进行对比，即可知道你的jetson开发套件是否达标了。

官方数据如下：

![.png](https://s2.loli.net/2024/08/06/vKfrds1MngEkBoF.png)

下面再讲如何使用jetson benchmarks：

## jetson benchmarks的使用

**可以结合github项目readme，不同的设备要下载的测试算法不同，运行命令也不同，下面是以orin-AGX举例。**

1.首先把github项目下载到设备上

```
git  clone  https://github.com/NVIDIA-AI-IOT/jetson_benchmarks
```

2.设置满功率，设备会重启

```
满功率设置
nvpmodel -q

sudo nvpmodel -m 0
```

3.下载测试算法

```
#1.在 jetson_benchmark 目录下
mkdir  models
sudo sh install_requirements.sh

#2.把下好的9个文件拷贝进models，进入models手动解压文件
cd models
unzip 文件名
```

4.运行

```
#3.返回jetson_benchmark 目录下
#orin-AGX
sudo python3 benchmark.py --all --csv_file_path benchmark_csv/orin-benchmarks.csv --model_dir (绝对路径)/models/  --jetson_clocks

上面的绝对路径就是你自己创建的models的路径
```

5.等待4个小时左右就会得到分数

与上面的图片进行对比，**如果分数差个几百，就说明你的设备不达标赶紧退货吧**，由于我当时测试距离现在已经是半年时间，我没有截图orin nx的基准测试分数，但是我这里测试了orin AGX的分数可以给大家参考一下

![AGX.png](https://s2.loli.net/2024/08/06/j1XySsednIOZUME.png)

分数和官方给的相差不大，说明这个设备是达标的。