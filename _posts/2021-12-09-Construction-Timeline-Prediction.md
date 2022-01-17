---
title: Construction Timeline Prediction 
layout: post
post-image: "https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project03-Construction.jpg?raw=true"
description: Developing a web based application to predict construction timelines from text using NLP.    
tags:
- Machine Learning
- NLP
- API 
---


---

# **Problem**

Predicting construction timelines is a difficult task, which heavily relies on user experience and estimates. The timelines are required to be accurate, so that construction material, personnel planning, and other tasks can be coordinated and costs reduced. Automating the prediction task, so that even junior project manager could accurately predict timelines, would be inherently useful in future project planning. Additionally, adding a user interface to the prediction and posting it on a website, would allow the application to be accessed by anyone anywhere, adding to its usefulness. 



# **Methodology**

Working with our client and stakeholders, we defined the scope of the project. It would include developing an application to predict construction timelines. The application would need to be easily accessible anywhere, and simple to use. 

Completing a preliminary search of comparable software that already exists in the world. The search yielded many project planning services which allowed users to input custom completion times and organize projects, but none actually predicted the time for a task. 

The client provided the data to use in building a machine learning model. It consisted of historical projects, with each project broken down to include: type of transformation, description, quantities, and units.

A new feature was calculated and generated to better enable the use of text in the macahine learning model, which was days/unit (and units/day). Other steps in building the machine learning model included data wrangling, data pre-processing, splitting the dataset, evaluation and optimization. 

The model was integrated into a web based app. The website was built to allow anyone to access it from anywhere an internet connection could be made. Flask and flask-cor are micro web frameworks that allowed communication with webpages and the python machine learning model. Postman was used for testing of the solution before deployment. 

Additional features that were added to the solution included: 
* Predicting unit type
* Error handling
* Allowing for Multiple Consecutive Tasks
* Spell Check
* Search for String Matches


# **Results**

The machine learning model was able to predict the completion rate of a construction activity. The model used NLP to analyze any words in the tranformation and/or description inputs to calculate a predicted timeline for a completing a unit of work and multiplied it by the quantity of units input by the user. The type of unit was seperately predicted from the input text. Additionally, a start date and an end date could be selected to determine if sufficient time was allocated to the project.

A sample of interacting with the site is shown below.

![Sample of Website](https://github.com/danylokolos/danylokolos.github.io/blob/main/assets/images/Project03-Predict.gif?raw=true)



# **Takeaways**

* Text was corrected, analyzed, and utilized for predictions using NLP inside a machine learning model. 
* Learned how to develop API's to interact between programs and web pages. Getting everything to work the first time is a bit tricky, but once this is accmplished, it is much faster next time. 
* Handling every type of conceivable error in user inputs can be a daunting task, as many types of user inputs need to be checked for. Significant amounts of time were spent to make the website user friendly and describe errors to users.


