# EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION
**Made by**: Denise Wafa B. Españo
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>
This repository contains Programming Assignment 4 for our course, Advanced Computer Programming and Algorithm. The Project focuses on data wrangling and visualization techniques utilizing the Pandas and Matplotlib libraries


**Objectives:**
The objective of this activity is to demonstrate proficiency in data wrangling and visualization techniques. Specifically, this experiment focuses on filtering tabular datasets through multiple categorical and numerical criteria, constructing focused DataFrames by extracting key features, and summarizing the statistical relationships between categorical variables and numerical scores. Furthermore, it highlights the ability to effectively communicate data insights through clear, well-structured, and correctly labeled visualizations.
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

Before wrangling the data, the necessary Python libraries must be imported. Pandas is used for data manipulation, while Matplotlib is a comprehensive library used for creating static and interactive visualizations in Python. The dataset `board2.csv` is loaded into a DataFrame named  `df`. 

```python
import pandas as pd
import matplotlib.pyplot as plt
```
```python
df = pd.read_csv('board2.csv')
df
```

## A. VISAYAS COMMUNICATION DATAFRAME
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

```python
VisComm = df[(df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication')][['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm
```
The expression `df[(df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication')` evaluates element-wise across the DataFrame. Because Pandas operates on boolean, the biwtwise AND operaator `&` is required instead of the Python logical and. This evaluates to True only for records meeting both criteria. 

Following the row, a list of column labels `[['Name', 'Gender', 'Math', 'Electronics', 'Average']]` extracrts those specific attributes in that exact sequence, storing the final output in VisComm. 

```python
print("Number of rows:", VisComm.shape[0])`
```
The `.shape` return a tuple representing (row, columns). `VisComm.shape[0]` returns 5, verifying the row count of the filtered slice without reading the entire table into a loop. 

## B. VISAYAS FEMALE DATAFRAME
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

```python
VisFemale = df[(df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female')][['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale
```
Just like the previous problem, the pairs `(df['Hometown'] == 'Visayas')` with `(df['Gender'] == 'Female')`. The column projection isolates `['Name', 'Track', 'GEAS', 'Electronics', 'Average']`, saving the resulting rows into VisFemale. 

```python
VisFemale = (VisFemale[VisFemale['Average'] >= 60])
VisFemale
```
 

## C. CATEGORY-AVERAGE VISUALIZATION
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

```python
track_mean = df.groupby('Track')['Average'].mean().reset_index()
track_mean
```

```python
gender_mean = df.groupby('Gender')['Average'].mean().reset_index()
gender_mean
```

```python
hometown_mean = df.groupby('Hometown')['Average'].mean().reset_index()
hometown_mean
```

```python
plt.figure(figsize=(20, 4))

plt.subplot(1, 3, 1)
plt.bar(track_mean['Track'], track_mean['Average'])
plt.title('Average by Track')
plt.xlabel('Track')
plt.ylabel('Average Score')

plt.subplot(1, 3, 2)
plt.bar(gender_mean['Gender'], gender_mean['Average'])
plt.title('Average by Gender')
plt.xlabel('Gender')
plt.ylabel('Average Score')

plt.subplot(1, 3, 3)
plt.bar(hometown_mean['Hometown'], hometown_mean['Average'])
plt.title('Average by Hometown')
plt.xlabel('Hometown')
plt.ylabel('Average Score')

plt.show()
```

Thank you for reading!

To see the main Python program for Programming Assignment 4, click this  and download. Open on Jupyter Notebook, then run all cells. 

**READ ME file Version History:**

*September 11, 2026 - Initial README file started.

*September 17, 2025 - 






