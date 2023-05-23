# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
## Data Pre-Processing
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull().sum()
df.info()
df.describe()
```
## Segment that has Highest sales
```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```
##  City that have Highest profit
```
df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
```
## Which ship mode is profitable?
```
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()
```
## Sales of the product based on region.
```
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()
df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
```
## Find the relation between sales and profit.
```
df["Sales"].corr(df["Profit"])
```
```
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
```
```
sns.pairplot(df_corr, kind="scatter")
plt.show()
```
## Segment
```
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
## City
```
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
## States
```
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
## Segment and Ship Mode
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()
```
## Segment, Ship mode and Region
```
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```
# OUPUT

![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/c1cdfae1-79fe-4090-a024-8d73d7047274)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/d077b1de-f980-436d-a70c-79b197ec8e6d)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/3eb86ce0-0f61-4b74-8b70-ba7cff60525f)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/df03a6da-f012-4649-8527-4515aeb01cc6)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/bddecb0a-7d65-4167-bd68-0548146b8e22)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/c7ae81ce-68d3-46f6-9c59-fe02c6b74d9d)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/069d6ff1-e4ab-4e01-a106-988734cfb575)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/717ded1c-f08e-408d-9553-e27708b7f6f7)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/7ef581ac-7407-4a6f-b8a5-f308e68f4e9d)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/c90044bf-c49d-4333-b7c7-4104f32f78fc)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/88b2f862-c87a-4bae-acd4-e1eae064b2d0)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/fd506e14-9e1c-4fa3-aae2-e7acdbce5505)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/95fa8b2f-6d56-4427-8712-65b7e7e01b61)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/feb0a594-733e-4db3-9f79-53a73976e4e3)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/8e7fff20-e65c-4c48-8610-d8d9ef2294c3)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/e94fd08e-e72d-4cc0-b408-a246c048c37b)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/a032dfc7-3347-453a-956c-20453392ca84)
![image](https://github.com/Jayakrishnan22003251/Ex-08-Data-Visualization-/assets/120232371/5121e503-2a6e-49d7-b6e4-11775860eabf)

# RESULT
Thus, Data Visualization is performed on the given dataset and save the data to a file.
