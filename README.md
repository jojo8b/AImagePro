# AImagePro
AI Imange Processing
目标：
本项目运用计算机的快速与大量处理数据的能力，将医学领域中图像识别与计算的工作更有效率的完成。特别是希望在耳鼻喉科相关的特征识别和图像计算有突破。具体的项目目标是在嗅沟的识别和嗅球体积的计算，和嗅沟深度的计算。

原理：
头部扫描影像以DICOM 作为输入格式，训练数据集先以人工方式标示特征，从而在特征下方识别目标特征。扫描影像以渐层的方式，将头部剖面的影像储存于目录中。
本系统将目标特征在剖面影像形成的面积集成预测的空间图，进行体积的计算。

核心技术：
运用人工智能中对影像处理的特征辨识的深度神经网络框架，搭配图像识别的演算法与GPU计算等方式，达到高效、快速、准确的辨识功能。

具体的技术列表：
Keras: 深度学习的框架搭建， 建立与使用训练模型的整体框架。
Tensorflow：深度学习中神经网络的组成元件
Faster R-CNN：实现目标检测的步骤：候选区域生成，特征提取，分类，位置精修。
Sklearn: 机器学习的演算法集成
Opencv: 影像处理分析计算，对检测到的目标进行图像分割和
PyDicom：读取医学影像档（DICOM）

流程：

特征训练：
1）以PyDicom读取DICOM 档案，转换格式成为JPEG等特征标记软件可读取的格式
2）医学人员使用系统中特征标记程序labelImg.py，对目标以方框标示，程序记录标示框的位置，影像的灰度、形状等特征于xml记录档,
3）将所有训练的图像JPEG档与特征记录的xml档放置于特征训练集的相对目录
4）运行训练程式读取影像与特征档，产生并保存以这个特征训练集的模型

特征辨识：
1）用户将需辨识的DICOM目录导入储存在辨识程式的文件系统中
2）程序读取已训练完成的特征训练集的模型，以模型设定系统的参数配置
3）程式读取DICOM并转换格式
4）循序把影像档输入到模型中进行辨识
5）符合特征的图像，将辨识的区域与范围以方框标示；未符合特征的图档没有方框
6）对该DICOM目录所有符合特征辨识的图档进行整合处理并计算预测的特征的体积
