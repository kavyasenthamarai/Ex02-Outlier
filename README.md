# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
```
   ## Aim:
TO detect and remove the outliers in the given data set and save the final data.

Algorithm:
##Step 1:
Import the required packages(pandas,numpy,scipy)

##Step 2:
Read the given csv file

##Step3:
Convert the file into a dataframe and get information of the data.

##Step 4:
Remove the non numerical data columns using drop() method.

##Step 5:
Detect the outliers in the data set using z scores method.

##Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

##Step 7:
Check if the outliersare removed from data set using graphical methods.

##Step 8:
Save the final data set into the file.

Program:
    
Program developed by : kavya.k
Register number : 212222230065

import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/bhp.csv")

df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]

df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)

##(3)Examine price_per_sqft column and use zscore of 3 to remove outliers. from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)

##(4)(i) For the data set height_weight.csv detect weight outliers using IQR method. import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/height_weight - Sheet1.csv")

df

df.head()

df.info()

df.describe()

df.isnull().sum()

df.shape

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]

df1

df1.shape

sns.boxplot(x="weight",data=df1)

##(4)(ii) For the data set height_weight.csv detect height outliers using IQR method. sns.boxplot(x="height",data=df)

q1 = df['height'].quantile(0.25)

q3 = df['height'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df2 =df[((df['height']>=ll)&(df['height']<=ul))]

df2

df2.shape

sns.boxplot(x="height",data=df2)
```
##Output:

##(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

##Dataset:
![image](https://user-images.githubusercontent.com/118668727/229698290-d35af02b-ef9d-462b-905a-91d9d34b104f.png)
##Dataset Head :
![image](https://user-images.githubusercontent.com/118668727/229698481-46d221dc-7b93-4ec1-a047-a3efed0b0ea7.png)
##Dataset Info :
![image](https://user-images.githubusercontent.com/118668727/229698576-0b9f96b9-ac3b-4086-bb21-0a7dc5a9afb3.png)
![image](https://user-images.githubusercontent.com/118668727/229698652-c7a2f430-c3f4-47c9-b794-b7272fcbc703.png)
##Dataset Describe:
![image](https://user-images.githubusercontent.com/118668727/229699521-6db300eb-9b0b-42b7-bd2c-757eef7e89a6.png)
##Null Values:
![image](https://user-images.githubusercontent.com/118668727/229698793-fa220695-0b97-4327-9bae-c03c141e8e1d.png)
##Dataset Shape:
![image](https://user-images.githubusercontent.com/118668727/229698940-96363ad4-29d8-418a-95f8-a2417577a30d.png)
##Box plot of price_per_sqft column with outliers:
![image](https://user-images.githubusercontent.com/118668727/229699114-843c39cf-e0a3-4e53-8798-79e445622244.png)
##price_per_sqft - Dataset after removing outliers:
![image](https://user-images.githubusercontent.com/118668727/229699233-0de6b9b0-91cb-4cf8-807f-07dff950443a.png)
##price_per_sqft - Shape of Dataset after removing outliers :
![image](https://user-images.githubusercontent.com/118668727/229699324-ecdaa3c1-1b36-48c0-b409-3038b95d7bd4.png)
##Box Plot of price_per_sqft column without outliers:
![image](https://user-images.githubusercontent.com/118668727/229700222-d4f081cc-69ac-4256-8bd4-11700afefe14.png)
##(3) Examine price_per_sqft column and use zscore of 3 to remove outliers. ##Dataset after removal of outlier using z score:
![image](https://user-images.githubusercontent.com/118668727/229700354-21228453-7485-465d-a273-785c02d1abf6.png)
##Weight - Without Outliers using IQR method
![image](https://user-images.githubusercontent.com/118668727/229700821-e2799d85-8a7a-47ca-aa8a-39d45ab2a90e.png)
##Height - With outliers: 
![image](https://user-images.githubusercontent.com/118668727/229700970-b1d6b0fb-89d1-4cd2-b457-4fcab3213067.png)
##Height - Dataset after removing Outliers using IQR method:
![image](https://user-images.githubusercontent.com/118668727/229701016-290e99d8-7c12-4179-9313-c9fa2cf94d0a.png)
##Height - Shape of Dataset after removing Outliers using IQR method:
![image](https://user-images.githubusercontent.com/118668727/229701092-da0416cb-ff67-45b4-8ded-303575cc2a7b.png)
##Height - Without Outliers using IQR method: 
![image](https://user-images.githubusercontent.com/118668727/229701149-27927904-a105-49c6-b8c6-d804982d553f.png)
##Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
