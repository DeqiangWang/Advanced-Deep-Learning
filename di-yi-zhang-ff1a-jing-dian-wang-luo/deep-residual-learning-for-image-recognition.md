# Deep Residual Learning for Image Recognition

## 前言

在VGG中，卷积网络达到了19层，在GoogLeNet中，网络史无前例的达到了22层。那么，网络的精度会随着网络的层数增多而增多吗？在深度学习中，网络层数增多一般会伴着下面几个问题

1. 计算资源的消耗
2. 模型容易过拟合
3. 梯度消失/梯度爆炸问题的产生

问题1可以通过GPU集群来解决，对于一个企业资源并不是很大的问题；问题2的过拟合通过采集海量数据，并配合Dropout正则化等方法也可以有效避免；问题3通过Batch Normalization也可以避免。貌似我们只要无脑的增加网络的层数，我们就能从此获益，但实验数据给了我们当头一棒。

作者发现，随着网络层数的增加，网络发生了退化（degradation）的现象：随着网络层数的增多，训练集loss逐渐下降，然后趋于饱和，当你再增加网络深度的话，训练集loss反而会增大。注意这并不是过拟合，因为在过拟合中训练loss是一直减小的。

当网络退化时，浅层网络能够达到比深层网络更好的训练效果，这时如果我们把低层的特征传到高层，那么效果应该至少不比浅层的网络效果差，或者说如果一个VGG-100网络在第98层使用的是和VGG-16第14层一模一样的特征，那么VGG-100的效果应该会和VGG-16的效果相同。所以，我们可以在VGG-100的98层和14层之间添加一条直接映射（Identity Mapping）来达到此效果。

基于这种使用直接映射来连接网络不同层直接的思想，残差网络应运而生。

## 1. 残差网络

### 1.1 残差块

残差网络是由一系列残差块组成的（图1）。一个残差块可以用表示为：

```
x_{l+1}= x_l+\mathcal{F}(x_l, {W_l})
```

残差块分成两部分直接映射部分和残差部分。h\(x\_l\)是直接映射，反应在图1中是左边的曲线；\mathcal{F}\(x\_l, {W\_l}\)是残差部分，一般由两个或者三个卷积操作构成，即图1中右侧包含卷积的部分。

###### 图1：残差块

\[ResNet\_1\]

图1中的'Weight‘在卷积网络中是指卷积操作，’addition‘是指单位加操作。

在卷积网络中，x\_l可能和x\_{l+1}的Feature Map的数量不一样，这时候就需要使用1\*1卷积进行升维或者降维（图2）。这时，残差块表示为：

```
x_{l+1}= h(x_l)+\mathcal{F}(x_l, {W_l})
```

其中h\(x\_l\) = W'\_lx。实验结果1\*1卷积对模型性能提升有限，所以一般是在升维或者降维时才会使用。

###### 图2：1\*1残差块

\[ResNet\_2\]

### 1.2 残差网络



## Reference

\[1\] He K, Zhang X, Ren S, et al. Deep residual learning for image recognition\[C\]//Proceedings of the IEEE conference on computer vision and pattern recognition. 2016: 770-778.

\[2\] He K, Zhang X, Ren S, et al. Identity mappings in deep residual networks\[C\]//European Conference on Computer Vision. Springer, Cham, 2016: 630-645.
