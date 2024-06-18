Diwali Sales Analysis
Introduction
This project involves analyzing the Diwali Sales dataset to gain insights into customer behavior and purchasing patterns. The analysis covers various aspects such as gender, age group, state, marital status, occupation, and product categories.

Dataset
The dataset used for this analysis is Diwali Sales Data.csv. It contains the following columns:

User_ID: Unique ID for each customer
Cust_name: Customer name
Product_ID: Unique ID for each product
Gender: Gender of the customer
Age Group: Age group of the customer
Age: Age of the customer
Marital_Status: Marital status of the customer
State: State where the customer is located
Zone: Zone where the customer is located
Occupation: Occupation of the customer
Product_Category: Category of the product
Orders: Number of orders placed
Amount: Total amount spent
Status: Unused column
unnamed1: Unused column
Setup
Clone the repository:

bash
Copy code
git clone <repository-url>
Install the necessary libraries:

Copy code
pip install numpy pandas matplotlib seaborn
Download the dataset:
Ensure that the Diwali Sales Data.csv file is placed in the appropriate directory.

Data Cleaning and Preparation
Import libraries:

python
Copy code
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
Load the dataset:

python
Copy code
df = pd.read_csv("C:/Users/SP/Downloads/Python_Diwali_Sales_Analysis-main/Python_Diwali_Sales_Analysis-main/Diwali Sales Data.csv", encoding='unicode_escape')
Check the shape of the dataset:

python
Copy code
df.shape
Preview the dataset:

python
Copy code
df.head()
Check for null values and data types:

python
Copy code
df.info()
Drop unrelated columns and handle null values:

python
Copy code
df.drop(['Status', 'unnamed1'], axis=1, inplace=True)
df.dropna(inplace=True)
df['Amount'] = df['Amount'].astype('int')
Exploratory Data Analysis (EDA)
Gender Analysis
Plotting a bar chart for Gender:

python
Copy code
ax = sns.countplot(x='Gender', data=df)
for bars in ax.containers:
    ax.bar_label(bars)
plt.show()
Total amount by Gender:

python
Copy code
sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='Gender', y='Amount', data=sales_gen)
plt.show()
Age Group Analysis
Plotting a bar chart for Age Group and Gender:

python
Copy code
ax = sns.countplot(data=df, x='Age Group', hue='Gender')
for bars in ax.containers:
    ax.bar_label(bars)
plt.show()
Total Amount vs Age Group:

python
Copy code
sales_age = df.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='Age Group', y='Amount', data=sales_age)
plt.show()
State Analysis
Total number of orders from top 10 states:

python
Copy code
sales_state = df.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)
sns.set(rc={'figure.figsize': (16, 5)})
sns.barplot(data=sales_state, x='State', y='Orders')
plt.show()
Total amount/sales from top 10 states:

python
Copy code
sales_state = df.groupby(['State'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)
sns.set(rc={'figure.figsize': (16, 5)})
sns.barplot(data=sales_state, x='State', y='Amount')
plt.show()
Marital Status Analysis
Plotting a bar chart for Marital Status:

python
Copy code
ax = sns.countplot(data=df, x='Marital_Status')
sns.set(rc={'figure.figsize': (7, 5)})
for bars in ax.containers:
    ax.bar_label(bars)
plt.show()
Total amount by Marital Status and Gender:

python
Copy code
sales_state = df.groupby(['Marital_Status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.set(rc={'figure.figsize': (6, 5)})
sns.barplot(data=sales_state, x='Marital_Status', y='Amount', hue='Gender')
plt.show()
Occupation Analysis
Plotting a bar chart for Occupation:

python
Copy code
sns.set(rc={'figure.figsize': (20, 5)})
ax = sns.countplot(data=df, x='Occupation')
for bars in ax.containers:
    ax.bar_label(bars)
plt.show()
Total amount by Occupation:

python
Copy code
sales_state = df.groupby(['Occupation'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.set(rc={'figure.figsize': (20, 5)})
sns.barplot(data=sales_state, x='Occupation', y='Amount')
plt.show()
Product Category Analysis
Plotting a bar chart for Product Category:

python
Copy code
sns.set(rc={'figure.figsize': (20, 5)})
ax = sns.countplot(data=df, x='Product_Category')
for bars in ax.containers:
    ax.bar_label(bars)
plt.show()
Total amount by Product Category:

python
Copy code
sales_state = df.groupby(['Product_Category'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)
sns.set(rc={'figure.figsize': (20, 5)})
sns.barplot(data=sales_state, x='Product_Category', y='Amount')
plt.show()
Product ID Analysis
Total number of orders by Product ID:

python
Copy code
sales_state = df.groupby(['Product_ID'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)
sns.set(rc={'figure.figsize': (20, 5)})
sns.barplot(data=sales_state, x='Product_ID', y='Orders')
plt.show()
Top 10 most sold products:

python
Copy code
fig1, ax1 = plt.subplots(figsize=(12, 7))
df.groupby('Product_ID')['Orders'].sum().nlargest(10).sort_values(ascending=False).plot(kind='bar', ax=ax1)
plt.show()
Conclusion
From the analysis, the following insights were gathered:

Most buyers are females, and their purchasing power is greater than males.
The majority of buyers are from the age group 26-35 years.
Most orders and sales are from Uttar Pradesh, Maharashtra, and Karnataka.
Married women are the largest group of buyers.
The top occupations of buyers are in IT, Healthcare, and Aviation.
The most sold products are from the Food, Clothing, and Electronics categories.
Future Work
Further analysis can be conducted to:

Examine seasonal trends in sales.
Perform a detailed product-level analysis to identify bestsellers.
Explore customer segmentation for targeted marketing.
Acknowledgements
Thank you to the contributors of the Diwali Sales Data for providing the dataset and inspiration for this project.
