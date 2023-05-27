# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the required libraries.
2. Read the data set and find the number of null data.
3. Import KMeans from sklearn.clusters library package.
4. Find the y_pred .
5. Plot the clusters in graph.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: S.Sham Rathan  
Registe.rNo : 21222123093  
*/

import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[] 

for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1,11),wcss)
plt.xlabel("No of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"]= y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")


```

## Output:
### 1. data.head() function:
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/cc3f4541-62ff-42f8-a28b-2a6388f68f63)
### 2. data.info():
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/9989635e-1b13-423d-8fb8-a18a3802384e)
### 3. data.isnull().sum() function
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/f2f60cec-f4df-4f79-9e5b-2d5dd1f6cb10)
### 4. Elbow method Graph:
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/14dcf48e-e4ac-4b68-9102-bc021ca2715e)
### 5. KMeans clusters
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/f9b059b2-56d1-4ec1-88a6-5f161ced5f72)
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/53bf9a34-30aa-4be2-b116-cdcbbbef1574)
### 6. Customer segments Graph
![image](https://github.com/ShamRathan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93587823/6dfff698-6130-4867-a006-430e050471b8)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
