# Paper reading

#### EfficientDet: Scalable and Efficient Object Detection

基于Efficient net的目标检测系列模型，文中对目前常用的FPN方法做了讨论，并基于PANet的FPN进行了简化，加入了skip connection，并使用了类似SE的注意力机制方法(去除了softmax的指数运算，提高速度)，对不同的feature map进行权重融合，命名为BiFPN。在 Compound Scaling方面提出了适用于Efficient net系列的scaling公式，最终在COCO上达到 51 mAP，并且保证了FPS。

#### Double-Head RCNN Rethinking Classification and Localization for Object Detection

目前的大多数检测模型都使用了全卷积网络，本文就着重讨论了FC和Conv对分类和回归分支的不同影响，发现FC更适合分类分支，而Conv更适合回归分支，并且Conv的分类结果也可以提高FC分类分支的结果，因此提出了一种Double head RCNN，在FC做分类分支的情况下，结合non-local对回归分支做了复杂的设计，同时提出一种结果融合的方法。文中对于FC和Conv的讨论还是比较有意思的。

#### MFPN: A NOVEL MIXTURE FEATURE PYRAMID NETWORK OF MULTIPLE ARCHITECTURES FOR OBJECT DETECTION

针对于FPN的改进，传统的FPN-based网络只单纯的针对于小目标检测的提高，从而使用从上至下的融合预测，文中对大中小三类目标物针对性的设计和优化了FPN的结构，对于小目标在FPN的基础上在最高层的特征图上做了一个GAP，用以保存语义信息，中目标设计了一个fusion-splitFPN，将前两层和后两层FPN分别融合得到$a_s$和$a_l$，将得到的特征图cat之后再拆分为四个特征图，大目标设计了和FPN类似的bottom-up的结构，基本与FPN相反，最终将三种FPN结构进行分特征图相加，进行检测，COCO最终结果47.6mAP，较原始提升有2%左右，文章设计性太强，结果还不错，算是针对于FPN做了一些探索。