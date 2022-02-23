零基础入门CV赛事-Task2数据读取与数据扩增

在上一张当中给大家介绍了赛题的内容，和三种不同的解决方案，从本章开始，我们将逐渐学习使用定长字符识别，思路来构建模型，逐步讲解赛题的解决方案和相应知识点，

## 数据读取与数据扩增

本章主要内容为数据读取与数据扩增，和Python读取赛题数据三个部分组成

### 2.1学习目标

学习Python和PyTorch中图像读取

学习扩增方法和PyTroch读取赛题数据

### 2.2图像读取

由于赛题数据是图像数据任务的识别图像中的字符，因此我们首要进行对数据的读取 操作，在Python中由很多库可以完成数据读取的操作，比较常见的由Pillow和OpenCV

### 2.2.1Pillow

Pillow是Python图像处理函数库PIL的一个分支，Pillow提供了常见的图像读取和处理的操作 ，而且可以与Pythonnotebook无缝集成，是应用比较广泛的恶库



```
from PIL import Image
#导入Pillow库
#读取图片
im = Image.open('./cat.png')
from PIL import Image,ImageFilter
im = Image.open('./cat.png')
#应用模糊滤镜
im2 = im.filter(Inagefilter.BLUR)
im2.save('blur.jpg','jpeg')
from PIL import image
#打开一个jpg图像文件，注意是当前路径
im = Image.ipen('/cat.jpg')
im.thumbnail((w//2,h//2))
im.save('thumbnail.jpg','jpeg')


```

当然上面只演示了Pillow最基础的操作，Pillow还有很多的图像操作，是图像操作的必备课

Pillow的官方文档

### 2.2.2OpenCV

OpenCV是一个跨平台的计算机视觉库，

## 2.3数据扩增方法

在上一个小节当中给大家初步介绍了Pillow和OpenCV的使用，现在回到塞梯街道字符识别任务中，在赛题中我们需要对的图像进行字符识别，因此需要我们完成的数据的读取操作，同时也需要完成数据扩增Data Augmentation操作

### 2.3.1数据扩增介绍

在深度学习数据扩增方法非常重要，数据扩增可以增加训练集的样本，同时也可以有效理解模型过你和的情况，也可以给模型带来的更强的泛化能力，，



数据扩增有什么作用？

在深度学习模型的训练过程当中，数据扩增是必不可少的环节，现有深度学习的参数非常多，一般的模型可训练的数量基本上都是万到百万的级别，而训练集的样本的数量很难有这么多。

其次数据扩增可以扩展样品空间，假设现在的分类模型需要对汽车进行分类，左边的是汽车A，右边的为汽车B，如果不使用任何的数据扩增方法深度学习模型会从汽车车头的角度来进行判别，而不是在汽车具体的区别，。

有哪些数据扩增方法，

在常见的数据扩增方法中，一般会从图像的颜色、尺寸、形态、空间、和像素等角度进行变换。当然不同的数据阔怎方法可以自由进行组合，得到更加丰富的数据扩增方法。

以torchvision为例，常见的数据扩增方法包括：

1.transforms.CenterCrop对图片中心进行裁剪

2.transforms.Colorjitter对图像颜色的对比度，饱和度和零度进行变换

3.transforms.FiveCrop对图像四个角和中心进行裁剪得到五分图像

4.transforms.Grayscale对图像进行灰度变换。

5.transforms.Pad使用固定值进行像素填充

6.transforms.RandomAffine随机仿射变换

7.transforms.RandomCrop随机区域裁剪

8.transform.RandomhorizonalFliop随机水平翻转。

9.transform.RandomRotation随机旋转

10.transforms.RandomVerticalFlip随机垂直翻转。

在本次赛题中，赛题任务是需要对图像中的字符进行识别，因此对于字符图片并不能进行翻转操作。比如字符6经过水平翻转就变成了字符9，会改变字符原本的含义

torchvision

pytorch官方提供的数据扩增库，提供了基本的数据数据扩增方法，可以无缝与torch进行集成；但数据扩增方法种类较少，且速度中等

imgaugimgaug是常用的第三方数据扩展库，提供了多样的数据扩增方法，且组合起来非常方便，且组合起来非常方便，速度较快。。。

albummentations

是常用的第三方数据库，提供了多样的数据扩增方法，对图像分类，语义分割，物体检测，和关键点检测都支持，速度较快。。。



## 2.4Pytorch读取数据

由于本次赛题我们使用Python框架讲解具体的解决方案，接下来将是解决塞梯的第一部分Python读取赛题数据。、

在Python中数据是通过Dataset进行封装，并通过Dataloader进行并行读取，所以我们只需要重载一下数据读取的逻辑就可以完成数据的读取。。假设训练集存储位置为’./train/'训练集标签文件存储位置为‘./train'示例代码如下。。

```
import os,sys,glob，shutil,json
import cv2

from PIL import Image
import numpy as np

import torch
from torch.utils.data.dataset import Dataset
import torchcision.transforms as trainforms

class SVHN Dataset(Dataset):
	def_init_(self,img_path,img_label,transform=None)
		self.img_path = img_path
		self.img_label = img_label
		if transform is not None:
			self.transform = transform
		else
			self.transform = None
	def _getitem_(self,index):
		img = Image.open(self.img_path[index]),convert('RGB')
		
		if self.transform is not None:
		img = self.transform(img)
		
		#原始SVHN中列别为10为数字0
		lbl = np.array(self.img_label[index],dtype=np.int)
		leb = list(lbl )

```







torch vision和imgaug还有albumentations是常用的第三方数据扩增库，提供了多样的数据扩增

![image-20220222115312235](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222115312235.png)