# Ex-04-Multivariate-Analysis

AIM:

To perform Multivariate Exploratory Data Analysis on the given data set.

EXPLANATION:

Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

ALGORITHM:
STEP 1
Import the built libraries required to perform EDA and outlier removal.

STEP 2
Read the given csv file

STEP 3
Convert the file into a dataframe and get information of the data.

STEP 4
Return the objects containing counts of unique values using (value_counts()).

STEP 5
Plot the counts in the form of Histogram or Bar Graph.

STEP 6
Use seaborn the bar graph comparison of data can be viewed.

STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

STEP 8
Save the final data set into the file

CODE:
```
Developed by: NIVETHA K
Registration Number: 2122222230102
```
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 _Intro to DS/Exp_3/SuperStore.csv")
df

df.head()

df.info()

df.describe()

df.tail()

df.shape

df.columns

df.isnull().sum()

df.duplicated()

df['Postal Code'] = df['Postal Code'].fillna(df['Postal Code'].mode()[0])

df.isnull().sum()

states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("SALES")
plt.show()

states=df.loc[:,["Segment","Sales"]]
states=df.groupby(by=["Segment"]).sum()
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("SALES")
plt.show()

sns.barplot(df["Ship Mode"],df["Sales"],hue=df["Category"])

df.corr()
sns.heatmap(df.corr(),annot=True)

plt.figure(figsize=(10,7))
sns.scatterplot(df['Sub-Category'], df['Sales'], hue=df['Ship Mode'])
plt.xticks(rotation = 90)
```
OUTPUT

DATASET

![ex 4](https://user-images.githubusercontent.com/119559844/230065793-f63a179e-331a-47ae-a3b5-cce126036278.png)


DATASET HEAD

![ex 4 1](https://user-images.githubusercontent.com/119559844/230065882-c37a1d63-efd9-4d90-b02d-7d2d74baaf3f.png)


DATASET TAIL

![ex 4 3 ](https://user-images.githubusercontent.com/119559844/230066266-2aeaad36-aff8-46b2-95c2-bc80038e7a51.png)


DATASET INFO

![ex 4](https://user-images.githubusercontent.com/119559844/230066336-91eef7ed-f7dd-4047-9997-dcb7e6ec5140.png)


DATASET DESCRIBE

![ex 4 5](https://user-images.githubusercontent.com/119559844/230066424-ab0bd31e-17b0-4d38-8d64-98fc3598af4a.png)


DATASET SHAPE

![ex 4 6](https://user-images.githubusercontent.com/119559844/230066478-0aee97e3-ff48-41d9-98c7-ebf8d0fdb9af.png)


DATASET COLUMNS

![ex 4 8](https://user-images.githubusercontent.com/119559844/230066543-4be2abd1-d988-4b12-8687-3044c4185172.png)

Multivariate Analysis - Segment

![ex 4 9](https://user-images.githubusercontent.com/119559844/230066997-77a9680a-7419-49de-bedd-d9887ee417b2.png)

Multivariate Analysis - Ship Mode & Category vs Sales

![ex 4 10](https://user-images.githubusercontent.com/119559844/230067057-74b6e832-7759-4478-af23-6021a716c8e9.png)


Multivariate Analysis - Heat Map

![ex 4 11](https://user-images.githubusercontent.com/119559844/230067112-14efa207-b71d-472f-b601-e712e5133313.png)


Multivariate Analysis - Sub-Category & Ship Mode vs Sales

![ex 4 12](https://user-images.githubusercontent.com/119559844/230067138-041a213d-6886-454d-b33c-a34874ee23f2.png)


RESULT:
```
1.Most sales were from the California State
2.Most sales were from Consumer Segment
3.Most sales were from "New York City"
4.Most Sales were shipped on the Same Day and is most from Technology
5.Highest sale was from Machines Sub-category and is shipped in standard class
```
