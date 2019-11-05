# Supermarket Sales Prediction

## *1.Problem Statement*

The data scientists at BigMart have collected sales data for 1559 products across 10 stores in different cities for the year 2013. Now each product has certain attributes that sets it apart from other products. Same is the case with each store.

The aim is to build a predictive model to find out the sales of each product at a particular store so that it would help the decision makers at BigMart to find out the properties of any product or store, which play a key role in increasing the overall sales.

## *2. Hypothesis Generation*

It involves understanding the problem in detail by brainstorming as many factors as possible which can impact the outcome. It is done by understanding the problem statement thoroughly and before looking at the data.

We can start the process by working on four levels: Store Level, Product Level, Customer Level and Macro Level.

### 1.Store Level Hypotheses
City type: Stores located in urban or Tier 1 cities should have higher sales because of the higher income levels of people there.

Population Density: Stores located in densely populated areas should have higher sales because of more demand. Store Capacity: Stores which are very big in size should have higher sales as they act like one-stop-shops and people would prefer getting everything from one place

Competitors: Stores having similar establishments nearby should have less sales because of more competition.

Marketing: Stores which have a good marketing division should have higher sales as it will be able to attract customers through the right offers and advertising.

Location: Stores located within popular marketplaces should have higher sales because of better access to customers.

Ambiance: Stores which are well-maintained and managed by polite and humble people are expected to have higher footfall and thus higher sales.

### 2.Product Level Hypotheses
Brand: Branded products should have higher sales because of higher trust in the customer.

Packaging: Products with good packaging can attract customers and sell more.

Utility: Daily use products should have a higher tendency to sell as compared to the specific use products.

Display Area: Products which are given bigger shelves in the store are likely to catch attention first and sell more. Visibility in Store: The location of product in a store will impact sales. Ones which are right at entrance will catch the eye of customer first rather than the ones in back.

Advertising: Better advertising of products in the store will should higher sales in most cases. Promotional Offers: Products accompanied with attractive offers and discounts will sell more.

### 3.Customer Level Hypotheses
Customer Behavior: Stores keeping the right set of products to meet the local needs of customers will have higher sales.

Job Profile: Customer working at executive levels would have higher chances of purchasing high amount products as compared to customers working at entry or mid senior level.

Family Size: More the number of family members, more amount will be spent by a customer to buy products

Annual Income: Higher the annual income of a customer, customer is more likely to buy high cost products. Past Purchase History: Availablity of this information can help us to determine the frequency of a product being purchased by a user.

### 4.Macro Level Hypotheses
Environment: If the environment is declared safe by government, customer would be more likely to purchase products without worrying if it’s environment friendly or not.

Economic Growth: If the current economy shows a consistent growth, per capita income will rise, therefore buying power of customers will increase.


## EDA

### Target Variable

Since our target variable is continuous, we can visualise it by plotting its histogram.

![1549263564109](https://user-images.githubusercontent.com/48282246/68144702-23749e80-ff2c-11e9-99e6-4e037128ebf3.png)

As you can see, it is a right skewd variable and would need some data transformation to treat its skewness.

### Independent Variables (numeric variables)

Now let’s check the numeric independent variables. We’ll again use the histograms for visualizations because that will help us in visualizing the distribution of the variables.
![Grid Plot](https://user-images.githubusercontent.com/48282246/68162276-993e3180-ff4f-11e9-815a-fbba3470533c.jpeg)

1.There seems to be no clear-cut pattern in Item_Weight.
2.Item_Visibility is right-skewed and should be transformed to curb its skewness.
3.We can clearly see 4 different distributions for Item_MRP. It is an interesting insight.

### Independent Variables (categorical variables)
Now we’ll try to explore and gain some insights from the categorical variables. A categorical variable or feature can have only a finite set of values. Let’s first plot Item_Fat_Content.

![Fat Content](https://user-images.githubusercontent.com/48282246/68162514-149fe300-ff50-11e9-89b2-83749e629ea6.jpeg)

Let us check other categorical variables.

![Cat Plot Grid](https://user-images.githubusercontent.com/48282246/68240457-da444d80-0004-11ea-8e84-35953937ba5d.jpeg)

In Outlet_Size’s plot, for 4016 observations, Outlet_Size is blank or missing.We will check for this in the bivariate analysis to substitute the missing values in the Outlet_Size.

We’ll also check the remaining categorical variables.

![Plot Grid](https://user-images.githubusercontent.com/48282246/68240472-e4fee280-0004-11ea-8fb1-37f421995e12.jpeg)

1. Lesser number of observations in the data for the outlets established in the year 1998 as compared to the other years.
2. Supermarket Type 1 seems to be the most popular category of Outlet_Type.

After looking at every feature individually, let’s now do some bivariate analysis. Here we’ll explore the independent variables with respect to the target variable. The objective is to discover hidden relationships between the independent variable and the target variable and use those findings in missing data imputation and feature engineering in the next module.

We will make use of scatter plots for the continuous or numeric variables and violin plots for the categorical variables.

### Target Variable vs Independent Numerical Variables

Let’s explore the numerical variables first.

![Corr Plot](https://user-images.githubusercontent.com/48282246/68240513-fba53980-0004-11ea-862c-0ab403b4bc5f.jpeg)

1. Item_Outlet_Sales is spread well across the entire range of the Item_Weight without any obvious pattern.
2. In Item_Visibility vs Item_Outlet_Sales, there is a string of points at Item_Visibility = 0.0 which seems strange as item visibility cannot be completely zero. We will take note of this issue and deal with it in the later stages.
3. In the third plot of Item_MRP vs Item_Outlet_Sales, we can clearly see 4 segments of prices that can be used in feature engineering to create a new variable.

### Target Variable vs Independent Categorical Variables

Now we’ll visualise the categorical variables with respect to Item_Outlet_Sales. We will try to check the distribution of the target variable across all the categories of each of the categorical variable.

We could have used boxplots here, but instead we’ll use the violin plots as they show the full distribution of the data. The width of a violin plot at a particular level indicates the concentration or density of data at that level. The height of a violin tells us about the range of the target variable values.

![Violin Plot 1](https://user-images.githubusercontent.com/48282246/68240540-0b248280-0005-11ea-96c3-12ab7b43e1a3.jpeg)

1. Distribution of Item_Outlet_Sales across the categories of Item_Type is not very distinct and same is the case with Item_Fat_Content.
2. The distribution for OUT010 and OUT019 categories of Outlet_Identifier are quite similar and very much different from the rest of the categories of Outlet_Identifier.

In the univariate analysis, we came to know about the empty values in Outlet_Size variable. Let’s check the distribution of the target variable across Outlet_Size.


