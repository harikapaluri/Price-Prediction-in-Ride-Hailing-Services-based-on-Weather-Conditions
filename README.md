# Team Name: Data Scouts
### Team Members:
 
|Name     | 
|---------|
|[Sai Harika Paluri](https://github.com/harikapaluri)| 
|[Nikhil Kumar Mutyala](https://github.com/NikhilKumarMutyala) |    
|[Sree Divya Keerthi Paravasthu Siddanthi](https://github.com/SreeDivyaKeerthiPS) |    
|[Ravi Theja Goalla](https://github.com/wgaca007) |    
 
 
#  Project Title: Price prediction in ride-hailing services based on weather conditions

## Project Description:
Uber and Lyft's ride prices are not constant like public transport. They are greatly affected by the demand and supply of rides at a given time. So what exactly drives this demand? The first guess would be the time of the day; times around 9 am and 5 pm should see the highest surges on account of people commuting to work/home. Another guess would be the weather; rain/snow should cause more people to take rides.

The data is approx. for a week of Nov '18 ( I actually have included data collected while I was testing the 'querying' application so might have data spread out over more than a week. I didn't consider this as a time-series problem so did not worry about regular interval. The chosen interval was to query as much as data possible without unnecessary redundancy. So data can go from end week of Nov to few in Dec)
The Cab ride data covers various types of cabs for Uber & Lyft and their price for the given location. You can also find if there was any surge in the price during that time. Weather data contains weather attributes like temperature, rain, cloud, etc for all the locations taken into consideration.


## Data:
The dataset contains 10 features along with the price for 693071 observations. Later we add few more derived features to this dataset.<br>
The description for the 10 features is given below:<br>

### cab_rides.csv
<img src="https://github.com/NikhilKumarMutyala/Prediction-of-Uber-Lyft-Ride-Prices-depending-on-the-Weather-Conditions/blob/master/DATA.PNG" width="450">

### weather.csv
<img src="https://github.com/NikhilKumarMutyala/Prediction-of-Uber-Lyft-Ride-Prices-depending-on-the-Weather-Conditions/blob/master/data2.PNG" width="450">

The date is in timestamp format. So we change that timestamp into date format, the date attribute is added to the dataset and timestamp attribute is removed. Few attributes are added like hour, fare_per_mile.


## Installation:
* Anaconda 4.5.12 Distribution
* Python 3.7
* Jupyter Notebook


## CRISP-DM Process:
Cross-industry standard process for data mining, known as CRISP-DM, is an open standard process model that describes common approaches used by data mining experts. It is the most widely-used analytics model.

![alt text](https://github.com/NikhilKumarMutyala/Prediction-of-Uber-Lyft-Ride-Prices-depending-on-the-Weather-Conditions/blob/master/crisp%20dm.PNG)
*image credits: [Youtube](https://www.youtube.com/watch?v=CRKn-9gVNBw)*

This model is an idealised sequence of events. In practice many of the tasks can be performed in a different order and it will often be necessary to backtrack to previous tasks and repeat certain actions. The model does not try to capture all possible routes through the data mining process.
CRISP-DM breaks the process of data mining into six major phases:

* Business Understanding
* Data Understanding
* Data Preparation
* Modeling
* Evaluation
* Deployment

 ### Business Understanding
The first thing we must do in any project is to find out exactly what we are trying to accomplish. We must state objectives and requirements. We should translate these goals and restrictions into the formulation of a data mining problem definition. We must start with a clear understanding of
* A problem that you want to address/ Objectives
* The business goals
* Constraints
 Finally, we prepare a preliminary strategy for achieving these objectives.<br>
 
 For our project, We are trying to accomplish
 * What attributes affect price? 
 * How much does it cost per mile depending on route and cab type?
 
 
 ### Data Understanding
The second stage of the CRISP-DM process requires us to acquire the data listed in the project resources. This initial collection includes data loading, if this is necessary for data understanding. The data-understanding phase includes three tasks. These are
* Gathering data
* Describing data
* Exploring data

#### Gathering Data
We need to verify that we have acquired the data or at least gained access to the data, tested the data access process, and verified that the data exists. First we need to Outline data requirements, Verify data availability, Define selection criteria.<br>

We acquired the data from Kaggle Datasets. The dataset is Uber & Lyft Cab prices. You can download the dataset [here](https://www.kaggle.com/ravi72munde/uber-lyft-cab-prices).

#### Describing Data
We describe the source and formats of the data, the number of cases, the number and descriptions of the fields, and any other general information that may be important.<br>
Data is described using dataframes, info, shape, head, describe functions.<br>
* Dataframes gives data in table format<br>
* Info gives datatypes, no of columns, memory usage etc.<br>
* Shape determines no of rows and columns.<br>
* Head displays first 5 rows of dataframe.<br>
* Describe shows count, mean, std, min, max, percentiles, etc.

#### Exploring Data
We look at the range of values and their distributions using EDA. We’ll use simple data manipulation and basic statistical techniques like count_values, missing values, etc for further checks into the data. Data exploration supports several purposes:
* Get familiar with the data
* Spot signs of data quality problems
* Set the stage for data preparation steps<br>
 All these are done using visualization for easy interpretation of data. SNS countplot, violinplot, barplot, scatterplot, boxplot etc are used. We also use matplotlib plots like lineplot, barcharts,subplots, etc for exploring data. 


### Data Preperation
The data preparation phase includes three tasks. These are
* Cleaning data
* Constructing data
* Formatting data

#### Cleaning Data
We make changes, perhaps tracking down sources to make specific data corrections, excluding some cases or individual cells (items of data), or replacing some items of data with default values or replacements selected by a more sophisticated modeling technique.<br>
There are some missing data in the dataset. All the missing values are from prices attribute whose cab_type is taxi. We use a formula to predict prices. The attribute timestamp is removed as we derive time from it. Once the data is cleaned, we start modeling.

#### Constructing Data
We may need to derive some new attributes. For this dataset we derived few attributes from existing attributes. The dervied attributes are date, hour and fare_per_mile. The date and hour are derived from timestamp. Where as fare_per_mile is derived from price and distance. 

#### Formatting Data
The may need to be formatted. For example, the date might be in int or float, we need to convert it into date format. <Br>
 Here the date is in timestamp format. We change that into date format.


### Modeling

#### Selecting Modeling Techniques

For this dataset we are using Gradient Boosted Tree, Random Forest and Convolutional Neural Network.


### Evaluation
We evaluate not just the models you create but also the process that we used to create them, and their potential for practical use. The general evaluation metrics we use are Accuracy, Precision, and Recall, F1 Score, AUC-ROC Curve.

## Bias, Fairness, and Trust in AI
This topic is written as we are inspired by Dr. Doug Haugue, Professor of Practice - UNCC Data Science Initiative. <br>
Bias is often identified as one of the major risks associated with artificial intelligence (AI) systems. Recently reported cases of known bias in AI — racism in the criminal justice system, gender discrimination in hiring — are undeniably worrisome. The public discussion about bias in such scenarios often assigns blame to the algorithm itself. The algorithm, it is said, has made the wrong decision, to the detriment of a particular group. But this claim fails to take into account the human component: People perceive bias through the subjective lens of fairness.<br>
Here it can be helpful to consider how we are defining both bias and fairness. Bias occurs when we discriminate against (or promote) a defined group consciously or unconsciously, and it can creep into an AI system as a result of skewed data or an algorithm that does not account for skewed data. For example, an AI system that reviews job applicants by learning from a company’s historical data could end up discriminating against a particular gender or race if that group were underrepresented in the company’s hiring in the past.<br>
No AI system can be universally fair or unbiased. But we can design these systems to meet specific fairness goals, thus mitigating some of the perceived unfairness and creating a more responsible system overall. Any decision — especially those humans make — can be construed as unfair in some way to one or more people affected by it. But exploring these issues can bring you closer to achieving responsible AI that strikes a balance between business goals and ethical concerns, while cultivating the trust of customers and other stakeholders.



## Conclusion
Finally from the dataset we acheive useful insights based on pre-defined objectives.
