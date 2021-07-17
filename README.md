
## Salary Prediction Case Study - Exploratory Data Analysis and Model Building
#### Prepared by : Kousik Das
<img src="https://cdn.hrpayrollsystems.net/wp-content/uploads/2020/01/Depositphotos_55140233_s-2019.jpg"/>
### Table of Contents:
### [1. Problem Statement ](#problem)
### [2. Loading Datasets](#loading)
### [3. Sample Data : How the dataset looks like](#sample)
### [4. Data Analysis : Data Insights](#dadi)
### [5. Understanding target variable in Detail](#target)
### [6. Data Visualization : Graphical way for More Insights](#dv)
<a id='problem'></a>
### 1. Problem Statement
Based on certain atributes for a Job, a model is required which can prdict salaray for a person for whom we know some other similar information.

This report is divided in below parts. In first section , some Exploratory Data Analysis has been shown to understand and strategise the model design in effective way.

A. Loading Available datasets and examine Summary Statistics

B. Understanding Data through Exploratory Data Analysis

C. Designing a efficient Machine Learning Model to predict Salary 

<a id='loading'></a>
### 2. Loading Datasets ( Section A)

Three datasets are avaialable for this Business Problem.

1. Dataset to train the Model : train_features.csv

2. Dataset to test the Model: test_features.csv

3. Salary Information for Training dataset: train_salaries.csv

All these 3 dataset loaded in Data folder of this repository.

<a id='sample'></a>
### 3. Sample Data : How the dataset looks like

Let's have a look on the actual dataset to get a primary understanding and idea to stratigise next coarse of actions.


|   | jobId            | companyId | jobType        | degree      | major     | industry | yearsExperience | milesFromMetropolis |
|---|------------------|-----------|----------------|-------------|-----------|----------|-----------------|---------------------|
| 0 | JOB1362684407687 | COMP37    | CFO            | MASTERS     | MATH      | HEALTH   | 10              | 83                  |
| 1 | JOB1362684407688 | COMP19    | CEO            | HIGH_SCHOOL | NONE      | WEB      | 3               | 73                  |
| 2 | JOB1362684407689 | COMP52    | VICE_PRESIDENT | DOCTORAL    | PHYSICS   | HEALTH   | 10              | 38                  |
| 3 | JOB1362684407690 | COMP38    | MANAGER        | DOCTORAL    | CHEMISTRY | AUTO     | 8               | 17                  |
| 4 | JOB1362684407691 | COMP7     | VICE_PRESIDENT | BACHELORS   | PHYSICS   | FINANCE  | 8               | 16                  |



Taining Dataset and Testing data set are identical in structure. First one will be used to train model and test set will be helpful to evaluate and decide on final model.

#### 3.3. Sample data for Salary(Target) corresponding to Training set

| jobId |           salary |     |
|------:|-----------------:|-----|
|     0 | JOB1362684407687 | 130 |
|     1 | JOB1362684407688 | 101 |
|     2 | JOB1362684407689 | 137 |
|     3 | JOB1362684407690 | 142 |
|     4 | JOB1362684407691 | 163 |

Salary value prsent in column 'salary' is in unit of 1000 USD. It is represnting salary value for corresponding job id as in the training dataset.

<a id='dadi'></a>
### 4. Data Analysis : Data Insights (Section B)

Training dataset having 8 columns, 1000000 rows. 2 Columns are numeric : 'yearsExperience' and 'milesFromMetropolis'.

There is no missing value as well as duplicate value in training data set.

#### Summary statistics for categorical columns:

|  jobId |        companyId | jobType |  degree |       major | industry |         |
|-------:|-----------------:|--------:|--------:|------------:|---------:|---------|
|  count |          1000000 | 1000000 | 1000000 |     1000000 |  1000000 | 1000000 |
| unique |          1000000 |      63 |       8 |           5 |        9 |       7 |
|    top | JOB1362684407687 |  COMP39 |  SENIOR | HIGH_SCHOOL |     NONE |     WEB |
|   freq |                1 |   16193 |  125886 |      236976 |   532355 |  143206 |

1. It can be said that jobid is a unique alphanumeric value and may not have much contribution to predict the target(salary).
2. 63 unique values present for CompanyID field, 8 unique Job Type, 5 different qualifications with 9 distinct Major values in 7 type of industries.

#### Summary statistics for numerical columns:

|  jobId |        companyId | jobType |  degree |       major | industry |         |
|-------:|-----------------:|--------:|--------:|------------:|---------:|---------|
|  count |          1000000 | 1000000 | 1000000 |     1000000 |  1000000 | 1000000 |
| unique |          1000000 |      63 |       8 |           5 |        9 |       7 |
|    top | JOB1362684407687 |  COMP39 |  SENIOR | HIGH_SCHOOL |     NONE |     WEB |
|   freq |                1 |   16193 |  125886 |      236976 |   532355 |  143206 |


Below are the insights for above numerical columns:

1. Years of experience varried almost symmetrically from 0 years to 24 years.

2. Distance from Metropolis is well distributed between 0 miles to 99 miles.

#### In Summary -

1. 63 Company Ids :- Example: COMP39,COMP37.
2. 8 Job Types :- SENIOR, VICE_PRESIDENT, MANAGER, CTO, JANITOR, CEO, JUNIOR, CFO.
3. 5 different Qualifications :- HIGH_SCHOOL, BACHELORS, MASTERS, DOCTORAL, NONE.
4. 9 Knowledge Majors :- NONE, CHEMISTRY, LITERATURE, ENGINEERING, BUSINESS, PHYSICS, COMPSCI, BIOLOGY, MATH.
5. 7 distinct Industries :-WEB, AUTO, FINANCE, EDUCATION, OIL, HEALTH, SERVICE.

<a id='target'></a>
### 5. Understanding target variable in Detail

[Salay Distribution](images/sal-ch.png)


While analyzing data , 5 rows having Salary value as '0' (Zero). This is unusual and suspected missing data. Those should be removed from training data.

Analyzing data greater than upper bound , it seems all are valid data.

<a id='dv'></a>
### 6. Data Visualization : Graphical way For More Insights


####  Correlation between selected features and Heat Map Visualization

This measure will give an insights about the relation among different features. it will even provide an understanding of impact of these on Salary ( target value). First two utility functions has been defined to include all categorical columns in correlation value claculation. 

This is an exploratory data analysis of Salary prediction dataset. It will act as an catalyst to design final model for Salary prediction in Part-II of this model buliding exercise. based on the above anaylysis below regression model can be recommended as a probable model algorithm.

1. Linear Regression
2. RandomForest 
3. GradienBoost

### 7. Model Building 

Three model has been built and the lowest MSE model has been choosed to produce the prediction file at result folder of this repository.



















