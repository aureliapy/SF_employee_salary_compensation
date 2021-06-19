# SF_employee_salary_compensation
San Franciso City Employees Salary Database
> The San Francisco Controller's Office maintains a database of the salary and benefits paid to City employees since the fiscal year 2013. This dataset contains more than 650k employee records found in San Francisco from 2013 to 2020. The dataset consists of 678,524 rows and 22 columns. The dataset was obtained from the website of [Kaggle]. 

## Table Content
* [Problem Statement](#problem-statement)
* [Technologies](#technologies)
* [Features](#features)
* [Problem Description](#problem-description)
* [Summary of Dataset](#summary-of-dataset)
* [Conclusion](#conclusion)
* [Room for Improvement](#room-for-improvement)

## Problem Statement
The project objective is to develop a compensation prediction model, which calculates the total sum of additional benefits to your salary.
This is a regression problem to forecast the total compensation of city’s employees based on his or her overtime, other salaries, retirement, health and dental and other benefits.
It will help the City for offering competetive pay to existing and future employees while aslo keeping payroll expenses in check. 

## Technologies
Project is created with: 
* Python

## Features
Attached [Feature Listing] for the features in this [Dataset]

## Problem Description 
* Before starting actual analysis, a lot of cleaning needs to be done on the data. 
* There are also some missing values which needs to be replaced. 
* Same code with multiple similar values for the 4 features - Job, Union, Department and Job Family. 
* Categorized unassigned Job Family based on their Union Group. 
* Selection of encoding method for categorical feature. 

## Summary of Dataset
#### 1. Evaluation
* There are 2 types of calendar from the dataset and we have drop the "Calendar" due to the financial forecasting will be using "Fiscal" for further insights. 
* The most important attributes were Organization Group, Department, Job, Salaries and Benefits. Total Compensation is the target of our prediction model. 

#### 2. Analysis
* We have removed Employee Identifier and Year Type that is not useful for predictive task.
* There are 8 years data from 6 organization group data from the city San Fransico which contains 58 different department and it had been grouped into 24 Job Family.
* From the distribution plot of numerical columns, we observed that there are negative values for most of the columns including the Target.
  > It may due to the adjustment of wages, benefits have overpaid or employees have leave the the organization but the benefit had been overclaimed. By health and dental wise, it is a group insurance that covered by year hence the organization may have to recover back as well.
  > Example, an employee who was overpaid at the end of Fiscal year 2013 with an adjustment to correct the mistake not occurring until the beginning of Fiscal year 2014. If the employee did not receive other payment in FY2014 for the same department and job, the report would show only this adjustment for the employee as a negative amount.
* There may have zero dollar amounts. Zero-dollar amounts could be a separated employee receiving a one-time payout of accrued vacation hours but no other salary or benefits during the period. Hence the employee will have zero amount in "Salaries","Overtime" or other benefits categories and only have "Other Salaries".
* It has outlier due to the negative values from all numerical columns however we will not drop the negative values except for "Total Compensation". As negative values needed to be use for prediction as it is one of the records affect the total from the forecasting.
* Among all the features correlation, all the categorical features are not correlated with numerical features. However it is normal for numerical features is related as the sum of all the features is the target feature.
* The top count from categorical variable of the dataset: 
    * Organization Group - Public Works, Transportation and Commerce
    * Department - Public Health
    * Job - Transit Fare Inspector
    * Job Family - Revenue

## Conclusion
During model training, 10 models was selected for baseline training as per below and the models were evaluated using MAE as the evaluation metric. 
   * Random Forests 
   * XGBoost
   * AdaBoost
   * ExtraTress
   * DecisionTrees
   * Linear Regression
   * Gradient Boosting
   * Histogram Gradient Boosting
   * Elastic Net
   * K Neighbors 
Based on baseline model results, Random Forests and ExtraTrees with the lowest values of MAE was chosen for hyperparameter optimizations optimized to improve the metric results.
Results: The best model performance is Extra Tree Regressor because it has the lowest average discrepancy between actual and predicted value. Compared to other models which do not have improvement after tuning. Extra Tree Regressor can forecast the compensation with mean absolute percentage error (MAPE) of 0.67% which are a very good results with a lower error rate.

The prediction model is able to help The San Francisco Controller's Office to have better planning of their budget and resources to help prevent under or over estimations and maintain a stable calculation through the years to come. It can also help the city to request more manpower cost if they know in advance. 
The City may have more time to requisite funds for essential stuff to make good of the city and provide maintenance of the public places after having sufficient fund for their manpower cost. They can take this opportunity to cut cost on certain department and provide adequate remuneration for the lower wage jobs. 

## Room for Improvement
- To have more EDA on the dataset
- Use PCA to apply dimension reduction on our dataset which helps to determine the most significant features for representing the variations. 
- Use pickle to store model training results to avoid longer timing of running the fitting model again after the script closed. 
- Train the feature separately and ensemble difference algorithms to have better results. 


This project was done as part of DS106 project requirement of Applied Data Science with Machine Learning in MAGES of Institute of Excellence - 2021. 

[Kaggle]:https://www.kaggle.com/siddheshera/san-francisco-employee-salary-compensation
[Feature Listing]:https://drive.google.com/drive/folders/1k6TOzQx9n8qJqo5kIeHvXmDOOEeefdH1?usp=sharing
[Dataset]:https://drive.google.com/file/d/1lOGW1oALwRZ1h5KhF9C_F9P_MRzKdY1R/view?usp=sharing
