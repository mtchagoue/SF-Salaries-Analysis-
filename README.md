# SF-Salaries-Analysis-
# SF Salaries Analysis - Pandas Python Analysis

![image](https://github.com/mtchagoue/Retail-data-analysis/assets/115325778/44af86d5-0277-4063-91d4-f33c1192c8b2)

## **Introduction:**
Also known as “Golden Gate City” -  “San Fran” , San Francisco is known for its Golden Gate Bridge, steep streets, Alcatraz… It is the thirteenth largest city in the United States. Let’s analyze its employees’ salaries.

## **Problem Statement:**
Our interest here is to find the minimal, maximum salary; the job type to earn the maximum salary in SF. While doing so we will answer questions, explore the data with Pandas in Python
1.  Display Top 10 Rows of The Dataset

data = pd.read_csv(r'C:\Users\Archange\Desktop\Salaries.csv')

data.head()

3. Check Last 10 Rows of The Dataset

data.tail(10)

5. Find Shape of Our Dataset (Number of Rows And Number of Columns)

data.shape

print('Number of rows:',data.shape[0])

print('Number of Columns:', data.shape[1])

7.  Getting Information About Our Dataset Like Total Number Rows, Total Number of Columns, Datatypes of Each Column And Memory Requirement

data.info()

9. Check Null Values In The Dataset

data.isnull().sum()

11. we will not need: ID, Notes, Agency, and Status Columns in our analysis. Why don’t we just drop them don’t forget to specify the  argument axis=1

data = data.drop(['Id','Notes', 'Agency', 'Status'], axis=1)  

13. Get Overall Statistics About The Dataframe

data.describe()

15. Find Occurrence of The Employee Names  (Top 5)

data['EmployeeName'].value_counts().head()

17. Find The Number of Unique Job Titles

data['JobTitle'].nunique()

10.Total Number of Job Titles Contain Captain (here we can play with the argument  case=False for case sentivity –lower or upper case)

len(data[data['JobTitle'].str.contains('CAPTAIN', case=False)])

19. Display All the Employee Names From Fire Department

data[data['JobTitle'].str.contains('fire', case=False)] ['EmployeeName']

21. Find Minimum, Maximum, and Average BasePay

data['BasePay'].describe()

24. Replace 'Not Provided' in EmployeeName' Column to NaN => interesting question here as we need to import np numpy to answer the question

import numpy as np

data['EmployeeName'] = data['EmployeeName'].replace('Not provided',np.nan) 

25. Drop The Rows Having 5 Missing Values => really interesting question and answer

data.drop(data[data.isnull().sum(axis=1)==5].index, axis=0)

26. Find Job Title of ALBERT PARDINI

data[data['EmployeeName']==('ALBERT PARDINI')]['JobTitle']

28. How Much ALBERT PARDINI Make (Include Benefits)?

data[data['EmployeeName']== ('ALBERT PARDINI')] 

17.Display Name of The Person Having The Highest BasePay

data[data['BasePay'].max() == data['BasePay']]['EmployeeName']

18.Find Average BasePay of All Employee Per Year

data[data['BasePay'].mean() == data['BasePay']]

30. Find Average BasePay of All Employee Per JobTitle
    
32. Find Average BasePay of Employee Having Job Title ACCOUNTANT  
33. Find Top 5 Most Common Jobs
## **Data sourcing:**
Datalink: We get the data from Kaggle. This is the link: https://www.kaggle.com/datasets/kaggle/sf-salaries


## Analysis and Visualization:
## Analysis:
The city of SF has a total of 1552 jobs. The average base salary is $70k. 
The maximum salary is $302k. It is good to be a Zoo Curator(Highest paid job). 👍

The visualization looks like this:

![image](https://github.com/mtchagoue/Retail-data-analysis/assets/115325778/f03c005e-8921-4633-beb2-513aeface325)

![image](https://github.com/mtchagoue/Retail-data-analysis/assets/115325778/068c9cc5-ac0b-4cde-bc53-06530b605ec5)

