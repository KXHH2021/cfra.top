---
title: yolov8seg仅分割不显示检测框（boxes）
date: 2024-2-3 20:55:08
categories:
  - yolov8seg
tags:
  - boxes
description: yolov8实例分割关闭boxes显示
cover: https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/bus1.4aughhphiyw0.webp
---

# yolov8seg仅分割不显示检测框（boxes）

有时候我们使用yolov8seg的分割功能，不需要显示boxes框，但是yolov8seg默认是这样的情况：

![https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/bus1.4aughhphiyw0.webp](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/bus1.4aughhphiyw0.webp)



检测框和置信度很碍眼，我们有是否方法去除呢？

我们不妨仔细查看

[YOLOv8的官方文档]: https://docs.ultralytics.com/zh

就会有所收获：

点击`预测`主题，可视化参数：

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/PixPin_2024-02-03_21-11-44.8872peguo9w.webp)

我们注意`show_boxes`这个参数，我们添加`boxes=False`

![https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.3oyjrh715620.webp](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.3oyjrh715620.webp)

运行结果：

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/bus2.56qqtq3qufc0.webp)

果然把boxes框去掉了。

我们yolo新手很容易忽略官方文档的存在，而跑去网上搜索，还不一定有你想要的答案，有时候解决问题的方法只是调一个参数的事情，我非常建议yolo新手有空能够仔细看看官方文档，我本人也是经常看看官方文档有什么解决方法，而后再去网上搜索。

希望我的文章对你有所帮助，有问题可以联系我的邮箱：kxhh2025@gmail.com。