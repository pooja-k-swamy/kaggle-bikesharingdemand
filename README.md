## Bike sharing demand Kaggle competition

The problem deals with analysis of the demand in the Capital Bikeshare program of Washington D.C. We need to combine historical usage patterns with weather data to forecast the bike rental demand. Therefore, it’s a regression problem.
The generated data comprises of duration of travel, departure location, arrival location, and time elapsed. Frequency of the data recorded is one hour. So, we are provided hourly rental data spanning two years. 
Bike sharing systems therefore function as a sensor network, which can be used for studying mobility in a city.
Training set is of the first 19 days of each month while testing data is of the remaining days.

### Data Description
We are provided hourly rental data spanning two years.
Size of Dataset:
Total 10886 training samples and 6493 test samples
Numerical feature: 
temp: temperature; 	atemp: “feels like” temperature
Humidity; windspeed; casual; registered
Categorical feature:
Season: 1=spring; 2=summer; 3=fall; 4 = winter
Holiday: whether the day is considered a holiday
Workingday: whether the day is neither a weekend nor holiday
Weather: 1,2,3,4 (follow good to extremely bad)
Object: Datetime: hourly date+timestamp
Dependent variable: count: number of total rentals
The dataset was provided by Hadi Fanaee Tork using data from Capital Bikeshare. It is hosted on UCI, and is accessible at [this link] http://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset

### Feature Engineering

* Transform datatime to hour/day/month/year
* Drop atemp since it is highly correlated to temp
* Data distribution and correlation of the features is visualised for better understanding of the dataset


### Model Fitting

For training data, need to split it into training set (80%) and validation set (20%) to test the model performance
In this project, we are going to calculate Root Mean Squared Logarithmic Error (RMSLE) to test each model’s performance on Validation set, select the best model with lowest RMSLE value

#### Model Selection

Different models implemented are:
* KNN                                                
* Random Forest
* Support Vector Regression
* AdaBoost
* Bagging Regression
* Gradient Boost
* Linear Regression 

*Tune parameters with Grid Search with the three best models*
* Random Forest
* Bagging
* Gradient Boosting

Regularization models
* LASSO
* Ridge

Model | RMSLE value 
------------ | -------------
Random Forest | 0.33519
Gradient Boosting | 0.2704
Bagging Regression | 0.3329

### Model Improvement

Model | RMSLE value | Key Difference
------------ | ------------- | -------------
LASSO | 0.982348 | Feature selection by penalty function(L1)
Ridge | 0.982389 | Avoid Overfitting by penalizing features(L2)

### Summary and Results

####### ![Screenshot (11)](https://user-images.githubusercontent.com/60587239/81622706-c0befc80-93bf-11ea-8ffc-e17b67a1bb55.png)

Gradient Boosting(After Tuning hyperparameters) performs best on the validate set, with lowest RMSLE value of 0.27047

Thank you!
