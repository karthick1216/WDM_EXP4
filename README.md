### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07/02/26 
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

### Program 1:
```python
import pandas as pd
df = pd.read_csv('/content/clustervisitor - 2.csv')
df
cluster = {"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"old":(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(visitors)
  vcount=len(count)
  print(f"The visitors on {group} age are")
  print(visitors)
  print("count=",len(visitors))

```

### Visualization 1:
```python
import matplotlib.pyplot as plt

age_group_labels = list(cluster.keys())

# Extract the actual numerical count (length) from each group's DataFrame
visitor_counts = [len(c) for c in count]

# Different colors for each bar
colors = ['blue', 'green', 'red']

# Plot
plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color=colors)

plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output 1:

<img width="1272" height="702" alt="image" src="https://github.com/user-attachments/assets/56630984-bea9-4f3f-b675-457c7c8651d1" />
<img width="717" height="864" alt="image" src="https://github.com/user-attachments/assets/931c2ccb-adbb-4f96-984c-2c50956670e2" />
<img width="878" height="689" alt="image" src="https://github.com/user-attachments/assets/87d5cf64-4b56-4918-af64-d4ff0ae86b18" />


### PROGRAM 2:
```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import pandas as pd

# Selecting Age and salary (corrected from Income)
df1 = df['Age']
df2 = df['salary']
df3 = pd.concat([df1, df2], axis=1)

# Initialize and apply StandardScaler
s = StandardScaler()
newdf = s.fit_transform(df3)

# Perform KMeans clustering
k = KMeans(n_clusters=4, random_state=42)
df3['cluster'] = k.fit_predict(newdf)
df3
```
### visualization 2:
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.scatter(df3['Age'],df3['salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary')
plt.title('visitor distribution different clusters')
```
### Output 2:
<img width="1274" height="692" alt="image" src="https://github.com/user-attachments/assets/ac5cdcdc-621f-41c0-b214-fe3ec96c03a5" />
<img width="896" height="687" alt="image" src="https://github.com/user-attachments/assets/a4ba2094-5e0d-48ba-bb2d-d80c2cd95d2c" />




### Result:
The Cluster and Visitor Segmentation for Navigation patterns in Python has been successfully implemented.
