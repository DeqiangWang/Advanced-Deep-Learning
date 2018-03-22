# Neural Machine Translation by Jointly Learning to Align and Translate

简介

在传统的RNN Encoder-Decoder模型中，在编码的过程中，将t-1时的状态h\_{&lt;t-1&gt;}和t时刻的数据x\_{&lt;t&gt;}输入到t时刻的RNN单元中，得到t时刻的状态h\_{&lt;t&gt;}，经过T个时间片后，得到长度等于隐节点数量的特征向量\mathbf{c}。在解码的过程中，将特征向量\mathbf{c}和上个时间片预测的输出y\_{&lt;t'-1&gt;}输入到RNN的单元中，得到该时刻的输出y\_{&lt;t'&gt;}，经过T'个时间片后得到输出结果。但在一些应用中，比如句子长度特别长的机器翻译场景中，传统的RNN Encoder-Decoder表现非常不理想。一个重要的原因是t’时刻的输出可能更关心输入序列的\[t1, t2\]部分是什么内容而和其它部分是什么关系并不大。例如在机器翻译中，当前时间片的输出可能仅更注重原句子的某几个单词而不是整个句子。

这篇论文率先提出了Attention的思想，通过Attention机制，模型可以同时学习原句子和目标句子的对齐关系和翻译关系。在编码过程中，将原句子编码成一组特征向量的一个集合，在翻译时，每个时间片会在该集合自行选择特征向量的一个子集用于产生输出结果。




