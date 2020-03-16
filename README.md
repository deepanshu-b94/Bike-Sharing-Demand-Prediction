# Bike-Sharing-Demand-Prediction

## Purpose

Forecasting the futuristic demand has been crucial to many businesses. The main purpose of our project is to provide statistical analysis and methods that predict futuristic demand, specifically the number of registered users based on obtained information, in order to help stakeholders and investors make decisions. With accurate forecast, the cost can be cut down by optimizing the business operations – people management, financial management and cash flow. The uncertainty is reduced and helps us to anticipate the change in the market. Moreover, a promising forecast is compelling to investors who might be interested in putting money into a business. Hence for a business to operate efficiently, it needs some idea of what the future will look like. A forecast provides this look as a foundation upon which to plan.

## Modelling

Firstly, an initial feature selection based on previous correlation analysis and Exploratory Data analysis is conducted. After splitting the dataset into training and test sets, the procedure of model estimation, diagnostic, variable transformation, variable selection is followed, and it is seen if there is any benefit to use advanced models such as LASSO regression and Ridge regression. After all the models are built, we choose the best 2 models based on adjusted R^2 , RMSE and k-fold cross validation to ensure the models both well fit to training data and would have good generalization on testing data.

### Model Construction

The following list shows the 5 models and the predictors associated with each model whose performance was measured and compared. 

Model name          	Predictors
lm_full <-	season, yr, holiday, weekday, weathersit, temp, hum, windspeed

lmfullquadratic <-	season, yr, holiday, weekday, weathersit, temp, hum, windspeed, temp^2, hum^2

lmfullcubic <-	season, yr, holiday, weekday, weathersit, temp, hum, windspeed, temp^2, hum^2, windspeed^2, temp^3, windspeed^3

lmweatheronly <-	weathersit, temp, hum, windspeed

lminteractionsaic <-	season, yr, holiday, weekday, weathersit, temp, hum, windspeed, season:temp, season:hum, weathersit:temp, weathersit:hum, weathersit: windspeed

The best model was selected with lowest Mean Squared Error on test data.

## Conclusions

Exploratory Data Analysis justifies our intuition that bike usage reach its peak in summers, and drops as winter comes, and there are significant differences in number of users during different weathers, especially precipitations. The plot for the registered users over the year shows that bike sharing business follows a good trend, with seasonal fluctuations.

First, built a baseline model using predictors {season, yr, holiday, weekday, weathersit, temp, hum, windspeed}. Equal variance assumption and normality assumption didn't hold and stay incorrect in spite of response variable transformation and adding polynomial terms. An analysis on the use of LASSO regression showed that penalties on β estimates is not necessary. One possible reason is the predictor space is quite small. Comparison on models showed that the model with cubic terms and the model with interaction terms have best performance. This justifies our point from another perspective: since the predictors are limited, more complex model instead of simpler model could lead to better result



