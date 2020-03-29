# West Nile Virus Prediction - Kaggle Challenge

## Background

West Nile virus is most commonly spread to humans through infected mosquitos. Around 20% of people who become infected with the virus develop symptoms ranging from a persistent fever, to serious neurological illnesses that can result in death.

In 2002, the first human cases of West Nile virus were reported in Chicago. By 2004 the City of Chicago and the Chicago Department of Public Health (CDPH) had established a comprehensive surveillance and control program that is still in effect today.

## Problem Statement

To predict when and where different species of mosquitos will test positive for West Nile virus using a strong classifier model with AUC score using information related to weather, location, and spray efforts in the past, to help the City of Chicago and CPHD more efficiently and effectively allocate resources towards preventing transmission.

Datasets provided : Train, Test, Weather and Spray<br>
[https://www.kaggle.com/c/predict-west-nile-virus/](https://www.kaggle.com/c/predict-west-nile-virus/).

---


## Project team organization and planning

The project is executed as a group and Github repository was used to share notebooks among team members.<br>
Project planning was implemented through google sheet by defining deliverables, timelines, team member responsible and progress tracking.<br>

---

## Data Cleaning & EDA

**Data Cleaning**

    1) Appropriate data types assigned to features e.g date
    2) Dropped redundant features such e.g. location related features & duplicate rows
    3) Dropped features with huge instances of missing values
    4) Imputed values to features indicated with M (Missing) & T(Trace)
    5) Aligned training set with testing set for training and modeling later on

**EDA**

    1) Data availability:
        a. Train data: 2007, 2009, 2011 and 2013
        b. Test data: 2008, 2010, 2012 and 2014
        c. Spray data: 2011 and 2013
        d. Weather data: 2007 - 2014

    2) Significant increase in number of spray locations in 2013 vs. 2011

    3) Looking at traps with WNV presence vs. sprays, clusters can be identified where sprayed. For some reason, central area did not have any spray locations

    4) Out of total 7 species of mosquitoes only 3 species are seen to be carriers of WNV virus

    5) 2009 and 2011 are the years where overall WNV count was lower. Need to dig deeper into the reason why. Probably weather conditions were not favorable for the mosquitoes in these years.

    6) Only 8 out of 134 traps have > 10 WNV positive

    7) After identifying top traps and trying to plot sprays over these traps explained the spraying locations much better.

---

## Modeling, Evaluation and conclusions

**Modeling**

Tried 5 different models. For easier comparison the basic Logistic Regression model was considered as the baseline model.<br>
The models tried and their respective Kaggle score follows:

Model     | Kaggle Score
-----     | ------------
Logistic Regression | **0.50**
Gradient Boost Classifier| **0.56**
Gradient Boost Classifier with Grid Search | **0.49**
Random Forest Classifier| **0.52**
XGBoost Classifier| **0.53**
Decision Trees| **0.52**

**Model Evaluation**

Baseline score : Logistic Regression

Score on train set   | Score on test set
-----     | ------------
**0.74** | **0.78**

Score of chosen model : Gradient Boost Classifier

Score on train set   | Score on test set
-----     | ------------
**0.90** | **0.87**

**Insights and conclusions**

    1)  Least variance between test and training scores >> not overfit

    2)  Feature importance suggests the prevalence of WN virus in certain locations, with specified species

    3)  Time of the year with longer days influences virus presence

    4)  Features highlighted to be used to determine where and when to focus on spraying efforts

**Limitations and Recommendations**

    Limitation: Model scored significantly lower on out of sample Kaggle set.

**Recommendations:**

    1)  Elaborate feature engineering with time series functions on weather dataset

    2)  Include dummy variable for top traps

    3)  NumMosquito feature even with its high correlation to virus presence had to ignored >> predict this feature first before predicting presence of virus

    4)  Availability of spray information for more years would help the model score better


---
## Cost Benefit Analysis, Conclusions & Recommendations

**Human Benefits of spraying outweighs the Costs!<br>**
The table below explains further:

 Cost and Benefit | Spray | Not Spray
-----      |-----     | ------------
Misc. Costs |Labour work : Approx. $0.75 per acre of spray | Medical cost<br> $33,143 per inpatient<br>$6,317 per outpatient<br> $18,097 per patient spent time in a nursing home<br> Productivity loss<br>$58,935 per personal income
Vector Control Cost | ~ $144K per person |
Benefits |   Human life saved<br> - Improved quality of life<br> - Workplace productivity<br> - Economic benefits from tourism  |Human life loss <br> - Long term / wider mental health issues<br> - Lower workplace productivity <br> - Negative economic impact

**Recommendations**

    1)  Consider strategically spraying at locations with highest infections.

    2)  Conduct spraying during hotter months i.e. August and September

    3)  Educate and promote the public to:
        a)  Use insect repellent
        b)  Wear long-sleeved shirts and pants
        c)  Take steps to control mosquitoes indoors and outdoors
            i.e. Remove standing water where mosquitoes could lay eggs
