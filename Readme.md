# Paper reading

#### EfficientDet: Scalable and Efficient Object Detection

基于Efficient net的目标检测系列模型，文中对目前常用的FPN方法做了讨论，并基于PANet的FPN进行了简化，加入了skip connection，并使用了类似SE的注意力机制方法(去除了softmax的指数运算，提高速度)，对不同的feature map进行权重融合，命名为BiFPN。在 Compound Scaling方面提出了适用于Efficient net系列的scaling公式，最终在COCO上达到 51 mAP，并且保证了FPS。

#### Double-Head RCNN Rethinking Classification and Localization for Object Detection

目前的大多数检测模型都使用了全卷积网络，本文就着重讨论了FC和Conv对分类和回归分支的不同影响，发现FC更适合分类分支，而Conv更适合回归分支，并且Conv的分类结果也可以提高FC分类分支的结果，因此提出了一种Double head RCNN，在FC做分类分支的情况下，结合non-local对回归分支做了复杂的设计，同时提出一种结果融合的方法。文中对于FC和Conv的讨论还是比较有意思的。