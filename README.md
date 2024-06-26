In a Given Project, we identify that in which sector copnay needs tofocus, which state company getting more orders and on the basis of that what steps company should take so that it helps to expand growth of the company. 
we find outcome with the help of python.


                                          superstore Data Analytics

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = pd.read_excel(r'C:\Users\ibtis\Downloads\superstore\sample.xlsx')

df.head()

df.info()

# to check null values

df.isnull().sum()

# we found that in product base margin column, it has 72 null values. Best option is we can average it on  the basic of mean

df['Product Base Margin'].fillna(df['Product Base Margin'].mean(), inplace =True)

df.isnull().sum()

df.head(5)

df.shape

# Identifying Order Priority



df['Order Priority'].value_counts()

# while using count option for order priority we found that critical has depicted twice so we need to rectify this error##

df['Order Priority'].unique()

df['Order Priority'].replace('Critical ','Critical', inplace = True)

df['Order Priority'].unique()



plt.figure(figsize = (5,5))
plt.title(' Priority Order')
plt.savefig('Priority Order.jpg')
sns.countplot(x = 'Order Priority', data = df)
plt.show()

# ship mode

x = df['Ship Mode'].value_counts().index

y = df['Ship Mode'].value_counts().values

plt.pie(y, labels = x, autopct = '%0.2f%%')
plt.title('ship mode')
plt.savefig('Ship Mode.jpg')
plt.show()

# in the given pie chart, it clearly stated that ship mode in Regular Air  is highest as compare to Express and Delivery Truck 

# ship mode with product category

df['Product Category'].value_counts()

sns.countplot(x = 'Product Category', data  = df, hue = 'Ship Mode')
plt.title('Product category with ship mode')
plt.savefig('Product category with ship mode.jpg')
plt.show()

# In column bar chart, it clearly mention that Regular Air ship mode is highest in all product category

# customer segment

df['Customer Segment'].value_counts()

sns.countplot(x = 'Customer Segment', data = df)
plt.show()

# in the aove bar chart, it clearly depicted that corporate buy more goods as compare to small business and consumer

# product category with product sub category

df['Product Sub-Category'].value_counts()

Office Supplies, Product Category

plt.figure(figsize = (10,5))
sns.countplot(x = 'Product Category', data = df[df['Product Category']=='Office Supplies'], hue = 'Product Sub-Category')
plt.title('Office supplies in Product sub category')

plt.show()

#  in Office supplies, usage of paper is more

plt.figure(figsize = (5,5))
sns.countplot(x = 'Product Category',data =df [df['Product Category']=='Technology'], hue = 'Product Sub-Category')
plt.title('Technology with product sub category ')

# iN TECHNOLOGY, Telephone and communication is highest



df['Product Category'].value_counts()



plt.figure(figsize = (5,5))
sns.countplot(x = 'Product Category', data = df[df['Product Category']=='Furniture'], hue = 'Product Sub-Category')
plt.title('Furniture with product sub category')

# In furniture, Office furnishing is in top 

#    order date with orders

df.info()

df['Order Year'] = df['Order Date'].dt.year
df.info()

df['Order Year'].value_counts()

sns.countplot(x = 'Order Year', data = df)
plt.title('Order Year')
plt.show()

# In the below chart it depicted that, year by year , order of the company increasing

#product category with profit

sns.barplot(x = 'Product Category', y = 'Profit', data = df, estimator = 'sum')
plt.title('Product category : Profit')



sns.barplot(x = 'Product Category', y = 'Product Base Margin', data = df, estimator = 'sum')

# product base margin and product category: while comparing two chart it depicted that inspite of lower margin in technology,company earn more in Technology






# Company earning highest profit in Technology category

plt.figure(figsize = (10,10))
sns.barplot(x = 'Customer Segment', y = 'Profit', data = df, estimator = 'sum')

#  state with order

df['State or Province'].value_counts()[:5]

# It says that california is top state which buying more products in company.









