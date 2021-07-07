# ColorConstancy

## Background

This is a paper list about Color Constancy (new topic for me). Until now, I haven't found any no newcomer-friendly tutorials. So it appeared.

All papers will only have links, which redirects to the initial page, and will not provide downloads on this site to avoid license issues. AWB is often used as a synonym for computational color constancy in digital photography.


The core of AWB is `estimate of the illumination chromaticity`


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

Characterization of Illumination Chromaticity (CCIC)


### Only based on the images

#### Statistical Approaches

Gray world hypothesis: based on the achromatic hypothesis, which is good for colorful equally images .Paper: [A spatial processor model for object colour perception]()

MAX-RGB: which is good for the situation that the brightest component values in the image belong to an achromatic object or a specular reflection
Paper: [The retinex theory of color vision]() 

SHADES-OF-GRAY: A weighted combination between Gray World and Max-RGB
Paper: [Shades of gray and colour constancy]()

GRAY EDGE HYPOTHESIS: the average of the reflectance differences in a scene is achromatic. Good for full resolution image, and doesn't perform well when downscaled. 
Paper: [Edge-based color constancy]()

#### Gamut-Based Approaches 


#### Physics-based Approaches


#### Learning-based Approaches 

[Convolutional color constancy]()

[FFCC, (2017 CVPR)](https://arxiv.org/pdf/1611.07596v3.pdf)


### Based on the detailed knowledge of the camera module properties




## Latest Color Constancy Topics


## Performance Evaluation Index - How to measure?




