# # Exp 6 Analysis and Visualization of COVID-19 Dataset using Python

**Date:27/08/2026**

## AIM:

To analyse a large real-world COVID-19 dataset using Python and visualize key trends and relationships using multiple types of graphs for meaningful insights.

## DESIGN STEPS:

### Step 1:

Clone the repository from GitHub.

### Step 2:

Create a Python project in the preferred IDE (VS Code/PyCharm/Jupyter Notebook).

### Step 3:

Create the Python program for analysing and visualizing the COVID-19 dataset using **Pandas** and **Matplotlib** libraries.

### Step 4:

Load the **`covid_cases.csv`** dataset using Pandas and explore the dataset by displaying its shape and column names.

### Step 5:

Check and handle missing values in the dataset, if any.

### Step 6:

Perform basic data exploration by finding the total number of records and generating the statistical summary using the `describe()` function.

### Step 7:

Use Matplotlib to create different visualizations:

* **Line Graph:** Trend of confirmed cases over time globally.
* **Bar Chart:** Top 10 countries by total confirmed cases.
* **Pie Chart:** Case distribution of the top 5 affected countries.
* **Scatter Plot:** Relationship between confirmed cases and deaths.
* **Histogram:** Distribution of active cases.

### Step 8:

Add appropriate titles, axis labels, legends, and other necessary labels to the graphs.

### Step 9:

Execute the program and analyze the generated visualizations to identify meaningful trends and relationships in the COVID-19 dataset.

## PROGRAM:
~~~
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
data = pd.read_csv("covid_case.csv")

# Display basic information
print("First 5 rows:")
print(data.head())

print("\nDataset Shape:")
print(data.shape)

print("\nColumn Names:")
print(data.columns)

# Check missing values
print("\nMissing Values:")
print(data.isnull().sum())

# Remove missing values
data = data.dropna()

# Convert Date column to datetime
data['Date'] = pd.to_datetime(data['Date'])

# Total number of records
print("\nTotal Records:", len(data))

# Statistical summary
print("\nStatistical Summary:")
print(data.describe())

# Line Graph: Global confirmed cases over time
global_cases = data.groupby('Date')['Confirmed'].sum()

plt.figure()
plt.plot(global_cases.index, global_cases.values)
plt.title("Global Confirmed COVID-19 Cases Over Time")
plt.xlabel("Date")
plt.ylabel("Confirmed Cases")
plt.show()

# Bar Chart: Top 10 countries by confirmed cases
top10 = data.groupby('Country')['Confirmed'].sum().sort_values(ascending=False).head(10)

plt.figure()
top10.plot(kind='bar')
plt.title("Top 10 Countries by Confirmed Cases")
plt.xlabel("Country")
plt.ylabel("Confirmed Cases")
plt.show()

# Pie Chart: Top 5 affected countries
top5 = data.groupby('Country')['Confirmed'].sum().sort_values(ascending=False).head(5)

plt.figure()
plt.pie(top5, labels=top5.index, autopct='%1.1f%%')
plt.title("Top 5 Countries Case Distribution")
plt.show()

# Scatter Plot: Confirmed vs Deaths
plt.figure()
plt.scatter(data['Confirmed'], data['Deaths'])
plt.title("Confirmed Cases vs Deaths")
plt.xlabel("Confirmed Cases")
plt.ylabel("Deaths")
plt.show()

# Histogram: Distribution of active cases
plt.figure()
plt.hist(data['Active'], bins=20)
plt.title("Distribution of Active Cases")
plt.xlabel("Active Cases")
plt.ylabel("Frequency")
plt.show()
~~~

## OUTPUT:

*(Paste the execution output showing the dataset information, statistical summary, and generated Line Graph, Bar Chart, Pie Chart, Scatter Plot, and Histogram.)*
<img width="688" height="707" alt="image" src="https://github.com/user-attachments/assets/0d321afa-f466-4628-ace6-8dac31e93609" />
<img width="700" height="547" alt="image" src="https://github.com/user-attachments/assets/4b28e7eb-c705-4aea-9796-f1bcfbcc3573" />
<img width="677" height="602" alt="image" src="https://github.com/user-attachments/assets/be39fcc6-2f46-4729-a400-2bf4dbe0ed20" />
<img width="512" height="487" alt="image" src="https://github.com/user-attachments/assets/4c4e2c30-0d1f-44a7-bed7-7c58bd1a139f" />
<img width="717" height="546" alt="image" src="https://github.com/user-attachments/assets/9fc0b976-8cec-491e-b44e-8545c233f38c" />
<img width="697" height="552" alt="image" src="https://github.com/user-attachments/assets/da03e895-f19f-44d8-9010-7bf4c9afb618" />

## RESULT:

The COVID-19 dataset was successfully analysed using Python. The dataset was explored using Pandas, and meaningful trends and relationships were visualized using different types of graphs such as line graph, bar chart, pie chart, scatter plot, and histogram using Matplotlib.
