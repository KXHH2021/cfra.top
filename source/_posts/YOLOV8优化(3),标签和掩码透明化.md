---
title: YOLOV8优化(3),标签和掩码透明化
date: 2024-2-4 15:09:49
categories:
  - YOLOV8优化
tags:
  - YOLOV8
cover: https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.3zcijscluza0.webp
---

大家在检测一些密集目标时经常会遇到标签名互相遮挡的情况，给大家分享一个调整标签透明度的方法。

修改方式非常简单，只需要修改一个文件 `ultralytics/yolo/utils/plotting.py`

第一步将 `cv2.rectangle(self.im, p1, p2, color, thickness=self.lw, lineType=cv2.LINE_AA)` 这句注释掉，

换成下面这三句：

```
overlay = self.im.copy()

alpha = 0.7  # 透明度 数值越小 透明度越高

cv2.rectangle(overlay, p1, p2, color,thickness=self.lw, lineType=cv2.LINE_AA)
```

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.1twi923dkosg.webp)

第二步将

```
cv2.rectangle(self.im, p1, p2, color, -1, cv2.LINE_AA)  # filled
cv2.putText(self.im,
```

注释掉

换成

```
cv2.rectangle(overlay, p1, p2, color, -1, cv2.LINE_AA)  # filled
cv2.putText(overlay,
```

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.4qtagvhpmb20.webp)

最后添加`self.im = cv2.addWeighted(overlay, alpha, self.im, 1 - alpha, 0)`

效果：

![](https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.2u9omyv08f00.webp)





如果只要改变掩码的透明度，以上步骤不用做。

直接修改`def masks(self, masks, colors, im_gpu, alpha=0.3, retina_masks=False):`的`alpha`的值即可

![]((https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.1rlsp7d778jk.webp)https://cdn.jsdelivr.net/gh/KXHH2021/seveimg@main/img/image.1rlsp7d778jk.webp)
