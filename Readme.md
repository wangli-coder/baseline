# Paper reading

#### EfficientDet: Scalable and Efficient Object Detection

基于Efficient net的目标检测系列模型，文中对目前常用的FPN方法做了讨论，并基于PANet的FPN进行了简化，加入了skip connection，并使用了类似SE的注意力机制方法(去除了softmax的指数运算，提高速度)，对不同的feature map进行权重融合，命名为BiFPN。在 Compound Scaling方面提出了适用于Efficient net系列的scaling公式，最终在COCO上达到 51 mAP，并且保证了FPS。

#### Double-Head RCNN Rethinking Classification and Localization for Object Detection

目前的大多数检测模型都使用了全卷积网络，本文就着重讨论了FC和Conv对分类和回归分支的不同影响，发现FC更适合分类分支，而Conv更适合回归分支，并且Conv的分类结果也可以提高FC分类分支的结果，因此提出了一种Double head RCNN，在FC做分类分支的情况下，结合non-local对回归分支做了复杂的设计，同时提出一种结果融合的方法。文中对于FC和Conv的讨论还是比较有意思的。

#### MFPN: A NOVEL MIXTURE FEATURE PYRAMID NETWORK OF MULTIPLE ARCHITECTURES FOR OBJECT DETECTION

针对于FPN的改进，传统的FPN-based网络只单纯的针对于小目标检测的提高，从而使用从上至下的融合预测，文中对大中小三类目标物针对性的设计和优化了FPN的结构，对于小目标在FPN的基础上在最高层的特征图上做了一个GAP，用以保存语义信息，中目标设计了一个fusion-splitFPN，将前两层和后两层FPN分别融合得到$a_s$和$a_l$，将得到的特征图cat之后再拆分为四个特征图，大目标设计了和FPN类似的bottom-up的结构，基本与FPN相反，最终将三种FPN结构进行分特征图相加，进行检测，COCO最终结果47.6mAP，较原始提升有2%左右，文章设计性太强，结果还不错，算是针对于FPN做了一些探索。

#### Filter Response Normalization Layer: Eliminating Batch Dependence in the Training of Deep Neural Networks
batch normalization层在计算资源有限的情况下训练效果会急速下降，而instance normalization，group normalization等等在较大batch时，效果仍然略差于BN，这篇文章提出了一种新型的归一化层，不管在batch大还是小的情况下，都能够稳定训练，并且效果较BN层都有提升，被称为FRN，其主要的设计类似于IN层，在（H, W）的维度进行归一化，同时计算上抛去了减均值的操作，并且使用的二范数来替代方差，改进了relu函数来避免过多的激活为0的情况，因此FRN是由normalization层和激活函数一起构成，文中还讨论了特殊情况下的FRN，在公开数据上的效果是略有提升，在batch较小时，超越了IN, GN等，在batch较大时，超越了BN，能否被广泛使用，还需要时间的验证。