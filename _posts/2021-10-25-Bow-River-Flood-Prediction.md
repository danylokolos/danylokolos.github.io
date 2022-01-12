---
title: Bow River Flood Prediction 
layout: post
post-image: "https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project02-CalgaryFlood.JPG?raw=true"
description: Predicting a flood on the Bow River using machine learning and multiple open source datasets.    
tags:
- Data Science
- Machine Learning
- Data Cleaning
---


---

# **Problem**

In 2013, the Bow River flooded causing extensive damage in the city of Calgary. The total cost of the flood has been assessed at approximately $5 billion. Much of the damage was to infrastructure and personal property. Forecasting a flood of this magnitude is a problem that needs to be solved. An accurate flood forecast could have allowed for mitigation procedures to have been initiated, and the extensive damage may have been partially reduced. 


# **Methodology**

To solve the problem, I researched wha comes causes flooding and which variables are important. Weather, temperature, rainfall, snowpack, soil saturation, and upstream water levels are all important factors that need to be studied. 

After researching available data, two open source data sets were found. They didn't contain all the variables that were identified, but the most important factors would were included. Both datasets came from government websites. 

Water flow rates: [https://wateroffice.ec.gc.ca/mainmenu/historical_data_index_e.html](https://wateroffice.ec.gc.ca/mainmenu/historical_data_index_e.html) From here, 17 water flow gauges in Calgary and upstream along the Bow River were extracted.

Weather data: [https://climate.weather.gc.ca/historical_data/search_historic_data_e.html](https://climate.weather.gc.ca/historical_data/search_historic_data_e.html) From this, data from 2 weather stations, in Banff and Kananaskis, that could be important to predicting water flow rates, were retrieved. Items of interest included air temperature, and precipitation.

Data was reformatted and combined. Seperate .csv files of individual stations were scraped for data within a ten year time span and transformed into a single tabular dataset. Into this dataset, weather data was inserted matching to the appropriate dates. Several data wrangling steps were applied, to correct for missing data (station not recording), faulty data (impossible values) and unreliable data (frozen sensors). 

After pre-processing, splitting, builing machine learning models, and evaluating those models, prediction results were obtained. 


# **Results**

The results of our best model predicted the flood of the Bow River in 2013. The actual daily flow rate on June 21, 2013 was 1750 m3/s. One day before the maximum flood, our model predicted 1672 m3/s and two days before the flood, 1638 m3/s. This corresponds to errors of 4.5% and 6.4%, respectively. 

The features which were most importance in the model corresponded to flow rates in the Bow River just below the Ghost Reservoir (feature importance 38%), and less so in the Kananaskis River (feature importance 11%) and Bow River near Cochrane (feature importance 11%). The second largest feature of importance was the precipitation amount in Kananaskis (feature importance 22%). All other features had less than 2% relevance each.

As a bonus, our model also predicted flow rates for non-flood events. These could be used in for other purposes relating to water management. Mean absolute error predicting one day in advance was 7.6 m3/s and two days in advance 10.8 m3/s. From the figures below, one can see the errors increased as the flow rates in the river were higher. Predicting 2 days in advance had more scatter in the predictions, resulting in less accuracy. 

![Prediction Lag 1 Day](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project02-PredictionLag1Day.png?raw=true)
![Prediction Lag 2 Day](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project02-PredictionLag2Day.png?raw=true)




Results are displayed below. On the left a natural colour image is compared to the land use map generated using machine learning.

![Raw Satellite Image](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-Sentinel-2_L2A_True_color_2.png?raw=true)
![Classified Image](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-KNN_SatelliteClassification_05.png?raw=true)

![Legend](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project01-Legend_1.png?raw=true)

Lots of detail can be seen in the land use map, which might have been hidden at first glance in the original image, such as lakes, and small towns. The confusion matrix showed high levels of accuracy, confirming what we see by comparing the images. 

# **Takeaways**

* We managed to get a large area mapped and labeled by manually labeling less than 1% of the data and using machine learning to do the rest.
* These techniques can be applied to other instances, not just image classification but to almost any dataset. 
* Solution could be improved if we added more land class types. 



