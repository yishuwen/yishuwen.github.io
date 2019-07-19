---
layout:     post
title:      Batch Normalization 神经网络 
subtitle:   
date:       2019-07-19
author:     Yi
header-img: img/post-bg-math.jpg
catalog: true
tags:
    - 神经网络
    - 机器学习
---
### 动机
神经网络在训练过程中，中间层的激活输出的分布是不断变化的，因此后面的网络层需要根据前层输出的分布不断调整。当前层激活输出落入后层饱和区后，造成反向传播算法梯度难以向前传递。所以对神经网络的每一层作批归一化，可以稳定各层的输出的分布，同时避免激活输出落入饱和区，实现神经网络的快速训练。

### 训练
对于单层所有激活输出，各维特征独立作以下变换

``` math
\hat{x}^{(k)} = \frac{x^{(k)}-E[x^{(k)}]}{\sqrt{Var[x^{(k)}]}}
```

上式，期望方差以batch中不同样本均值方差代替。

由于经过归一化后使得激活输入落入了激活函数的线性段（例如sigmoid），难以实现神经网络的非线性输出，所以增加以下线性变换，使部分样本激活输入得以落入非线性段，其中gamma与beta为训练变量
``` math
y^{(k)}=\gamma^{(k)}\hat{x}^{(k)} + \beta^{(k)}
```

<img src="/img/BatchNormalization/Fig1.png"  height="400" width="495">

Note: 在训练过程中保存均值、方差以便在推断中使用。



使用时，Batch normalization在激活之前，线性层之后。
Note：卷积神经网络：每个feature map共享一组参数。

论文链接：[Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](http://de.arxiv.org/pdf/1502.03167)

---
