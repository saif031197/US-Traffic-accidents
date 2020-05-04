# Prediction of traffic accidents in the US

Spring 2020 Knowledge Based Systems Final project
# Project Site
| [Google Cloud Console](https://console.cloud.google.com/home/dashboard?project=kbs-final-project) | [User Dashboard](https://datastudio.google.com/u/1/reporting/e3384c22-c9d5-4e66-b916-0e8ddf91c3f5/page/QryKB) | [Colab Notebook](https://colab.research.google.com/drive/1AL_JfULDYx4OxKifAW7gTJkpqUxHiG2M#scrollTo=QHzLs6Zflt-k) |
| ------ | ------ | ------ |

# Group Members
| [Akshaya Easwaran](https://github.com/Akshuhrsh) | 
 [Akshay Gupta](https://github.com/akshaygupta16) |    
 [Herleen Sanhotra](https://github.com/HerleenS) |    
 [Kanika Saini](https://github.com/skanikasaini6) |
 [Mohammad Saif](https://github.com/saif031197) |
|---------|---------|---------|---------|---------|


## Research question: 

We are building an early prediction system to predict the probability of severity of traffic accidents in the  US based on certain attributes like time, weather and location. The outcomes of this analysis will help the government authorities understand various factors that lead to traffic accidents and make sound decisions that can save thousands of lives every year.

## Audience Definition: 

The intended audience of our project are US road transportation officials, law enforcement officers, governement authorities as well as general public. The predictions from our project will help government authorities in mitigating road accidents and will also help in spreading awareness among the general public.

## Domain and Data: 

[We are using US-Accidents: A Countrywide Traffic Accident Dataset from Kaggle.](https://www.kaggle.com/sobhanmoosavi/us-accidents)

This dataset is a countrywide traffic accident dataset that has been collected from 49 states of the USA. The data is captured from a variety of sources namely US departments of transportation, law enforcement agencies, traffic cameras, and traffic sensors.

This data can be used to carry out various predictions like accident-prone areas i.e geographic locations where it is most likely for accidents to occur, probability of severity of accidents. We can also predict what external factors contribute the most to vehicular accidents such as weather conditions (snow, rain, thunderstorm, etc) or accidents caused due to breaking traffic rules. The dataset briefly describes these factors using attributes such as Weather_Condition, Bump, Crossing, Give_way, Junction, No_exit, Railway, Traffic_Signal, etc. The data is also geographically sorted using the attributes City, County, State, Zipcode, and Country. Another vital information the dataset includes is the Period of the Day which indicates whether the accident occurs during the day or night. The NC driving handbook guide suggests that night time driving is much more dangerous than day time driving due to a number of reasons.

### Preprocessing that may be necessary 

1. The first and foremost preprocessing would be checking for NULL values. If a column contains more than 80% of missing values, that column shall be dropped. Data imputation needs to be done otherwise.
2. Standardizing records would be the next step as the values have different ranges. Standardization will be applied to numeric columns of the dataset like Pressure(in), Visibility(mi), Wind_Chill(F), etc. 
3. Text mining needs to be done for the columns: Start_Time, End_Time, Street, Weather_Timestamp. 
4. Data Encoding on all the categorical columns (City, Country, Timezone, etc) can also be done. 

### Size of data:

There are 3 million accident records in this dataset collected from February 2016 to December 2019. The dataset has 49 columns(attributes) that are both categorical and numerical.

### Exploratory Data Analysis

<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/EDA/Accident%20Prone.png" width="590">
<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/EDA/Severity.png" width="442">
<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/EDA/Severity%20States.png" width="1131">
<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/EDA/Visibility.png" width="704">

## Detailed plan for data ingest, ML, Evaluation of Results and Presentation of Results

#### Data Ingest - 
For this task we created a bucket on GCP and uploaded our dataset and made it public so that it can be accessed from anywhere by anyone and its especialyl useful when working on google colab outside of GCP

### Machine Learning - 
Before starting on the Machine Learning model we need to deal with missing values as needed depending on the type of data, either remove the feature entirely or impute the missing values with mean, mode or median.

### Evaluation of Results - 
Since this is a huge dataset with around 3 million entries, splitting the data into test and train could be beneficial but a better way to evaluate the model is to use cross validation.

### Presentation of Results-
A display of the most contributing factors to the severity of accidents and test scenarios where how changing a factor leads to different results.

## 43 Rules of Machine Learning

While there may be that many rules not all of them are relevant to our project so as a result, we’re going to discuss the rules that we feel are relevant to our project.

### Rule 2: First, design and implement metrics
This rule explains how looking at metrics before building the model ensures that we don’t run into problems later and to be liberal when gathering metrics, our project will explore several different metrics which ensures that we get a broader perspective
### Rule 4: Keep the first model simple and get the infrastructure right
Building a simple model as a baseline for building complex models
### Rule 7: Turn heuristics into features or handle them externally.
This rule tells how to add old heuristics that contain important information to the machine learning system. For our project, we will explore existing heuristics and will try to include them in our machine learning model as the rule says.
### Rule 11: Give feature columns owners and documentation
When dealing in a dataset with many features we need to keep track of who is managing what feature and assign roles to members accordingly, our project has 49 features so each of us will get around 10 features to play with.
### Rule 17: Start with directly observed and reported features as opposed to learned features
Learned features are created using external systems and if an external system is used to create a feature, remember that the external system has its own objective. The external system's objective may be only weakly correlated with your current objective.
### Rule 20: Combine and modify existing features to create new features in human-understandable ways
In the pre-processing step, some features can be transformed to create new features. The discretisation of continuous features is one way to do so. For our project we have used this to transform the continuous feature ‘Temperature’ and create a new feature ‘Binned_Temperature(F)’.Similarly, the features ‘Wind_Chill’, ‘Humidity’ and ‘Pressure’ can be converted into new features with discrete values.
### Rule 22: Clean up features you are no longer using
Any unnecessary feature which is not being used in the model should be dropped. This way the relevant features can work faster for our models. In the initial stages of our project, we dropped a few features with more than 100k missing records. We can always add back these features if it gives meaningful results in our models in later stages. 
### Rule 30: Importance-weight sampled data
In a nutshell, attributes should be inspected before being dropped.
### Rule 39: Launch decisions are a proxy for long-term product goals
The final product must be evaluated in such a way that it tells its performance for the next five years. All the metrics should be taken into consideration. Various error metrics and performance metrics will be used in this project.
### Rule 41: When performance plateaus, look for qualitatively new sources of information to add rather than refining existing signals.
When evaluating our model and the performance doesn’t seem to increase, looking towards adding new features might yield better results than trying to fine tune the existing ones.


## Steps for AutoML in GCP

## Results and Evaluation

We have 2 AutoML models for our evaluation, the first one was just testing the waters and checking AutoML's capabilities so as a result we limited the training node-hour to 1, the minimum allowed in order to make it budget friendly, after evaluating the result with Model 1 we went ahead and performed the same training but with 5 node-hours instead, exhausting our complete budget in the process but getting slightly better results. Model 2 will serve as the basis of our final evaluation but a summary of Model 1 has been provided for reference.

<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/Results/Model_1_Summary.png">

_Summary for Model 1_

<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/Results/Model_2_Summary.png">

_Summary for Model 2_

### Model 2 Evaluation

* Area under [_precision-recall_ curve](https://www.geeksforgeeks.org/precision-recall-curve-ml/): 0.944
* Area under [_ROC_ curve](https://towardsdatascience.com/understanding-auc-roc-curve-68b2303cc9c5): 0.981
* [Precision](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c): 87.0%
* [Recall](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c): 86.8%
* [Log loss](https://towardsdatascience.com/understanding-binary-cross-entropy-log-loss-a-visual-explanation-a3ac6025181a): 0.318 
* [F1 Score](https://deepai.org/machine-learning-glossary-and-terms/f-score): 0.869

Confusion Matrix for prediction on testing data:

<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/Results/Model_2_CM.png">

Feature Importance:

<img src="https://github.com/saif031197/US-Traffic-accidents/blob/master/Results/Model_2_Feature_Importance.png">


## Tentative plan for analysis on GCP

| **Task**        | **Plan**           | **Date**  |
| ------------- | ------------- | ----- |
| *EDA and preprocessing*      | *Thoroughly going over the dataset to discover patterns, spot anomalies, test the hypothesis and check the assumptions through summary statistics and graphical representation. We would also perform the preprocessing steps mentioned in preprocessing and create a notebook with preprocessing steps.*  | *03/26/2020* |
| *Dashboard for User group, Dashboard for Data Engineers*      | *Creating a meaningful dashboard using Data Studio for users that tells them what we are trying to predict in simple terms. Creating a dashboard for Data Engineers in Data Studio going deeper into the attributes that were used for metrics and the analysis we are trying to achieve. We will use MySQL or BigQuery in GCP to be the source for Data Studio.*|  *03/26/2020* |
| *GCP further processing - ML* | *After getting insights from visualization of the data, supervised and unsupervised machine learning algorithms will be implemented. This is a binary classification problem. Classification algorithms like logistic regression, gradient boosting classifier, decision tree classifier, etc will be implemented.*|  *04/14/2020* |
| *Evaluation of results* | *The results will be evaluated using various error metrics like Absolute Mean Error, Squared Mean Error, etc. The lower the error metric value, the better the model. ROC curve can also be visualized.* | *04/16/2020* |
| *Steps for the production model* | *Further optimization can be done based on previous results using GridSearchCv or RandomSeacrhCV.* | *04/23/2020* |
| *Final Dashboard for User Group* | *Final dashboard with the visualizations of the performances of all the algorithms will be included. This will give an idea about the best working model to the user.* | *04/30/2020*|
| *Changes to the Dashboard* | *This step will be implemented if the dataset is updated by the author in the near future or if any additional algorithms are to be implemented.* | *05/04/2020*|



## Research Citations:
1. Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, and Rajiv Ramnath. “A Countrywide Traffic Accident Dataset.”, 2019.

2. Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, Radu Teodorescu, and Rajiv Ramnath. "Accident Risk Prediction based on Heterogeneous Sparse Data: New Dataset and Insights." In proceedings of the 27th ACM SIGSPATIAL International Conference on Advances in Geographic Information Systems, ACM, 2019.

3. [Road Accidents in US.](https://www.kaggle.com/biphili/road-accidents-in-us)

4. [Notebook to predict severity of accident](https://www.kaggle.com/phip2014/ml-to-predict-accident-severity-pa-mont)

The research paper “A Countrywide Traffic Accident Dataset.” provided us the dataset upon which our project is built on.The dataset includes important contextual information such as environmental stimuli which helps us in predicting the causes for road accidents.The research paper "Accident Risk Prediction based on Heterogeneous Sparse Data: New Dataset and Insights." shows the impact of traffic information, time and points-of-interest data for real-time accident prediction. The paper helps us in understanding the factors that need to be considered for real-time accident prediction. The kaggle kernel link helped us in understanding the dataset more clearly and also the preprocessing steps performed in it inspired some of our preprocessing steps. The kernel had many visualizations and gave us  some valuable insights on the dataset. The Notebook link from Kaggle helped us in the cleaning of the dataset.




