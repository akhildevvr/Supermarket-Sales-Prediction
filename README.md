# Supermarket Sales Prediction

## *Problem Statement*

The data scientists at BigMart have collected sales data for 1559 products across 10 stores in different cities for the year 2013. Now each product has certain attributes that sets it apart from other products. Same is the case with each store.

The aim is to build a predictive model to find out the sales of each product at a particular store so that it would help the decision makers at BigMart to find out the properties of any product or store, which play a key role in increasing the overall sales.

## *Hypothesis Generation*

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


## *EDA

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

![Violin Plot 2](https://user-images.githubusercontent.com/48282246/68240573-1677ae00-0005-11ea-9b18-f0fc10788493.jpeg)

The distribution of ‘Small’ Outlet_Size is almost identical to the distribution of the blank category (first vioin) of Outlet_Size. So, we can substitute the blanks in Outlet_Size with ‘Small’.

Please note that this is not the only way to impute missing values, but for the time being we will go ahead and impute the missing values with ‘Small’.

Let’s examine the remaining variables.

![Violin Plot 3](https://user-images.githubusercontent.com/48282246/68240595-1f687f80-0005-11ea-83f8-f0c5738d2beb.jpeg)

1. Tier 1 and Tier 3 locations of Outlet_Location_Type look similar.
2. In the Outlet_Type plot, Grocery Store has most of its data points around the lower sales values as compared to the other categories.

## *Missing Value Treatment

Missing data can have a severe impact on building predictive models because the missing values might be contain some vital information which could help in making better predictions. So, it becomes imperative to carry out missing data imputation. There are different methods to treat missing values based on the problem and the data. Some of the common techniques are as follows:

1. Deletion of rows: In train dataset, observations having missing values in any variable are deleted. The downside of this method is the loss of information and drop in prediction power of model.

2. Mean/Median/Mode Imputation: In case of continuous variable, missing values can be replaced with mean or median of all known values of that variable. For categorical variables, we can use mode of the given values to replace the missing values.

3. Building Prediction Model: We can even make a predictive model to impute missing data in a variable. Here we will treat the variable having missing data as the target variable and the other variables as predictors. We will divide our data into 2 datasets—one without any missing value for that variable and the other with missing values for that variable. The former set would be used as training set to build the predictive model and it would then be applied to the latter set to predict the missing values.

## *Feature Engineering

Most of the times, the given features in a dataset are not sufficient to give satisfactory predictions. In such cases, we have to create new features which might help in improving the model’s performance. Let’s try to create some new features for our dataset.

In this section we will create the following new features:

1.Item_Type_new: Broader categories for the variable Item_Type.
2.Item_category: Categorical variable derived from Item_Identifier.
3.Outlet_Years: Years of operation for outlets.
4.price_per_unit_wt: Item_MRP/Item_Weight
5.Item_MRP_clusters: Binned feature for Item_MRP.

### Encoding Categorical Variables

Most of the machine learning algorithms produce better result with numerical variables only. So, it is essential to treat the categorical variables present in the data. One thing that can be done is to completely remove the categorical variables, but that would lead to enormous loss of information. Fortunately we have smarter techniques to deal with the categorical variables.

In this stage, we will convert our categorical variables into numerical ones. We will use 2 techniques — Label Encoding and One Hot Encoding.

Label encoding simply means converting each category in a variable to a number. It is more suitable for ordinal variables — categorical variables with some order.

In One hot encoding, each category of a categorical variable is converted into a new binary column (1/0).

#### Label encoding for the categorical variables
We will label encode Outlet_Size and Outlet_Location_Type as these are ordinal variables.

## *PreProcessing Data

In simple words, pre-processing refers to the transformations applied to your data before feeding it to the algorithm. It invloves further cleaning of data, data transformation, data scaling and many more things.

For our data, we will deal with the skewness and scale the numerical variables

### Removing Skewness

Skewness in variables is undesirable for predictive modeling. Some machine learning methods assume normally distributed data and a skewed variable can be transformed by taking its log, square root, or cube root so as to make its distribution as close to normal distribution as possible. In our data, variables Item_Visibility and price_per_unit_wt are highly skewed. So, we will treat their skewness with the help of log transformation.

### Scaling numeric predictors

Let’s scale and center the numeric variables to make them have a mean of zero, standard deviation of one and scale of 0 to 1. Scaling and centering is required for linear regression models.

### Correlated Variables

Let’s examine the correlated features of train dataset. Correlation varies from -1 to 1.

negative correlation: < 0 and >= -1
positive correlation: > 0 and <= 1
no correlation: 0
It is not desirable to have correlated features if we are using linear regressions.

![Corr Plot 2](https://user-images.githubusercontent.com/48282246/68240687-44f58900-0005-11ea-9b81-ae3ddb0fe464.jpeg)

The correlation plot above shows correlation between all the possible pairs of variables in out data. The correlation between any two variables is represented by a pie. A blueish pie indicates positive correlation and reddish pie indicates negative correlation. The magnitude of the correlation is denoted by the area covered by the pie.

Variables price_per_unit_wt and Item_Weight are highly correlated as the former one was created from the latter. Similarly price_per_unit_wt and Item_MRP are highly correlated for the same reason.

## *Model Building

Finally we have arrived at most interesting stage of the whole process — predictive modeling. We will start off with the simpler models and gradually move on to more sophisticated models. We will start with the simpler linear models and then move over to more complex models like RandomForest and XGBoost.

We will build the following models in the next sections.

Linear Regression
Lasso Regression
Ridge Regression
RandomForest
XGBoost
Evaluation Metrics for Regression
The process of model building is not complete without evaluation of model’s performance. That’s why we need an evaluation metric to evaluate our model. Since this is a regression problem, we can evaluate our models using any one of the following evaluation metrics:

1.Mean Absolute Error (MAE) is the mean of the absolute value of the errors.
2.Mean Squared Error (MSE) is the mean of the squared errors.
3.Root Mean Squared Error (RMSE) is the square root of the mean of the squared errors.

 ### Linear Regression

Let’s build our linear regression model with all the variables. We will use 5-fold cross validationin all the models we are going to build. Basically cross vaidation gives an idea as to how well a model generalizes to unseen data.

 ### Regularised Linear Regression

Regularised regression models can handle the correlated independent variables well and helps in overcoming overfitting. Ridge penalty shrinks the coefficients of correlated predictors towards each other, while the Lasso tends to pick one of a pair of correlated features and discard the other. The tuning parameter lambda controls the strength of the penalty.

 ### Random Forest

We will now build a RandomForest model with 400 trees. The other tuning parameters used here are mtry — no. of predictor variables randomly sampled at each split, and min.node.size — minimum size of terminal nodes (setting this number large causes smaller trees and reduces overfitting).

 #### Best Model Parameters

![RF Plot](https://user-images.githubusercontent.com/48282246/68240737-55a5ff00-0005-11ea-9f1c-d6d9e689c18d.jpeg)
As per the plot shown above, the best score is achieved at mtry = 5 and min.node.size = 20.


### XGBoost

We are going to use the xgb.cv() function for cross validation. This function comes with the xgboost package itself. Here we are using cross validation for finding the optimal value of nrounds.

 #### Variable Importance

Let’s plot feature importance based on the RandomForest model

![XGB Plot](https://user-images.githubusercontent.com/48282246/68240767-60609400-0005-11ea-9705-88320b866f97.jpeg)

As expected Item_MRP is the most important variable in predicting the target variable. New features created by us, like price_per_unit_wt, Outlet_Years, Item_MRP_Clusters, are also among the top most important variables. This is why feature engineering plays such a crucial role in predictive modeling.


