# Culture_CovidSpread-Final-project-kickoff
## Analysing the Impact of Culture & Socio Demographics on the Spread of Covid
# The Target Variable is the no. of registered covid cases per 100k per country, 193 weeks after the first case has been reported
# Data has been taken from World Data and WDI 
# Cultural Aspects are based on Hofstede's cultural Dimensions

Data has been cleaned, nans removed, all data set to the same starting point(first week a covid case was recorded) 
194 weeks of covid data have been analysed for 75 countries

Data has been screened and checked for outliers, but due to small sample size outliers (especially for GDP features) could not be removed
Data has been analysed for correlation using pearson and p values have been analysed for feature selection
after feature removal, R-squared and adjusted R have both decreased in itself but also decreased the difference among themselves.

The Adjusted R-squared value is similar to the Multiple R-squared value, but takes the number of  into account. Hence R-squared will always increase when a new variable is added to the prediction model, but if the variable is non-significant the Adjusted R-squared value will decrease.

The lower difference between R2 and adjusted R after feature removal speaks for less non-significant variables within the model.


## Train Test Split and X Feature Selection

## Feature Engineering
Different options have been checked against each other - log transformation, outlier removal, etc
Most work has been put into feature selection as the Model quickly overfit due to the small sample size

## Modeling
9 different models were tested against each other
model1 = linear_model.LinearRegression()
model2 = KNeighborsRegressor(7)
model3 = RandomForestRegressor(random_state=0)
model4 = Lasso(alpha=1.0)
model5 = ElasticNet(random_state=0)
#model6 = svr_lin
model7= svr_rbf
model8= ridge    #RidgeRegression
model9 = reg 

The Models (Lasso, ElasticNet, SVR_RBF, RidgeRegression and EstraTree) have been selected due to their good fit for small sample sizes.
Lineat Regression, KNeighbors and RandomForest have been added for comparison

## checking for overfit 

by comparing the y_test Mean to the y_test + Y-modelN RMSE

 Comparing the RMSE of yTest and YPredicted (per model) with the YTest Mean to see how well the model performs. If e.g. the RMSE is 10% above or below the mean, we have a good fit!
 
 ## Outcome
 Though it was possible to detect features that show a significant impact on the No. of covid cases per 1000k inhabitants, the modes show a very low RSquare value. Therefore additional Features need to be added to create a model. Additionally, the model is strongly overfit due to the small sample size. 

As a next step, additional features (e.g. wind, temperature, nutrition, sports events) need to be evaluated for their fit for the model
Furthermore, the data set needs to be enlarged - e.g. by going from country to regional data. 
