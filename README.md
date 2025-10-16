# TASK-1-EXPLORATORY-DATA-ANALYSIS-EDA-ON-RETAIL-DATASET
import pandas as pd import numpy as np import matplotlib.pyplot as plt #visualizing data %matplotlib inline import seaborn as sns

df = pd.read_excel('Retail Sales Analysis_utf.xlsx') df.shape df.head()

df.info

df.info df.dropna(inplace=True) df.shape

ax=sns.countplot(x='gender',data=df) for bars in ax.containers: ax.bar_label(bars)

df.groupby(['gender'], as_index=False)['total_sale'].sum().sort_values(by='total_sale',ascending=False)

# Total sale by gender
sns.barplot(x='gender', y='total_sale', data=df.groupby('gender', as_index=False)['total_sale'].sum()) plt.title('Total Sales by Gender') plt.show()

From the above graph, we can see most of the buyers are females

# Total sale by age
df['age_group'] = pd.cut(df['age'], bins=range(10, 80, 10), labels=['10-19','20-29','30-39','40-49','50-59','60-69']) sns.barplot(x='age_group', y='total_sale', data=df.groupby('age_group', as_index=False)['total_sale'].sum()) plt.title('Total Sales by Age Group') plt.show()

50-59 age group is most active in purchases.

# Total sale by category
sns.barplot(x='category', y='total_sale', data=df.groupby('category', as_index=False)['total_sale'].sum().sort_values(by='total_sale', ascending=False)) plt.title('Total Sales by Category') plt.xticks(rotation=45) plt.show()

Electronics and Clothing product types sell the most frequently.

# Top Customers
top_customers = df.groupby('customer_id', as_index=False)['total_sale'].sum().sort_values(by='total_sale', ascending=False).head(10) sns.barplot(x='customer_id', y='total_sale', data=top_customers) plt.title('Top 10 Customers by Sales') plt.xticks(rotation=45) plt.show()

#Customer_id 3 is the top customer by sales
