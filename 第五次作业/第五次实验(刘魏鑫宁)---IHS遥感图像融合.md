第五次实验---IHS遥感图像融合

学生：刘魏鑫宁

---

实验目的：

(1) 将多光谱影像重采样到与全色影像具有相同的分辨率；

(2) 将多光谱图像的Ｒ、Ｇ、Ｂ三个波段转换到IHS空间，得到Ｉ、Ｈ、Ｓ三个分量；

(3) 以Ｉ分量为参考，对全色影像进行直方图匹配 

(4) 用全色影像替代Ｉ分量，然后同Ｈ、Ｓ分量一起逆变换到RGB空间，从而得到融合图像。

---

实验结果：

![](http://ww1.sinaimg.cn/large/006y6mwBly1fxlla99rclj30oe0oa1ky.jpg)

---

实验心得：

​	一开始以为实验会很难~

​	然后分析了老师发的MATLAB程序，发现其实主要就是先乘一个矩阵tran1,得到三行分量，即I,H,S. 然后把I分量给换成全色通道，再乘回tran2变成RGB图像即可~

​	但是一开始有地方没有想明白，认为全色图像也是有三色通道的，看到MATLAB程序直接替换了I分量感到很疑惑，所幸没有在上面耽误太多的时间，去即时查了百度，发现全色图像就只有一个通道~

​	然后又是一个坑，看到reshape函数，发现它读取矩阵的方式是按列处理的，于是一开始也这么读取数据。。。有点无语，后面觉得不对，这么读数据太诡异了，就仔细思考了一下，写成：

![](http://ww1.sinaimg.cn/large/006y6mwBly1fxll4aj7wjj30zd0c4754.jpg)

其实它的意思就是对应位置的RGB或者IHS加权求和。

觉得写得很对，但是运行结果又报错，这次是因为图片太大所以损坏?

但是处理时的确是要用float,怀疑图像其实还是要用Byte,只是处理的时候是以float格式运算的，在修改完：

![](http://ww1.sinaimg.cn/large/006y6mwBly1fxll88k5obj30pw03taa3.jpg)

就好了，有趣！



