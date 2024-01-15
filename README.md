# Game-App-Analysis
Analysis of data sets of a company developing mobile game application


## Project Overview
This data analysis project aims to provide insights related to the performance of the company developing mobile game application in terms of users and company’s actions to retain them. 
The main aims of this project are:
1.	To understand how the clients are segmented and how many customers tend to retain or leave the application.
2.	The testing team have presented the results of A/B tests during which the users were given two different promotional offers. It is required to evaluate the results of the tests and give data-driven recommendations.

## Data Sources
- Data set with time of registration of the users
- Data set with time of all activities of the users
- Data set containing revenue per each user and information which promotional offer such user was provided

## Tools
- Python
- Jupiter Notebook
- API Yandex
- Libraries: pandas, datetime, matplotlib, seaborn, requests, scipy, numpy
- Statistic methods: Chi-Square Test, T-Test, Mann-Whitney U Test, Bootstrap

## Part I. Segmentation of Clients

### Data Cleaning and Preparation
-	Data loading and inspection
-	Checking missing values
-	Data formatting

### Data Analysis
The idea is to identify the retention trends in the application. Since the data is for a long period of time (from 1998 till 2020) I decided to calculate the metric creating the function for retention so that it will be more convenient to use it if there is a requirement to check any period and if new periods of time are added. 

After applying the function to the data for one month of 2019 the retention table was been received. The creation table was further visualized with the use of heatmap.

### Limitations
The given datasets provide only timing of registration and actions of the users. I was able to identify the retention. However more information is required to make recommendation on how to improve retention.

### Conclusion
Based on the results of segmentation and provided we have further details on activities of the app, we can discuss further possibilities for improvement. We can determine the days when the retention drastically fell and see what happened on those days. Or vice versa, when the retention grows we can determine the happenings of those days (new promotions, featuers introduced etc.)

## Part II. Results of A/B Test

### Data Cleaning and Preparation
-	Data loading and inspection
-	Checking missing and duplicated values

### Exploratory Data Analysis
EDA involved exploring two groups of customers and revenue based on division into groups. All customers were divided into 4 groups: control group paying customers, control group non-paying customers, test groups paying customers, test group non-paying customers. EDA revealed that major part pf users hadn’t brought any revenue and the huge difference of maximum cheque between the two groups (A and B).
Also, it was obvious that there were significant outliers in Group A.

### Data Analysis
In this section I was looking into different metrics, viz.
 
-	Conversion into payer (this metric is 6.6% higher in Control Group)
-	ARPU (this is 5% higher in the Test Group)
-	ARPPU

*Assumptions*:

Since we have significant outliers in the Control Group, it was decided to further divide this group into two sub-groups (Group A Full and Group A Without Outliers). The revenues and ARPPU were further analysed for such division. 
Difference between Test Group and  Control Group Without Outliers: 893.08%
Difference between Test Group and Full Control Group: 12.75%

### Evaluation of Signoificance
1.	Evaluating significance of change in Conversion Rate using Ch-square Test.
2.	Evaluating significance of change in ARPPU using:
-	T-test
-	Mann Whitney U-Test
-	Bootsrap

### Results and Conclusions
1.	In the Control Group there is a segment of customers with significantly higher revenues, which explains the outliers in the distribution of revenues in this group. Maximum revenue in this segment is 37433, which is considerably higher than the maximum in the same group but without outliers (400). In the Test Group there is no such a segment. 

2. Conversion in the Test Group is 0.06 p.p. or 6.65% lower than in the Control Group.  The probability of statistical randomness of such decrease is 0.03 which is less than the assumed border (alpha-level) of 0.05. 


3. It is possible that the decrease of the conversion rate in the test group can be explained by the absence of high-revenue customers. Other reasons can also affect the decrease, but to check them we will need more data. 


4. ARPPU is 12.75% higher in the Test Group compared to Full Control Group. While undergoing statistical tests for the Full Control Group and Test Group we could only prove statistically significant difference under Mann–Whitney U test, where p-value was less than 0.05. Bootstrap for the difference in the means and T-Test showed p-value > 0.05. However, it should be noted that T-test was not quite adequate in this situation (absence of normality and homoscedasticity of distributions) and under bootstrap p-value was quite close to the benchmark of 0.05 (even in the conditions of considerable outliers when we compared means), we can rely on the Mann–Whitney U test.


5. When the outliers were excluded, we received increased in ARPPU by 893.08%. Statistical tests in this comparison showed p-value < 0.05. Bootstrap showed that the change is in the range between 2675.74 and 2726.91 with the probability of 95%.


6. Generally speaking the set of offers for the Test Group turned out to be better with high probability. Despite the decrease in the Conversion Rate, ARPU metric increased by 5% in the Test Group.   


7. New set of promotional offers can be used for all the customers. However, before doing this, it is recommended to make further research why the high-revenue segment disappeared from the Test Group and what are the possible actions to retain such customers. This will help to maintain conversion rate on the same level and increase total revenue.  

