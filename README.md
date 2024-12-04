# ICT Data Analysis

This repository contains a Jupyter notebook for analyzing a dataset related to the integration of Information and Communication Technology (ICT) in teaching. The dataset includes various factors influencing ICT usage in education, including the perception of effectiveness, infrastructure, and teacher engagement with technology.

## Project Overview

This notebook provides the following steps:

1. **Data Import and Exploration**:
   - Import necessary libraries (Pandas, NumPy, Matplotlib, Seaborn).
   - Load the dataset from a CSV file (`ict.csv`).
   - Perform basic data exploration, including viewing the first few rows of the dataset, checking for missing values, and examining data types.

2. **Data Cleaning**:
   - Handle missing values by removing rows with NaN values.
   - Drop unnecessary columns (e.g., `Timestamp`).
   
3. **Data Transformation**:
   - Convert categorical variables (like survey responses) into numerical values using a replacement dictionary.
   - Perform type conversion for relevant columns to ensure appropriate data types (e.g., integer, float).

4. **Statistical Analysis**:
   - Calculate the mean, standard deviation, and median of all relevant columns.
   - Perform correlation analysis to understand relationships between different factors.

5. **Visualization**:
   - Visualizations (using Matplotlib and Seaborn) can be added here for further analysis, such as plotting the distribution of various columns or creating heatmaps of correlations.

## Prerequisites

Make sure you have the following Python libraries installed:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

You can install them using pip:

```
pip install pandas numpy matplotlib seaborn
```

## Data Description

The dataset consists of 200 rows and 22 columns, with each row representing a survey response from an individual (such as a student, teacher, or professional) regarding their views on ICT in education. Some of the columns include:

- **Age**: The age group of the respondent.
- **Occupation**: The occupation of the respondent (e.g., student, teacher, professional).
- **Gender**: The gender of the respondent.
- **Education Status**: The education level of the respondent.
- Several columns representing the respondent's opinion on various aspects of ICT in education, such as the effectiveness of technology-supported teaching, the impact of technology on student interest, and the availability of resources.

## Steps and Analysis

### 1. Data Import and Initial Exploration

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Reading the Dataset
df = pd.read_csv('ict.csv')

# Viewing the first few rows
df.head()
```

### 2. Data Cleaning

Checking for missing values and handling them:

```python
# Checking for missing values
df.isnull().sum()

# Dropping rows with missing values
df.dropna(inplace=True)

# Dropping unnecessary columns (Timestamp)
df.drop('Timestamp', axis=1, inplace=True)
```

### 3. Data Transformation

Replacing categorical text data with numeric values:

```python
replacer = {'Strongly disagree': 1, 'Disagree': 2, 'Neither agree nor disagree': 3, 'Agree': 4, 'Strongly agree': 5}
cols = df.columns[df.dtypes == 'object']
df[cols] = df[cols].replace(replacer)
```

### 4. Statistical Analysis

Summary statistics:

```python
# Mean and Standard Deviation
df.describe()

# Median of all factors
df.median()

# Correlation Analysis
corr = df.corr()
```

### 5. Visualization (Optional)

You can add visualizations here using `matplotlib` or `seaborn` to explore the dataset further:

```python
# Heatmap for correlation matrix
plt.figure(figsize=(10, 8))
sns.heatmap(corr, annot=True, cmap="coolwarm", fmt=".2f")
plt.title('Correlation Heatmap')
plt.show()
```

## Conclusion

This analysis provides insights into how different factors are related to the use of ICT in education. The dataset shows the perceptions of different individuals (such as students and professionals) on various aspects of technology integration in teaching. Correlation analysis and descriptive statistics can help to understand the relationships between these factors and guide decision-making for better implementation of ICT in educational environments.
