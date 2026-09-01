### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 20-08-2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

df = pd.read_csv("clustervisitor.csv")

X = df[['Age']]

kmeans = KMeans(n_clusters=3, random_state=42)

df['Cluster'] = kmeans.fit_predict(X)

print(df)

for i in range(3):
    print(f"\nCluster {i}")
    print(df[df['Cluster'] == i])

```
### Output:
<img width="434" height="527" alt="image" src="https://github.com/user-attachments/assets/b132a99d-0510-44a4-800a-e87fc596ed33" />

<img width="419" height="231" alt="image" src="https://github.com/user-attachments/assets/d0d99a00-9236-4591-8c42-0e896d6417f4" />

<img width="421" height="217" alt="image" src="https://github.com/user-attachments/assets/5d465d18-23aa-42fe-b838-6b90b1dd6d38" />

<img width="400" height="196" alt="image" src="https://github.com/user-attachments/assets/8f1df2cd-20d3-46f7-b6e1-2851ee72fdb6" />

### Visualization:
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))

for i in range(3):
    cluster = df[df['Cluster'] == i]
    plt.scatter(cluster['Age'], cluster['Cluster'], label=f'Cluster {i}')

plt.scatter(
    kmeans.cluster_centers_,
    range(3),
    color='red',
    marker='X',
    s=200,
    label='Centroids'
)

plt.xlabel("Age")
plt.ylabel("Cluster")
plt.title("Visitor Segmentation using K-Means")
plt.legend()
plt.grid(True)
plt.show()
```
### Output:

<img width="692" height="448" alt="image" src="https://github.com/user-attachments/assets/adb9f6ac-d175-4ffc-8a3b-acacaf6278a7" />

### Result:

Thus the code has been executed successfully.
