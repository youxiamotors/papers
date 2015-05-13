[README in English](README.en_US.md)  

#交通检测资料资料索引  
####导言
交通检测主要分为以下四项内容：

1. 车道线
2. 车辆、行人检测
3. 交通标识
4. 距离检测  

其中以车辆行人检测、车道线检测为较难，检测基于多帧，并使用许多感性的认识来做过滤。
CV的库：
opencv、libccv

<br />

##车辆、行人检测
车辆行人检测可分为四个步骤，（该方式参考论文：[Pedestrian Detection for Driving Assistance Systems: Single-frame Classification and System Level Performance](http://www.cs.huji.ac.il/~shashua/papers/iv04-ped.pdf))  
1. 在图像上，生成多个可重叠检测窗口，这些窗口的位置，可以是集中在车道线上，而不是在图像顶部（在图像中，顶部既是天空），用这个方法来避免全图扫描，并做到并发。  
2. 单帧检测，涉及DPM  
3. 多帧跟踪，连续多帧内，检测到的物体不会跑太远，有一定的运动规则，利用这点来避免重复的DPM，并过滤一定噪音（既上一帧存在，这一帧消失了，有可能是噪音）  
4. 用方框框出目标，并测出方框距离，速度等等。这个时候可以利用方框在路面上、人脚在方框底部这个感性认识来过滤噪音  

关于步骤2，有以下参考论文：  
30Hz Object Detection with DPM V5  

DPM: [Object Detection with Discriminatively Trained Part Based Models](http://cs.brown.edu/~pff/papers/lsvm-pami.pdf)   
[中文翻译](http://blog.csdn.net/masibuaa/article/details/17924671)  
libccv提供DPM

HOG: [Histograms of Oriented Gradients for Human Detection](http://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf)  
[中文翻译](http://blog.csdn.net/masibuaa/article/details/14056807)  

用图像分割来辅助后续的检测也是一个思路：
[Distinctive Image Features from Scale-Invariant Keypoints](https://www.cs.ubc.ca/~lowe/papers/ijcv04.pdf
)  
opencv上的有 金字塔、分水岭、均值漂移  
[均值漂移算法的研究与应用](http://202.118.31.195:8080/kzyjc/CN/article/downloadArticleFile.do?attachType=PDF&id=8540)  
[符合人类视觉感知的图像对象分割方法](http://www.ecice06.com/CN/article/downloadArticleFile.do?attachType=PDF&id=19886)





##车道线检测
这篇论文描述了基本的几个车道检测方法，从检测到跟踪  
[基于成像模型的车道线检测与跟踪方法](http://120.24.71.152/wp-content/themes/twentytwelve/pub_pdf/chedaojianche.pdf)

弯道拟合
[Lane detection and tracking using B-S](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.106.6644&rep=rep1&type=pdf)
