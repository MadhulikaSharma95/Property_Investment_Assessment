I. INTRODUCTION
---------------
Real Estate market is extremely dynamic. The prices of real estate properties are heavily dependent on economic factors such as inflation. Real estate prices are an important economic indicator, and price ranges are of significant importance to both buyers and sellers. In this project, prices of a property will be forecasted using explanatory factors that encompass a wide range of residential dwelling characteristics. The purpose of this project is to develop a regression model that can reliably predict the price of a property based on its attributes.

II. PROBLEM STATEMENT
---------------------
The focus of this project is to predict the investment value of a property based on features such as district, living area space etc. Since the investment value is a numeric property, this project is a regression problem.

III. DATASET DESCRIPTION
------------------------
The dataset for this project was collection from the City of Buffalo data sources. The dataset has 93653 data points with 85 features.

IV. DATASET PREPROCESSING
-------------------------
Data Source is from goverment website: https://data.buffalony.gov/Government/Current-2021-2022-Assessment-Roll/4t8s-9yih
In the 93653 data points, there is a major chunk of missing values in the dataset. The process of solving the missing values issue is split into three parts :

● For the columns with missing values in more than 80% of the rows: There are 11 columns with missing values in more than 72000 rows. Imputing with the null values would induce a bias in the data. The corresponding columns were dropped to solve the null values issue in this part. The dataset now has 73 features and 93653 rows.
● For the columns with missing values in less than 20% of the rows: There are approximately 5000 unique rows with columns having missing values in less than 20% of the rows. Dropping these rows will not affect the data as this is a small fraction compared to the entire dataset. So the dataset is now reduced to 73 features and 89457 rows.
● For the other columns: The missing values were imputed using the statistical values of the corresponding columns. For numerical columns, the null values were replaced with the median of the column. The median was chosen because imputing with mean would introduce a new value that’s not present in the dataset. Also, mean would result in a decimal value which might not be suitable for all data types. For categorical columns, the null values were replaced with the most frequently occurred value, i.e. mode of the column.

VI. DATA MODELLING
------------------
After treating the missing values, the dataset now has 73 features, which is a huge dimension to build a regression model. The features which make the most impact mathematically and theoretically are selected. The Pearson Correlation for every feature with the response variable is computed to analyze the extent of impact of the feature on the response variable.
Before moving to modeling, we remove a few outliers in the dataset to improve the accuracy. We noticed that a few properties have a total value greater than 9 million, so we drop the rows with such total value as they constitute a noise in the dataset.
     
●  Multiple Linear Regression
Multiple linear regression is an extension of simple linear regression used to predict an outcome variable (y) on the basis of multiple distinct predictor variables (x). After using this model, we have a R2 score of 69%.

●  Lasso Regression
Lasso regression is a method we can use to fit a regression model when multicollinearity is present in the data.In a nutshell, least squares regression tries to find coefficient estimates that minimize the sum of squared residuals. The lasso model gives us a R2 score of 0.688 which is less than the score from the previous model.

●  Ridge Regression
Ridge regression is an extension of linear regression where the loss function is modified to minimize the complexity of the model. The result of the Ridge regression is very similar to those of linear and lasso regression. The R2 score is 69%.

●  Random Forest Regression
Random Forest Regression is a supervised learning algorithm that uses ensemble learning methods for regression. It is a technique that combines predictions from multiple machine learning algorithms to make a more accurate prediction than a single model. We performed a random forest regression with 50 trees. It comes out as our best model by achieving 88% accuracy.

VIII. CONCLUSION
-----------------
In this project we used the city of buffalo property assessment data to perform various statistical learning. We first cleaned the dataset removing a few thousand columns. We performed multiple EDAs to understand the data to be able to suggest to any investors where to find any type of properties in the city, and most importantly how much they should expect to spend based on their chosen neighborhood, area, and their needs. Our best model predicts the value of a property with 89% accuracy.
