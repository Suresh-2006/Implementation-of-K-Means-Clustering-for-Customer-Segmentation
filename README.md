# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. .Import the necessary packages using import statement.

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3.Import KMeans and use for loop to cluster the data.

4.Predict the cluster and plot data graphs.

5.Print the outputs and end the program


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SURESH S 
RegisterNumber: 212223040215
*/

import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
```
```
data.head()
```
![image](https://github.com/user-attachments/assets/00a5974a-9589-47e6-ae77-69f15707169b)

```
data.info()
```
![image](https://github.com/user-attachments/assets/17ba549c-c162-4713-9fed-86de2ac95b5c)

```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/69193e95-1692-4902-971e-fa3bb1203074)

```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
  kmeans = KMeans (n_clusters = i, init ="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
```

```
plt.plot(range(1,11),wcss)
```
![image](https://github.com/user-attachments/assets/babd01d5-3429-4d9e-8888-cb26426fffe1)

```
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
```
![image](https://github.com/user-attachments/assets/8dcd5319-84a1-4df3-9444-8ab8d4e12c0c)

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
```
![image](https://github.com/user-attachments/assets/3c81b54b-55d5-4343-b168-6b320d106df9)

```
y_pred = km.predict(data.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/c0e92e54-2d8e-4151-a80d-dc073439d398)

```
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="black",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```
![image](https://github.com/user-attachments/assets/a9451c3a-0df0-4bf0-ac8d-ac23445c227e)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
