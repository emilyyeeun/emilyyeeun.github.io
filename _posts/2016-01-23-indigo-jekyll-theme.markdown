---
title: "Non-invasive Lactate Sensor"
layout: post
date: 2021-08-17
tag: Java | Python
# image: assets/images/workout.jpeg
projects: true
hidden: true # don't count this post in blog pagination
description: "ESE451 Senior Design Project"
category: project
author: emilyyeeun
externalLink: false
---
![screen-shot](/assets/screen-shot.png)
# About the Project
This project was for ESE 451, Electric & Systems Engineering Senior Design.
We designed an Android App that predicts blood lactate threshold using Machine Learning Model.

<strong> Tech Stack: </strong> Java for Android App Dev and Python for model training and backend (Flask)

# Why Lactate Testing?
Lactate is produced in excess by cells when the
body doesn’t have enough oxygen or the body’s
metabolic process is disrupted.

Lactate levels can be monitored to track metabolism rates. <br>
  ● can be used to find an individual’s ideal exercise level <br>
  ● can be used medically to detect conditions such as sepsis, heart failure, etc.

<div style="text-align:center"> <img src="/assets/lactate.png"></div>

As the test is done now, the process can be long and tedious while requiring lab technicians to draw blood every five minutes; however, individual lactate data is extremely valuable when developing training plans for athletes.

<div style="text-align:center"> <a href="https://docs.google.com/file/d/1Pq7lZ40r7c-5xTtFuQ2Ob8M3BxdrHRMe/preview" title="Invasive Lactate Testing"><img src="https://www.researchgate.net/profile/Julien-Louis-2/publication/317597927/figure/fig2/AS:667914503987213@1536254635905/Lactate-Pro-V2-LT-1730-in-use-by-the-authors_Q320.jpg" alt="Alternate Text" /></a></div>


# Stakeholders
<div style="text-align:center"> <img src="/assets/stakeholders.png"> </div>

<div style="text-align:left; padding-bottom:20px"> <img src="/assets/coach1.png" align="left">
“I would love to test my [UPenn Rowers], but that test sucks. You got
to take blood every 5 minutes or so. No one likes getting poked in the
ear. It would be great if you could make a better one”</div>

<br>
<div> </div>
<div style="text-align:left; padding-bottom: 40px"> <img src="/assets/coach2.png" align="left">
“Lactate testing has never been feasible for [UW Rowing] since the
process is so difficult to perform on a large group of guys, but it’s a
shame since the data is super valuable” </div>
<br>


# Design & Implementation
<div style="text-align:center"> <img src="/assets/design.png"></div>
The app requires the user to input his/her workout goal and bio inputs including glucose level, oxygen level, and heart rate.
The app then uses Machine Learning Ensemble Learning to predict the appropriate lactate threshold and returns workout recommendations.
<br>
<div style="text-align:center"><img src="/assets/implementation.png">  </div>
There are three fitness goals that the user can input: Cardio, Strength Endurance, and Strength Explosiveness.
<br>
<div style="text-align:center"><img src="/assets/machineLearning.png">  </div>
To create our data model, we got access to the MIMIC-III Clinical Database, which is a
relational and openly available database consisting of 26 tables which include demographics, vital signs, laboratory tests, medications, and more information for 40,000 patients during their stay in the ICU. It was developed by the MIT Lab for Computational Physiology. We were able to extract patients' age, gender, height, weight, glucose level, oxygen saturation, heart rate, and lactate level by merging tables on patients’ subject ID and their measurements’ item ID. We realized that there was a negative correlation between certain glucose and lactate quintiles, so we grouped glucose in mg/dL into 6 ranges: less than or equal to 72, between 72 and 97.2, between 97.2 and 120.6, between 120.6 and 136.8, between 136.8 and 147.6, and greater than 147.6. When users put in their data and the app shows them their lactate threshold, as seen in Appendix VI, it is what range the model is predicting. The different ranges in mmol/L are: less than or equal to 0.8 (Model’s Level 1), between 0.8 and 1.5 (Model’s Level 2), 1.5 and 2.4 (Model’s Level 3), 2.4 and 4.0 (Model’s Level 4), 4.0 and 6.0 (Model’s Level 5), and greater than 6.0 (Model’s Level 6).

After splitting up the data into training and testing sets (80% training and 20% testing) and running the logistic regression model, we got a testing mean squared error (MSE) of 0.1009, a root MSE of 0.3176, an R squared, which is the proportion of the variance in the dependent variable that is predictable from the independent variable, of 0.8612, and a percentage misclassified of 10.09%. To also check for the bias-variance tradeoff, we calculated the training MSE, which is 0.0938 and close to the testing MSE.
<br>
<div style="text-align:center"><img src="/assets/workout.png">  </div>



---

[Check it out](https://github.com/emilyyeeun/LactateSensor) here.
