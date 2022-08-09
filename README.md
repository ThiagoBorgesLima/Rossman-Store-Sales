
<img src="https://github.com/ThiagoBorgesLima/Rossman-Store-Sales/blob/main/imgs/rossmann.jpeg" width="900" height="475"><br>



# Rossmann Sales Prediction

This repository contains all steps based on CRISP-DS process model methodology to build a prediction sales model for a large drugstore chain. The data used in this model is available at the [Rossmann Store Sales competition page ate Kaggle.](https://www.kaggle.com/competitions/rossmann-store-sales/overview/description)

All information below is fictional.

## 1. Business Problem

Rossmann is one of largest drug store chain in Europe, operating over 3,000 drug stores in 7 countries across the continent.

Recently, the CFO received the task to renovate Rossmann stores and, in order to decide the amount of money each store will receive in the next period budget for renovation, he or she wants to know how much each store will sell in the next six weeks.

Therefore, this project was developed to use historical data from the stores to create a model that predicts sales in the next six weeks.

## 2. Data

The data used in this project can be found at:<br>
https://www.kaggle.com/competitions/rossmann-store-sales/data
<br>

<details><summary>Click here to see the original attibutes table</summary><br>
  
Attribute | Definition
------------ | -------------
|Id  | an Id that represents a (Store, Date) duple within the test set|
|Store | a unique Id for each store|
|Sales| the turnover for any given day (this is what you are predicting)|
|Customers | the number of customers on a given day|
|Open | an indicator for whether the store was open: 0 = closed, 1 = open|
|StateHoliday  | indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None|
|SchoolHoliday | indicates if the (Store, Date) was affected by the closure of public schools|
|StoreType| differentiates between 4 different store models: a, b, c, d|
|Assortment | describes an assortment level: a = basic, b = extra, c = extended|
|CompetitionDistance | distance in meters to the nearest competitor store|
|CompetitionOpenSince[Month/Year]| Agives the approximate year and month of the time the nearest competitor was opened|
|Promo  | indicates whether a store is running a promo on that day|
|Promo2 | Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating|
|Promo2Since[Year/Week]  | describes the year and calendar week when the store started participating in Promo2|
|PromoInterval | describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store|
</details>


<details><summary>Click here to see the created attibutes table in Feature Engineering session</summary><br>
  
Attribute | Definition
------------ | -------------
|year  | year the sale took place|
|month | month the sale took place|
|day| day the sale took place|
|week_of_year | week number of the year the sale took place|
|year_week | year and week number the sale took place|
|competition_time_month  | number of months competition started|
|promo_time_week| number of weeks since promotion has began based on sales date|
</details>

## 3. Business Assumptions

* For the stores with missing <i>"CompetitionDistance"</i> it was assigned a large distance, assuming that there is no competidor nearby.
* All lines with values in the column <i>"Open"</i> equal to 0 (meaning store closed) were removed.
* For all lines with missing values for <i>"CompetitionOpenSince[Month/Year]"</i> and <i>"Promo2Since[Year/Week]"</i>, the missing value was filled using the <i>"Date"</i>.

## 4. Solution Strategy

1. Data Description Analysis
2. Feature Engineering
3. Data Filtering
4. Exploratory Data Analysis
5. Data Preparation
6. Feature Selection
7. Machine Learning Modeling 
8. Hyperparameter Fine Tuning
9. Understand Model Performance
10. Deploy

## 5. Tools and Machine Learning Models

* Python 3.8
* Boruta as feature selector
* Linear Regression
* Regularized Linear Regression (LASSO)
* Random Forest Regressor
* XGBoost Regressor

[![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/python/plotly-express/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![SciPy](https://img.shields.io/badge/SciPy-%230C55A5.svg?style=for-the-badge&logo=scipy&logoColor=%white)](https://scipy.org/)
[![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com/)
[![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Heroku](https://img.shields.io/badge/heroku-%23430098.svg?style=for-the-badge&logo=heroku&logoColor=white)](https://www.heroku.com/)





## 6. Models Performance

For the problem solution, it was evaluated four machine learning algorithms: Linear Regression, Lasso Regression, Random Forest Regressor and XGBoost Regressor.

A cross-validation was made for each model, evaluating the Mean Absolute Error (MAE), the Mean Absolute Percentage Error (MAPE) and the Root Mean Squared Error (RMSE). The average cross-validation error as well their respective standard deviation are ilustrated in the table below:

|       Model Name          |        MAE CV       |    MAPE CV    |      RMSE CV       |
|:-------------------------:|:-------------------:|:-------------:|:------------------:|
| Linear Regression         |  2081.73 +/- 296.56 | 0.30 +/- 0.02 | 2953.15 +/- 468.99 |
| Lasso Regression          |  2115.89 +/- 341.40 | 0.29 +/- 0.01 | 3056.97 +/- 504.51 |
| Random Forest Regressor   |  841.86 +/- 221.10  | 0.12 +/- 0.02 | 1261.16 +/- 316.28 |
| XGBoost Regressor         |  1029.56 +/- 183.99 | 0.14 +/- 0.02 | 1485.04 +/- 262.49 |
 

Even though Random Forest Regressor model presented a slightly better performance, it was decided to proceed with XGBoost Regressor model because of the signicant lower memory and time consuming.

After running hyperparameter fine tuning for XGBoost Regressor model, the final performance was found as showed below.

|    Model Name        |     MAE      |    MAPE    |     RMSE       |
|:--------------------:|:------------:|:----------:|:--------------:|
|  XGBoost Regressor   |   626.974   |   0.0910    |   918.043      |

Error (real sales - prediction) scatter plot:

<img src="https://github.com/ThiagoBorgesLima/Rossman-Store-Sales/blob/main/imgs/errorxpred2.png" width="900" height="475"><br>

## 7. Business Results

In terms of business, MAE means how much the prediction is wrong, defining upper and lower bounds. MAPE means the percentage that predicted values are different when compared to the target values, thus, being an easy-to-interpret metric. 

The table below shows the worst store predictions, explaining that some stores are more difficult to predict sales. The worst_scenario field is calculated by subtracting the MAE from the predictions field and the best_scenario field is calculated by adding the MAE field.

|   store |   predictions |   worst_scenario |   best_scenario |      MAE |     MAPE |
|--------:|--------------:|-----------------:|----------------:|---------:|---------:|
|   292   |     105028    |      101730      |      108326     |  3298.2  | 0.544053 |
|   909   |     229375    |      221574      |      237175     |  7800.4  | 0.519917 |
|   876   |     206166    |      202181      |      210151     |  3984.9  | 0.305917 |
|   595   |     369952    |      365648      |      374257     |  4303.3  | 0.293733 |
|   722   |     344922    |      343148      |      346696     |  1773.7  | 0.240981 |



Finally, the table below shows the sum for all stores, as well as the worst and best scenarios:

| Scenario       | Values           |
|:---------------|:-----------------|
| predictions    | R$283,901,824.00 |
| worst_scenario | R$283,198,749.24 |
| best_scenario  | R$284,604,871.47 |


## 8. Telegram Bot

It was created a Telegram Bot in order to easily accesss predictions for individual stores by texting the store number you want the see the sales prediction. Bot can be accessed at https://t.me/rossmann_t_bot.

<img src="https://github.com/ThiagoBorgesLima/Rossman-Store-Sales/blob/main/imgs/bot.png" width="600" height="375">




## 9. Conclusion

The objective of this project was to simulate a real life business problem and address the solution using Machine Learning models. By using CRISP-DS methodoly, it was possible to build an organized structure in order to understand the business problem, analyse the data, test models and finally provide an accurate sales predictions for the stores. 

## 10. Next Steps
Next step would be run a second cycle for CRISP-DM proccess with focus on following points:
* Create new and more relevant parameter at feature engineering.
* Create more hypotesis in order to find more relevant variables.
* Test more Machine Learning models.
* Improve messages in the Telegram Bot.
<br>

---
## References:

* Datasets Rossmann Store Sales from [Kaggle](https://www.kaggle.com/competitions/rossmann-store-sales/data)
* Variables meaning on [Kaggle discussion](https://www.kaggle.com/competitions/rossmann-store-sales/overview)
* Comunidade DS

# Author

Thiago Borges Lima


[<img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>](https://www.linkedin.com/in/thiago-borges-lima-a731115b)
