# ITCS6155-KBS-Spring2020-Project

# Project Site
TBA

# Group Members
|Name     | 
|---------|
|[Akshaya Easwaran](https://github.com/Akshuhrsh)| 
|[Akshay Gupta](https://github.com/akshaygupta16) |    
|[Herleen Sanhotra](https://github.com/HerleenS) |    
|[Kanika Saini](https://github.com/skanikasaini6) |
|[Mohammad Saif](https://github.com/saif031197) |

## Research question: 

We are trying to predict the chances for traffic accidents in the  US based on certain attributes like time, weather and location. The outcomes of this analysis will help the government authorities understand various factors that lead to traffic accidents and make sound decisions that can save thousands of lives every year.

## Domain and Data: 

[We are using US-Accidents: A Countrywide Traffic Accident Dataset from Kaggle.](https://www.kaggle.com/sobhanmoosavi/us-accidents)

This dataset is a countrywide traffic accident dataset that has been collected from 49 states of the USA. The data is captured from a variety of sources namely US departments of transportation, law enforcement agencies, traffic cameras, and traffic sensors.

This data can be used to carry out various predictions like accident-prone areas i.e geographic locations where it is most likely for accidents to occur. We can also predict what external factors contribute the most to vehicular accidents such as weather conditions (snow, rain, thunderstorm, etc) or accidents caused due to breaking traffic rules. The dataset briefly describes these factors using attributes such as Weather_Condition, Bump, Crossing, Give_way, Junction, No_exit, Railway, Traffic_Signal, etc. The data is also geographically sorted using the attributes City, County, State, Zipcode, and Country. Another vital information the dataset includes is the Period of the Day which indicates whether the accident occurs during the day or night. The NC driving handbook guide suggests that night time driving is much more dangerous than day time driving due to a number of reasons.

### Preprocessing that may be necessary 

1. The first and foremost preprocessing would be checking for NULL values. If a column contains more than 80% of missing values, that column shall be dropped. Data imputation needs to be done otherwise.
2. Standardizing records would be the next step as the values have different ranges. Standardization will be applied to numeric columns of the dataset like Pressure(in), Visibility(mi), Wind_Chill(F), etc. 
3. Text mining needs to be done for the columns: Start_Time, End_Time, Street, Weather_Timestamp. 
4. Data Encoding on all the categorical columns (City, Country, Timezone, etc) can also be done. 

### Size of data:

There are 3 million accident records in this dataset collected from February 2016 to December 2019. The dataset has 49 columns(attributes) that are both categorical and numerical.

### Tentative plan for analysis on GCP

| **Task**        | **Plan**           | **Date**  |
| ------------- | ------------- | ----- |
| *EDA and preprocessing*      | *Thoroughly going over the dataset to discover patterns, spot anomalies, test the hypothesis and check the assumptions through summary statistics and graphical representation. We would also perform the preprocessing steps mentioned in preprocessing.*  | *03/26/2020* |
| *Dashboard for User group, Dashboard for Data Engineers*      | *Creating a meaningful dashboard using Data Studio for users that tells them what we are trying to predict in simple terms. Creating a dashboard for Data Engineers in Data Studio going deeper into the attributes that were used for metrics and the analysis we are trying to achieve. We will use MySQL or BigQuery in GCP to be the source for Data Studio.*|  *03/26/2020* |
| *GCP further processing - ML* | *After getting insights from visualization of the data, supervised and unsupervised machine learning algorithms will be implemented. This is a binary classification problem. Classification algorithms like logistic regression, gradient boosting classifier, decision tree classifier, etc will be implemented.*|  *04/02/2020* |
| *Evaluation of results* | *The results will be evaluated using various error metrics like Absolute Mean Error, Squared Mean Error, etc. The lower the error metric value, the better the model. ROC curve can also be visualized. * | *04/16/2020* |
| *Steps for the production model* | *Further optimization can be done based on previous results using GridSearchCv or RandomSeacrhCV.* | *04/23/2020* |
| *Final Dashboard for User Group* | *Final dashboard with the visualizations of the performances of all the algorithms will be included. This will give an idea about the best working model to the user.* | *04/30/2020*|
| *Changes to the Dashboard* | *This step will be implemented if the dataset is updated by the author in the near future or if any additional algorithms are to be implemented.* | *05/04/2020*|


