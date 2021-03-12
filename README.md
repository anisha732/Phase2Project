# King County Housing Data Analysis
<img src="https://github.com/anisha732/Phase2Project/blob/main/images/stripped.jpg?raw=true" alt= "house image" >

Author: Anisha Malhotra

# Overview
This project explores King County Housing Data in order to build a predictive model to estimate housing prices. 

# Problem
Identify which features help predict housing sale prices, and create a model with those features with a root mean squared error (RMSE) 
less than $200,000.

# Data
The King County housing dataset contained data from May 2014 to May 2015. The data included the prices of each house, and other features such as 
condition, grade, bedroom count, bathroom count, floors, square foot living area, etc.

# Methods
The methodology included data preparation, exploratory data analysis, feature engineering, statistical testing, feature selection, 
and running various models to determine which has the lowest RMSE.

## Exploratory Data Analysis (EDA)
<img src="https://github.com/anisha732/Phase2Project/blob/main/images/LivingSpace.png?raw=true" alt= "living space scatter" >

After plotting Living Space vs. Price, it appeared that this variable may have a significant effect on Price. After 
running statistical tests and models, I was able to confirm this.

<img src="https://github.com/anisha732/Phase2Project/blob/main/images/Grade.png?raw=true" alt= "grade boxplot" >

After plotting Grade vs. Price, it was evident that price and grade are positively correlated.

<img src="https://github.com/anisha732/Phase2Project/blob/main/images/correlation.png?raw=true" alt= "correlation" >

This correlation heat map helped determine any issues with multicollinearity between variables, as well as which features have the biggest correlation
to price. For example, sqft_above and sqft_living have a strong correlation to each other, so it was determined that only one should be used for the model.
Additionally, grade and sqft_living seem to have a strong correlation to price, so it may be worth considering including these features in the model.

## Feature Engineering
I engineered four features into my dataframe: yard space in square feet, age of the house as of 2021, the population by zip code, and the crime level by
zip code. Of those features, age of the house and crime level were the only ones I used in my model due to higher significance to price. 
After importing the crime data, I categorized the incident count per zip code into high crime, medium crime, and low crime.

<img src="https://github.com/anisha732/Phase2Project/blob/main/images/crime.png?raw=true" alt= "crime level" >


The graph shows that zip codes with higher crime had houses with lower prices. After running an ANOVA test on this data, I was able to 
conclude this data was statistically significant.

# Modeling
## Selection
Based on correlation factors, and running Kbest Features selection, I chose the features as bedrooms, bathrooms, sqft_living, years_old, and dummy
variables of zip code, waterfront, crime rate, and grade for my model.

## Model Evaluation
After running a train test split on a Polynomial and Interactions Model, along with a KBest Selection method, I ran 
a model based on the log of the price. The model that gave me the lowest RMSE score was the Log Model.
<img src="https://github.com/anisha732/Phase2Project/blob/main/images/log_model.png?raw=true" alt= "Model" >

Based on this model, the r-squared value was about 86% and RMSE was 144,371.
<img src="https://github.com/anisha732/Phase2Project/blob/main/images/log_final_score.png?raw=true" alt= "final rsquared" >

# Future Work
Going forward, I want to explore different features and their effect on price to include in the model for an even lower RMSE. 
Additionally, I would run more models to determine if there are any that result in more accurate predictions.

# Repository Structure
```
├── code
│   ├── Proj2_notebook_raw.ipynb
│   ├── Final Project 1 Notebook.ipynb
│   ├── PullingDataProj1.ipynb
│   └── functions.py
├── data
│   ├── crimes.csv
│   ├── housing_preds_anisha_malhotra.csv
│   ├── kc_house_data_test_features.csv
│   ├── kc_house_data_train.csv
│   └── zip_code_database.csv
├── images
├── Proj1Presentation.pdf
├── README.md
├── br_median.pickle
└── model.pickle
```
