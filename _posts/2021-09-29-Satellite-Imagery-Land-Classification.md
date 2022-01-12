---
title: Satellite Imagery Land Classification 
layout: post
post-image: "https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-KNN_SatelliteClassification_05.png?raw=true"
description: Classifying land types from satellite imagery using Machine Learning.    
tags:
- Data Science
- Machine Learning
- Remote Sensing
---


---

# **Problem**

Differentiating land types from imagery and storing it in a database can be a time consuming task. Although, a human can quickly recognize which areas are urban, farmland, forest, water, etc., converting that knowledge into a digital file will take considerable time. I realized this task could be accomplished much faster if I utilized some machine learning. 

# **Methodology**

To solve the problem at hand, I grabbed some data from an open source satellite imagery dataset: [https://www.sentinel-hub.com/explore/sentinelplayground/](https://www.sentinel-hub.com/explore/sentinelplayground/). If you've never played around with satellite imagery, the website provides lots of useful and interesting capabilities. Imagery is continuously updated, and the resolution is very good for a free resource. 

Selecting an area around Calgary proved interesting, as many different land types could be visible. I made sure to download all 12 bands of data. Remote sensing data is often imaged in EM bands in the visible spectrum (ie. red, green, blue), as well as outside the visible spectrum (into infrared and also slightly towards ultraviolet).

To use the data, I read it into Python and extracted pixel intensities across all 12 files. I performed some light filtering to smoothen the image by using a median filter on each 5 by 5 pixel area. This reduced the amount of noise visible in the dataset and would in the end improve my results. A CSV file containing coordinates and intensities for each EM band was saved.

Seven different land types were identified in a separate colour photo of the same area (urban, farmland, grassland, forest, water, snow, mountain/rock). Ten 20 by 20 pixel areas of each land type were identified. The pixel locations were stored in a manually generated file along with labels. This labeled data corresponded to approximately 0.73% of the total land that was covered in the satellite images. 

A dataset was created merging the full dataset of pixel intensities and of the labeled locations. The 20x20 pixel labeled locations were split into 5x5 pixel locations, in order to have more labeled samples in the dataset. Data was split into a validationa nd test dataset. 

Multiple classification methods were tested, in the end a k-nearest neighbour apporach proved most accurate with k=3.

The model was then used on the original data to predict land types across the entire satellite image. 

# **Results**

Results are displayed below. On the left a natural colour image is compared to the land use map generated using machine learning.

![Raw Satellite Image](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-Sentinel-2_L2A_True_color_2.png?raw=true)
![Classified Image](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-KNN_SatelliteClassification_05.png?raw=true)

![Legend](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-Legend_1.png?raw=true)

Lots of detail can be seen in the land use map, which might have been hidden at first glance in the original image, such as lakes, and small towns. The confusion matrix showed high levels of accuracy, confirming what we see by comparing the images. 

# **Takeaways**

* We managed to get a large area mapped and labeled by manually labeling less than 1% of the data and using machine learning to do the rest.
* These techniques can be applied to other instances, not just image classification but to almost any dataset. 
* Solution could be improved if we added more land class types. 



