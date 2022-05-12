# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

### Overview

The housing market is highly influenced by the economy. Although we have a vast amount of data available, our company does not have an accurate measure of housing prices. Our real estate agents share the challenge of providing an accurate estimate of the house to potential clients. Also, they need to know which features will affect the housing price and give recommendations to a potential client. Therefore, this analysis aims to develop a regression model to forecast Ames home prices and identify the most influential factors.

For this analysis, we will be looking at a comprehensive housing dataset from the city of Ames in Iowa, USA ([source](https://www.kaggle.com/competitions/dsi-us-11-project-2-regression-challenge/overview)). We will be exploring Linear, Ridge and Lasso Regression models for the prediction, where these models assume a linear relationship between input variables and the target variable. The metric used to measure their performance is the Root Mean Squared Error (RSME). In view of the project scale, the analysis will be split into 2 Jupyter notebooks:

Notebook 1 covers Data Cleaning and Exploratory Data Analysis
Notebook 2 covers Feature Selection, Modeling and Recommendations


### Data Dictionary

The data has 81 variables. The details on the data is found in the [data description](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).

The below are added features tried out duing the modeling process:

|Feature|Type|Description|
|---|---|---|---|
|total bathroom|*float*|All bathrooms in the house including basement| 
|age|*int*|Age of house (year sold minus year built)|
|overall score|*int*|Overall quality + Overall cond|
|garage score|*int*|Garage quality + Garage condition|
|exter score|*int*|Exterior quality + Exterior condition|
|bsmt score|*int*|Basement quality + Basement condition|

### Key EDA Findings

- Area and quality of the house have strong correlation to the sale price. The age of the house also shows an impact to the prices.
- We also observed a few features seem to have correlation (e.g. kitchen qc and overall qc) but the observed variables also have high correlation with the Sale Price. Hence, for such cases, we will consider to retain them. 
- From the visualizations, proximity to various conditions (Condition 2), type of dwelling (Bldg Type) and type of foundation (Foundation) show a stronger correlation to the sale price. 
- Total bathroom is an added feature which show a higher correlation than the individual bathroom features.

###  Modeling

We selected 24 features to perform the modelling using Linear, Ridge and Lasso Regression models. After spliting the train dataset, train dataset contains 1614 rows and validation dataset contains 404 rows.

Among the 3 regression models, Ridge regression has the best performance during the cross validation check (R2: 0.859). Model improvement is done with different selection. The best R2 0.870 achieved is based on the below features using the log sale price for Ridge Regression. Log sale price helps to normalize the data range and reduce the skewness. Hence, using a logarithm reduce the range of the variable but preserves the differences ([source](https://towardsdatascience.com/logarithms-what-why-and-how-ff9d050d3fd7)). This may explained why using log price helps to improve the model performance.

We adopted using the Ridge model with the best R2 score to fit the data. The R2 and RSME scores obtained for the training and validation models is shown in the table below. From the graph, the predicted value and true value fit closely to the line with a few outliers observed at the lower and higher price. Overall, the model has a good performance in predicting housing sale price.

**Features selected:** 'living area', 'total bsmt area', 'garage area', 'kitchen qc', 'fireplace qc', 'bsmt qc', 'garage qc', 'exter qc', 'overall qc', 'garage finish', 'functional', 'total bathroom', 'age', 'cond 2_Norm', 'cond 2_PosA', 'foundation_CBlock', 'foundation_PConc', 'foundation_Slab', 'foundation_Stone', 'foundation_Wood', 'bldg type_2fmCon', 'bldg type_Duplex', 'bldg type_Twnhs', 'bldg type_TwnhsE

| Model | R2 Score | RSME |
|:---------|:---------|:---------|
|Training |24031 | 0.8755 |
|Validation| 22771 | 0.8918 |

![](Images/predicted vs actual values.png)


### Conclusions

In this analysis, we have explored a housing dataset from the city of Ames in Iowa. From the exploratory data analysis, area, quality and age of the house showed a strong correlation with the housing prices. In addition, we have identified the features, home functionality, type of dwelling and foundation from the visualization. Feature engineering was explored and new features total bathrooms and age have a stronger impact on the house price. 24 features were selected for the modeling.

Linear, Ridge and Lasso regression models are used to predict the housing price. Based on the feature selection and modeling done, Ridge has a better performance than Linear and Lasso. Ridge is adopted to fit the model and the result show the model is not overfit and has a good performance in predicting the house prices.

### Recommendations

Having a bigger living and basement area and good quality of the house can increase the house prices while age of the house decrease the house price. Hence, if a client is looking to sell their house, they should try to do so earlier and highlight if they have a well maintained house. For those buying a house, we can advice them to invest in their renovation budget to maintain the quality of the house as quality is one of the influential factors. In addition, for buyers who are considering to invest in properties, we can advice them to invest in getting houses located in Stone Brook, Northridge Heights and Northridge or a bigger house in terms of the living and basement area and resell it when the house is still young.

For buyers with budget constraint, they may not be able to buy a bigger house and invest in the renovation. However, we can still share the information and help them to keep a lookout on cheaper deal so that they can allocate their budget accordingly based on their preference.

### Future Actions

We can explore fine tuning the model to further improve its performance with hyperparameters (e.g. solver, max_iter). We can consider to update the current dataset with the current year (2011) data so that we can have a better reflection for the year. In addition, we may want to review the data collection process to minimize the percentage of missing data (e.g. important consideration variable to be compulsory) so as to make the analysis more accurate and meaningful. Lastly, as the buyer/seller's perspective may change (e.g. younger generation buying houses), the team will conduct a study on new features that may impact the house sale in near future.