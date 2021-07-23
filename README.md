# King County Housing

Linear Regression Model 

## Motivation

In analyzing the King County Housing data, I aim to give recommendations and insights to real estate investors as to which features of a home and which areas within the county will maximize their profits. 

## Data

The information on properties in King County came from a dataset provided by kaggle.com. Originally, the dataset cotained 21,597 rows, representing individual properties, and 21 columns, representing features about each property.

## Methodology

1. I retained features that reflected the overall structure of the home and property along with features which were indicative of areas within King County. I chose to concentrate on what I defined as non-starter homes in the price range of 200-500 thousand dollars. Beyond eliminating features deemed superfluous, I additionally eliminated properties with either extravagant attributes - such as 6 or more bedrooms - or substandard qualities, like not having at least 1 full bathroom.
2. Next, I investigated into possible correlation between features. No features were correlated with the target, price, which was confirmed by both a scatter matrix as well as by a correlation matrix. Using the same two techniques for confirmation, the features sqft_above and sqft_living were found  to be collinear leading to the elimination of sqft_above.  Additionally, via the scatter matrix, the following features were determined to be categorical: bedrooms, bathrooms, floors, condition, and grade. The features yr_renovated, sqft_basement and waterfront were turned into binary categorical variables indicating presence of feature at the property. The heat map implied a relation between bedrooms, bathrooms, and sqft_living,  a relation between grade, sqft_above, and yr_built, and possibly a relation between bathrooms and grade, sqft_above, and yr_built.    
![Screenshot from 2021-07-23 11-46-40](https://user-images.githubusercontent.com/75818628/126816096-fc8fa009-80e7-47d8-b50a-bcf83185ef75.png)
3. Subsequently, multiple linear regression were run with the initial model having few changes to the original data other than cleaning. Categorical features were dummied which led to the discovery by way of a fresh correlation matrix of other collinear features and thus two more features were eliminated. More iterations followed and it was deemed prudent to standardize and log transform a few features. 
4. Between iterations, the residuals were examined visually through distribution histograms, qqplots, and scatter plots. Furthermore, the kurtosis and skewness statistics were inspected to evaluate normality and homoskedasticity. 
5. In the latter iterations, p-values were thoroughly examined against the set alpha threshold of 0.05. Features whose p-values remained insignificant and unchanging through iterations were expunged. Additionally, multiple cross validation checks were run to assess vaildity of the model's fit.

##Findings


