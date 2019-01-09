# Layer Normalization

## 前言

在上一篇的文章中我们介绍了BN\[2\]的计算方法并且讲解了BN如何应用在MLP以及CNN中如何使用BN。在文章的最后，我们指出BN并不适用于RNN等动态网络和batchsize较小的时候效果不好。Layer Normalization（LN）\[1\]的提出有效的解决BN的这两个问题。

## 1. BN的问题

以图1为例我们仔细分析BN为什么有不适用于RNN和不适用于batchsize较小的场景的原因。图1是一个简单的RNN网络，其中一个含有5个样本（$$N$$）组成的一个batch，在这个例子中每个样本都包含4个特征（$$C$$），但是每个样本的长度不同（$$T$$）。在BN中是按照特征进行归一化的，也就是沿着平行于$$y$$轴的方向进行归一化。

![](/assets/LN_1.png)

## Reference

\[1\] Ba J L, Kiros J R, Hinton G E. Layer normalization\[J\]. arXiv preprint arXiv:1607.06450, 2016.

\[2\] Ioffe S, Szegedy C. Batch normalization: Accelerating deep network training by reducing internal covariate shift\[J\]. arXiv preprint arXiv:1502.03167, 2015.
