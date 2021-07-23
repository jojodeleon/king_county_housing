
![thom-milkovic-skUTVJi8-jc-unsplash](https://user-images.githubusercontent.com/75818628/126841008-99044eb9-2dbf-43e7-8a4d-35c3d40bf48e.jpg)
# King County Housing

Linear Regression Model 

## Motivation

In analyzing the King County Housing data, I aim to give recommendations and insights to real estate investors as to which features of a home and which areas within the county will maximize their profits. 

## Data

The information on properties in King County came from a dataset provided by kaggle.com. Originally, the dataset contained 21,597 rows, representing individual properties, and 21 columns, representing features about each property.

## Methodology

1. I retained features that reflected the overall structure of the home and property along with features which were indicative of areas within King County. I chose to concentrate on what I defined as non-starter homes in the price range of 200-500 thousand dollars. Beyond eliminating features deemed superfluous, I additionally eliminated properties with either extravagant attributes - such as 6 or more bedrooms - or substandard qualities, like not having at least 1 full bathroom.
2. Next, I investigated into possible correlation between features. No features were correlated with the target, price, which was confirmed by both a scatter matrix as well as by a correlation matrix. Using the same two techniques for confirmation, the features sqft_above and sqft_living were found  to be collinear leading to the elimination of sqft_above.  Additionally, via the scatter matrix, the following features were determined to be categorical: bedrooms, bathrooms, floors, condition, and grade. The features yr_renovated, sqft_basement and waterfront were turned into binary categorical variables indicating presence of feature at the property. The heat map implied a relation between bedrooms, bathrooms, and sqft_living,  a relation between grade, sqft_above, and yr_built, and possibly a relation between bathrooms and grade, sqft_above, and yr_built.    
![Screenshot from 2021-07-23 11-46-40](https://user-images.githubusercontent.com/75818628/126816096-fc8fa009-80e7-47d8-b50a-bcf83185ef75.png)
3. Subsequently, multiple linear regressions were run with the initial model having few changes to the original data other than cleaning. Categorical features were dummied which led to the discovery by way of a fresh correlation matrix of other collinear features and thus two more features were eliminated. More iterations followed and it was deemed prudent to standardize and log transform a few features. 
4. Between iterations, the residuals were examined visually through distribution histograms, qqplots, and scatter plots. Furthermore, the kurtosis and skewness statistics were inspected to evaluate normality and homoskedasticity. 
5. In the latter iterations, p-values were thoroughly examined against the set alpha threshold of 0.05. Features whose p-values remained insignificant and unchanging through iterations were expunged. Additionally, multiple cross validation checks were run to assess vaildity of the model's fit.

## Analysis of Model

![Screenshot from 2021-07-23 12-38-51](https://user-images.githubusercontent.com/75818628/126821405-f1065c0c-462a-498f-8f25-469b3745f521.png)
1. The R-squared value of 0.679 has been consistent since the fifth iteration and varied from this in the 3rd and 4th iterations by a difference of merely 0.001. As R squared measures the strength of the relationship between our model and the target variable, price, this indicates that 67.9% of the variance in the price is explained by the predictor variables collectively.
2. All p-values of the remaining predictors are significant and have a value much less than the threshold alpha of 0.05. The intercept's p-value remained insignificant. However, this should not be seen as problematic.  The intercept is the value of the price when all the features are zero which in this case would mean there existed no property i.e. this is a nonsensical case that is far outside the observed data.
3. The final skewness evaluated for this model is -0.106 suggesting that the distribution is approximately symmetric and therefore indicative of a normal distribution. At 4.429 this model's kurtosis demonstrates a "skinny" leptokurtic distribution, a distribution with longer and fatter tails where the peak is higher and sharper than the peak of a normal distribution. This indicates the distribution has heavy tails and that there are outliers.
4. The RSME has remained consistent and acceptable starting with the 3rd iteration. This demonstrates that the model is a good fit signifying that the observed data points are close to the model's predicted values and therefore this fitted model should predict well. 
5. All cross validation tests have calculated a large, negative MSE indicating a robust model. 
6. The residual distribution appears normalish and meets the normality assumption. A qqplot confirmed the homoskedastic assumption as the variance of the residuals is constant or, in other words, the residuals do not vary much as the price changes as seen by the overall good fit of the data points.  

## Findings

#### Inconlusive Feature
When reversing the standardized and log transformed coefficient of the feature sqft_living, the result was implausably large. Future investigation as to whether this feature interacts with other features, such as bedrooms or bathrooms, is required to make a proper assessment of this feature. 

#### Negative Influence on Price
Of the 80 features explored, there were only four predictors that have a negative effect on the home's price, namely presence of a basement, having three floors, the property receiving a grade by the county in the range of 4-9, and the property being situated in the zipcode 98023. 

#### Positive Influence on Price
The majority of features have a positive on the price of the home. For features that denote the structure of the home itself that have a beneficial affect on value are the  property having had renovations, the property having two bedrooms, and the property having multiple bathrooms:<br>
   
When all other features are zero, a one foot increment in the square footage of the lot corresponds to an increase in $17.63 of property value.

Of the 62 zipcodes in the model, all but one of the zipcodes increase home values. This suggests that King County in general is a very desirable county in the area in which to invest in property.  This finding is significant so I focus on the top ten zipcodes for a maximum return on investment. However, I would also note that there are 24 zipcodes whose return on investment factor is at least two.<br>
>  The following zipcodes have the greatest rate of return:<br>
> > zip_98107: \\$3.0465 increase per \\$1 increase in price   
   zip_98102: \\$2.9990 increase per \\$1 increase in price   
   zip_98105: \\$2.9930 increase per \\$1 increase in price  
   zip_98112: \\$2.8805 increase per \\$1 increase in price  
   zip_98117: \\$2.6987 increase per \\$1 increase in price   
   zip_98199: \\$2.6372 increase per \\$1 increase in price  
   zip_98119: \\$2.6138 increase per \\$1 increase in price   
   zip_98115: \\$2.6004 increase per \\$1 increase in price   
   zip_98005: \\$2.5670 increase per \\$1 increase in price  
   zip_98116: \\$2.5335 increase per \\$1 increase in price  

![Screenshot from 2021-07-23 12-51-21](https://user-images.githubusercontent.com/75818628/126822011-e9c61a22-355d-4d84-a452-b3c3c3654699.png)














