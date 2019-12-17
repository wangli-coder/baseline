# Paper reading

#### EfficientDet: Scalable and Efficient Object Detection

基于Efficient net的目标检测系列模型，文中对目前常用的FPN方法做了讨论，并基于PANet的FPN进行了简化，加入了skip connection，并使用了类似SE的注意力机制方法(去除了softmax的指数运算，提高速度)，对不同的feature map进行权重融合，命名为BiFPN。在 Compound Scaling方面提出了适用于Efficient net系列的scaling公式，最终在COCO上达到 51 mAP，并且保证了FPS。