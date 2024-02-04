---
title: YOLOV8优化(2),自定义boxes和mask颜色
date: 2024-2-4 13:57:50
categories:
  - YOLOV8优化
tags:
  - YOLOV8 
cover: https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.3zcijscluza0.webp
---

有时候我们在推理时发现目标物体与检测框、掩码颜色相近，甚至相同，影响观测体验。

这篇文章来教大家如何自定义boxes和mask颜色

# 第一步

首先我们找到并打开`ultralytics/utils/plotting.py`文件

在`Colors类`之后添加`Color`类，在`colors = Colors()`后添加`color = Color()`，注意C要大写的

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.591ctyx7qg00.webp)

如果想自定义修改颜色可以在 `def __init__(self):`添加`self.*`常量，颜色选择为RGB格式

再添加类似

```
if i == *:
         return self.* if not bgr else self.*[::-1]

```

就可以了

class Color如下：

```
class Color:
    def __init__(self):
        self.red = (255, 0, 0) # 红色
        self.green = (0, 255, 0) # 绿色
        self.bru = (0,0,255)

    def __call__(self, i, bgr=False):
        if i == 0:
            return self.red if not bgr else self.red[::-1]
        elif i == 1:
            return self.green if not bgr else self.green[::-1]
        elif i == 2:
        	return self.green if not bgr else self.bru[::-1]
        else:
            raise ValueError("i 暂时只能取 0 1 2")
```

# 第二步

找到并打开`ultralytics/engine/results.py`

导入我们上一步创建好的Color类

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.w5us4fwft9s.webp)

`ctrl+f`搜索`annotator.masks`

把`annotator.masks`修改为

```
annotator.masks(pred_masks.data, colors=[color(1, True)], im_gpu=img_gpu)
#1为上一步我们设置过的颜色绿色

#若要设置多个标签的颜色，我们可以这样设置，将会顺序设置我们上一步设置的颜色
annotator.masks(pred_masks.data, colors=[color(x, True) for x in idx], im_gpu=im_gpu)

```

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.63jmgnjar1k0.webp)

`ctrl+f`搜索`annotator.box_label`

把`annotator.box_label`修改为

```
#单标签设置为1绿色
annotator.box_label(d.xyxy.squeeze(), label, color=color(1, True))
#多标签颜色顺序设置                annotator.box_label(d.xyxy.squeeze(), label, color=color(c, True))
```

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.qk04ygb87ao.webp)



最后我们运行推理就可以了。

希望我的文章对你有所帮助。有问题联系我，邮箱在(1)号文章结尾。