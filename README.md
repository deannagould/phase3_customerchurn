# SyriaTel Customer Churn

![SyriaTel](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/syriatel.png)

https://www.linkedin.com/company/syriatel/

**Deanna Gould**  
**Data Science Flex**

## Overview

SyriaTel is a mobile network provider that would like to understand why customers are churning, and how to prevent it. Currently, the dataset overall has a 14.5% churn rate. However, the churn rate is significantly higher in some states, with the highest states being New Jersey and California, with a 26.5% churn rate. 

### About the Data

There are 3,333 rows of data in the dataset, with 2850 customers that didn't churn, and 483 customers that did churn.

`state`: state the plan is in  
`account length`: length of time the account has been open  
`area code`: area code of the phone plan  
`phone number`: phone number  
`international plan`: indicator of international plan  
`voicemail plan`: indicator of a voicemail plan  
`number vmail messages`: number of voicemail messages  
`total day minutes`: minutes spent during the day  
`total day calls`: number of calls during the day  
`total day charge`: total charge for day calls  
`total eve minutes`: minutes spent during the evening  
`total eve calls`: number of calls during the evening  
`total eve charge`: total charge for evening calls  
`total night minutes`: minutes spent at night  
`total night calls`: amount of night calls  
`total night charge`: total charge for night calls  
`total intl minutes`: total international minutes  
`total intl calls`: number of international calls   
`total intl charge`: total international charge  
`customer service calls`: amount of customer service calls  
`churn`: whether a customer churns or not  

**Overall Churn**

![Churn Countplot](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/churn_countplot.png)

**Churn by State**

![Churn by State](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/churn_bystate.png)

## Strategy

I will cover several different types of models including Logistic Regression, RandomForest, XGBoost, and each will also have a version with GridSearchCV. I decided to use an F1 score instead of accuracy, because an accuracy score can be inflated by the number of true positives, which in this dataset, is quite a lot. 

Below is the confustion matrix from the baseline logistic regression model.
**Whole Number Confusion Matrix**

![First Confusion Matrix Whole Number](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/first_conf_int.png)

**Confusion Matrix Percentages**

![First Confusion Matrix Perfent](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/first_conf_percent.png)


## Conclusion

The best performing model was XGBoost with GridSearchCV. The average F1 score was 0.85, and the best F1 score was 0.95. The amount of true positives predicted in the model was 95, with only 27 false negatives. 

**Final Confusion Matrix**

![Final Confusion Matrix](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/conf_int.png)

**Feature Importances**

![All Feature Importances](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/ftr_imp_all.png)

Above are the feature importances based on the final model, which may be difficult to see, so the top five are below.

**Top 5 Features**

![Top Feature Importances](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/top5_ftrs.png)

**Churn by Customer Service Calls**

![Customer Service Churn](/Users/deannagould/Documents/phase3_project/phase3_customerchurn/Images/custsvc_churn.png)

As you can see, the international plan is the biggest indicator that a customer will churn, followed by the amount of customer service calls that were made. In addition, the state of Florida as well as DC have high importance for churn rates. SyriaTel does charge for a voicemail plan, but I am not sure if they charge an additional rate for the number of voicemail messages left.  

Due to the nature of the model, I can not say whether or not there is a positive or negative impact from the features, but I can make assumptions based on the importances. I can assume that customers with an international plan can have a higher monthly expense. SyriaTel may want to consider investing more in popular countries of their clients to potentially lower costs initially.  

In addition to that, if SyriaTel does not already record customer service calls for quality assurance and training purposes, they may want to consider doing so. If they do, it would be in their best interest to make sure that in situations where a customer has called several times, it is handled as efficiently and carefully as possible. 

If SyriaTel does charge more for the amount of voicemails, they could also consider charging a slightly higher initial cost for a voicemail plan to lower the additional charge per voicemail received.  

## Next Steps

Overall, I'm satisfied with the current state of the model. If SyriaTel records customer service calls, Natural Language Processing (NLP) could be a great tool to learn more about those high risk calls.

## Repository Structure


├── Data
│   └── churndata.csv
├── Images
│   ├── churn_bystate.png
│   ├── churn_countplot.png
│   ├── churn_heatmap.png
│   ├── churn_staterates.png
│   ├── conf_int.png
│   ├── conf_percent.png
│   ├── custsvc_churn.png
│   ├── daymin_hist.png
│   ├── first_conf_int.png
│   ├── first_conf_percent.png
│   ├── ftr_imp_all.png
│   ├── syriatel.jpeg
│   ├── syriatel.png
│   └── top5_ftrs.png
├── README.md
└── model_notebook.ipynb