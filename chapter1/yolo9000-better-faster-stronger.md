# YOLO9000: Better, Faster, Stronger

## 前言

在这篇像极了奥运格言（Faster，Higher，Stronger）的论文[1]中，作者提出了YOLOv2和YOLO9000两个模型。

其中YOLOv2采用了若干技巧对[YOLOv1](https://senliuy.gitbooks.io/advanced-deep-learning/content/chapter1/you-only-look-once-unified-real-time-object-detection.html)的速度和精度进行了提升。其中比较有趣的右一下几点：

1. 使用聚类产生的锚点代替[Faster R-CNN](https://senliuy.gitbooks.io/advanced-deep-learning/content/chapter1/faster-r-cnn-towards-real-time-object-detection-with-region-proposal-networks.html)和[SSD](https://senliuy.gitbooks.io/advanced-deep-learning/content/chapter1/ssd-single-shot-multibox-detector.html)手工设计的锚点；
2. 在高分辨率图像上进行迁移学习，提升网络对高分辨图像的响应能力；
3. 训练过程图像的尺寸不再固定，提升网络对不同训练数据的泛化能力。

除了以上三点，YOLO还使用了残差网络的直接映射的思想，R-CNN系列的预测相对位移的思想，Batch Normalization，全卷积等思想。YOLOv2将算法的速度和精度均提升到了一个新的高度。

## Reference

\[1\] Redmon J, Farhadi A. YOLO9000: better, faster, stronger\[J\]. arXiv preprint, 2017.