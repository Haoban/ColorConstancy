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

[FFCC - Fast Fourier Color Constancy, (2017 CVPR)](https://arxiv.org/pdf/1611.07596v3.pdf)

[FC4 - FC4: Fully convolutional color constancy with confidence-weighted pooling, (2017 CVPR)](https://openaccess.thecvf.com/content_cvpr_2017/papers/Hu_FC4_Fully_Convolutional_CVPR_2017_paper.pdf)

### Based on the detailed knowledge of the camera module properties




## Latest Color Constancy Topics


## Performance Evaluation Index - How to measure?

1. `E00` from CIE
2. Angular Error (common used before)
3. RAE (Reproduiction Angular Error) Paper: [The Reproduction Angular Error for Evaluating the Performance of Illuminant Estimation Algorithms](https://ieeexplore.ieee.org/abstract/document/7494650)
4. Relative Error


