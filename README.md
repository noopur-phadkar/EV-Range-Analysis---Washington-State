# Use-of-Electric-Vehicles-in-Washington-State

This study analyzes the adoption and usage of electric vehicles in Washington State and develops a predictive model to estimate the electric range of an electric vehicle based on its attributes. The findings suggest that battery capacity and vehicle type are among the most important factors influencing the electric range of an electric vehicle. The goal of this project is to create a predictive model that can accurately estimate the electric range of electric vehicles based on various attributes is the objective of this project. By achieving this, we can tackle the issue of limited electric range, which could potentially increase the adoption of electric vehicles.

# Dataset

## Name: Electric Vehicle Population Data [Washington US]

Dataset Source: Kaggle

The dataset pertains to the electric vehicle population in Washington, US, and provides details regarding the electric range, battery capacity, make, model, year, and other attributes of the EVs. The information was gathered by the Washington State Department of Transportation and the Department of Ecology as part of their initiatives to promote the adoption of electric vehicles and minimize greenhouse gas emissions resulting from the transportation sector.

<!---
Dataset Description:
VIN (1-10) - The unique identifier of the vehicle
County - The county where the vehicle is registered
City - The city where the vehicle is registered
State - The state where the vehicle is registered
Postal Code - The postal code of the registration location
Model Year - The year of the vehicle's model
Make - The manufacturer of the vehicle
Model - The model of the vehicle
Electric Vehicle Type - Type of electric vehicle (e.g. battery electric, plug-in hybrid)
CAFV Eligibility Vehicle - is eligible for Clean Alternative Fuel Vehicle (CAFV) incentives or not
Electric Range - The estimated electric range of the vehicle in miles
Base MSRP - The manufacturer's suggested retail price of the vehicle
Legislative District - The legislative district where the vehicle is registered
DOL Vehicle ID - The vehicle identification number assigned by the Department of Licensing
Vehicle Location - The location of the vehicle in longitude and latitude
Electric Utility - The utility company that supplies electricity to the vehicle owner
2020 Census Tract - The census tract where the vehicle is registered
-->

# Methodology

Based on the electric vehicle (EV) population data from Washington, USA, here is the analysis for each of the machine learning methods listed:

1. Scaling/Transformation: We used Label Encoding to convert categorical variables such as County, City, State, etc. to numerical variables. We then scaled the numerical variables to have zero mean and unit variance to improve model performance.
2. Outlier/Anomaly Detection Method: While scaling the data, we found that the variables Electric Range and Base MSRP were positively skewed. We used outlier removal to reduce the data skewness after detecting the outliers using the Mahalanobis distance criteria.
3. Statistical Tests: We used the Random Forest feature importance method to rank the features by importance. This helped us in selecting the relevant features pertaining to the target variable for building the predictive model.
4. Splitting Data into Train-Test Sets: We split the data into train and test sets by specifying the test dataset size to be 20% of the original dataset.
5. Classifier: Since the target variable is continuous, we converted it into a categorical variable ('Electric Range Category'). We then used a Logistic Regression and Decision Tree Classifier, both with k-fold cross-validation and grid search CV, to predict the "Electric Range Category" of an electric vehicle based on its attributes.
6. Regressor: We used Linear Regression and Random Forest Regressor, both with k-fold cross-validation and grid search CV, to predict the electric range of the Electric Vehicle based on its attributes.
7. Clustering: We used the K-means clustering algorithm to group the electric vehicles into 3 clusters based on the Electric Range variable as follows - short range, medium range, and long range. The optimal number of clusters was found using the Elbow Method.
8. Advanced Method: We performed ensembling by using the Gradient Boosting Regressor along with Random Forest Regressor to drastically improve the model performance. This ensemble method improved the regressor’s performance by over 80%.

# Classifiers

| Classifiers | Accuracy | Precision |  Recall |  F1 |  Cross Validation | 
| --- | ----------- | --- | ----------- | --- | ----------- |
| Logistic Reg. | 58.86 | 16.15 | 58.86 | 12.19 | 59.12 | 
| Decision Tree | 98.52 | 93.87 | 98.52 | 94.17 | 98.56 | 

# Regressors

| Regressors | Cross-validation MSE | Root Mean Squared Error |   R-squared | 
| --- | ----------- | --- | ----------- |
| Linear Regressor | 58.86 | 16.15 | 58.86 | 
| Random Forest Regressor | 26.051983 | 5.104114 | 0.997443 | 

# Advanced Method

The ensemble model achieves a much lower MSE of 5.07 compared to the Random Forest model alone, indicating that the ensemble model is better at predicting the electric range of vehicles than the Random Forest model alone

|  | Mean Squared Error |
| --- | ----------- |
| Random Forest Regressor | 26.051983 |
| Random Forest + Gradient Boosting | 5.066162 |
