# ColorConstancy

## Background

This is a **paper list** about Color Constancy (new topic for me). Until now, I haven't found any no newcomer-friendly tutorials. So it appeared.

All papers will only have links, which redirects to the initial page, and will not provide downloads on this site to avoid license issues. AWB is often used as a synonym for computational color constancy in digital photography.


The core of AWB is `estimate of the illumination chromaticity`

**If you dont know what is AWB/Color Constancy, or you are not familiar with followings, find them out there**
- [Some AWB terminologies (e.g. `chromatic adaptation`, `white point`, `Von Kries`)]()
- [Different color space]()
- [Image Signal Processing]()
- [Illuminations from CIE]()


## Useful links

- [Color Constancy in PaperwithCode](https://paperswithcode.com/task/color-constancy)
- [Color Constancy Research Website](https://colorconstancy.com/)
- [Color Constancy Topics in Github](https://github.com/topics/color-constancy)


## Some classic papers



## Some survey

[Computational Color Constancy: Survey and Experiments (2011, TIP)](https://staff.fnwi.uva.nl/th.gevers/pub/GeversTIP11.pdf)


Two main categaries if need detailed knowledge of the camera module properties.

Color by Correlation (CbC) methods
Gamut Mapping (GM) methods

Characterization of Illumination Chromaticity (CCIC)


### Only based on the images

#### Statistical Approaches

Gray world hypothesis: based on the achromatic hypothesis, e.g. the average color of the world is gray, which is good for colorful equally images .Paper: [A spatial processor model for object colour perception]()

(Perfect Reflectance) MAX-RGB/white patch: which is good for the situation that the brightest component values (max value in each channel) in the image belong to an achromatic object or a specular reflection
Paper: [The retinex theory of color vision]() 

SHADES-OF-GRAY: A weighted combination between Gray World and Max-RGB
Paper: [Shades of gray and colour constancy]()

GRAY EDGE HYPOTHESIS: the average of the reflectance differences in a scene is achromatic. Good for full resolution image, and doesn't perform well when downscaled. 
Paper: [Edge-based color constancy]()

#### Gamut-Based Approaches 

Gamut-mapping

Gamut-mapping 有时候会被列入 learning-besed 类算法，有事可以单独归为一类，也是我认为是一种非常简单有效的一类算法，Gamut-mapping 的假设是：在真实的世界中，某种光源下，能看到的颜色是有限的。这个理解起来比较困难，举个例子，Gamut-mapping 可以简单理解为不同的光源下，各种颜色的概率是不一样的；例如在烛光下看到天蓝色的概率是比较小的，而看到黄色的概率是大的。

Gamut mapping 的标准流程如下，但是这个算法有几类缺陷：
（1）learning 到的 gamut 不一样的标准的
（2）Gamut 是三维的话，计算量还是很大的
（3）不能求出一个准确解，只是一个最优解，这在学术上会导致其指标略差，不过对于业界来说足够了。



#### Physics-based Approaches


#### Learning-based Approaches 

人脑是怎么做白平衡的？

人的大脑在实现所谓色彩恒常性（AWB）的时候，是先通过形状，纹理先把物体识别出来，然后根据经验实现色彩恒常性。人眼看见一张白纸，大脑会先分析形状和纹，知道这是张纸，然后根据经验，知道这‘应该’是白色，最后再把它校正为白纸。 Machine learning 就是仿照人类大脑的工作方式。

利用 isp 提供的已有的统计信息作为特征。现在很多的 isp 都会把图像分成 n x m 个区域，然然后计算 B/G,R/G,以及 average R，G，B。用于白平衡算法。也会计算区域内的 sharpness，用于自动对焦算法。合理的利用好这些统计信息，产生出特征值，就足以用来训练 machine learning 算法了。


[Convolutional color constancy, (2015 CVPR)](https://arxiv.org/pdf/1507.00410.pdf)
    
    > 新概念与难点：**二维色度直方图** channels=[u, v], bin=[256, 256], bin-width=0.025

    ref: [OpenCV:2D直方图](https://opencv-python-tutorials.readthedocs.io/zh/latest/4.%20OpenCV%E4%B8%AD%E7%9A%84%E5%9B%BE%E5%83%8F%E5%A4%84%E7%90%86/4.10.3.%20%E7%9B%B4%E6%96%B9%E5%9B%BE3%EF%BC%9A2D%E7%9B%B4%E6%96%B9%E5%9B%BE/)

    对于不同tinted图像来说，chrominance histogram总是形状相同的，只有平移变换。This is a consequence of our definitions of u and v: scaling a pixel’s RGB value is equivalent to translating a pixel’s log-chrominance, as was noted in [20]. This equivalence between image-tinting and histogram-shifting enables the rest of our algorithm.

    对线性RGB图像应用每通道增益相当于诱导该图像的对数色度直方图的2D平移，这允许将颜色恒定性降低到在对数色度直方图空间中定位的任务。


[FFCC - Fast Fourier Color Constancy, (2017 CVPR)](https://arxiv.org/pdf/1611.07596v3.pdf)

    而FFCC不是在大对数色度平面上执行定位操作，而是在小对数色度环面上执行定位操作。
    
    通过以下形象的例子来降低计算量，但是会出现一些问题：1） 像素值被重叠的形状破坏，这使得检测变得困难，2）检测必须“环绕”这个环形图像的边缘，3）而不是绝对的、全局的位置，我们只能恢复一个混叠的、不完整的位置。FFCC的工作原理是将CCC的大卷积问题（即A上的人脸检测）和该问题的混叠缩小到一个可以有效解决的小尺寸（即B上的人脸检测）。实验表明，我们可以学习一个有效的颜色恒常性模型面对困难和模糊性，该卷积分类器将使用FFTs实现和学习，因为FFT卷积的自然周期性解决了检测“环绕”环形图像边缘的问题，并产生显著的加速比。


[FC4 - FC4: Fully convolutional color constancy with confidence-weighted pooling, (2017 CVPR)](https://openaccess.thecvf.com/content_cvpr_2017/papers/Hu_FC4_Fully_Convolutional_CVPR_2017_paper.pdf)

大量计算色彩恒常性算法(Qian et al. 2019;陈等人2019年;Cheng et al. 2015;Bianco、Cusano和Schettini 2017;Shi, Loy, and Tang 2016;Hu, Wang, and Lin 2017)依赖于`准确和稳健的照明预测`，然后使用简单而有效的`von Kries模型`(von Kries 1902)进行图像校正。

很少有算法（Qian等人2019）专注于具有挑战性的与摄像机无关的照明估计，从而实现了强大的性能。


### Based on the detailed knowledge of the camera module properties




## Latest Color Constancy Topics


## Performance Evaluation Index - How to measure?

1. `E00` from CIE
2. Angular Error (common used before)
3. RAE (Reproduiction Angular Error) Paper: [The Reproduction Angular Error for Evaluating the Performance of Illuminant Estimation Algorithms](https://ieeexplore.ieee.org/abstract/document/7494650)
4. Relative Error


