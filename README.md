by Hillary Chang (hic001@ucsd.edu) and Paige Pagaduan (ppagaduan@ucsd.edu)

## Overview
Our exploratory data analysis on this dataset can be found [here](https://hillarychang.github.io/Association-between-Protein-and-Calorie-Count/).

## Framing the Problem
In an era where mindful eating and wellness are in the spotlight, there's a growing emphasis on understanding the nutritional content of our meals. The calorie count of a recipe isn't just a number—it has evolved into a crucial piece of information, guiding individuals to make informed decisions about their dietary choices. For athletes, health enthusiasts, and even individuals living a normal lifestyle, having awareness of protein count and calorie content in recipes is essential for weight management, reaching fitness objectives, and fostering mindful decision-making. 

Our prediction problem for the Recipes and Ratings data set is predicting total calories based on the features of the data set, such as the number of ingredients per recipe ```n_ingredients``` and how the recipe is rated on a scale from 1 to 5 ```rating```. To model our prediction, we will be training a regression model. 

**Response Variable**: Our response variable will be an engineered column titled ```calories``` that we created during the exploratory data analysis process of this project. We believe that the ability to predict ```calories``` can be extremely useful for the food and health industry in a variety of different ways, such as in the development of new recipes and in the understanding of how different types of ingredients affect the overall caloric count of a recipe. This would not only allow manufacturers to maximize the nutritional value and quality of their products, but would also shift the industry towards a more health-conscious standard that would benefit consumers.

**Evaluation Metrics**:
We will be using the root mean square error (RMSE) in tandem with the coefficient of determination (R^2) as metrics to evaluate our regression model. 

RMSE, by definition, shows us the average error between our predictions from the actual values of ```calories```. Thus, the lower the RMSE of the model is, the more accurate the predictions it makes and the better the model is. By using RMSE to evaluate our model, we can tune it to have a relatively low RMSE, which means that it can reliably predict `calories.`

R^2, on the other hand, represents the proportion of the variance for our dependent variable ```calories``` that is predictable from the independent variables ```n_ingredients```, ```n_steps```, etc]. This is an essential metric for our model, as it provides an intuitive measure of how much of the variation in our predictions can be explained by our model. For example, a high R^2 indicates that our model can explain a large proportion of the variability in the `calories`, which is what we are training the model to do, while a low R^2 indicates the opposite, which is what we do NOT want to do. By using R^2, we can understand how closes our predictions align with the features in out model and swap out specific features depending on its value. 

**Information Known**: At the time of prediction, our data set will have all of its original columns from the merged data ```name```, ```minutes```, ```review```, etc. as well as columns that we engineered during the exploratory data analysis process from Project 3 ```avg_rating```, ```total_fat```, ```protein```, etc. 


## Base Model
**Introduction**:
The model that we will be using to solve our prediction problem will be the RandomForestRegressor. It will be trained on the`total_fat` and `sugar` features of the data set. Both of these features are quantitative.

**Data Encoding**:
For the `total_fat` feature, we applied Binarizer() with the threshold at 31.9, which is the mean of all the `total_fat` column. For the `sugar` feature, we applied StdScaler() to standardize the `sugar` for all recipes. 

**Model Description and Performance**:
We decided to use the RandomForestRegressor as our model of choice for this regression problem with default values on the parameters of the model.

Our model achieved a RMSE of 345.72485986758636 and a R^2 of 0.6556359621651207. Based on the RMSE alone, the model is very unreliable in predicting `calories` from our features, as the mean for the `calories` column is 419.52887014831776, which is relatively close to the RMSE we are achieving. Additionally, the R^2 implies that only 65.56% of the variability in the predicted `calories` can be explained by the `total_fat` and `sugar`. For our model to be considered “good,” we need to reduce the RMSE significantly and raise our R^2 to at least 90%.

| Metric            | Test Score                    |
| ------------------| ------------------------------|
| RMSE              | 345.72485986758636           |
| R^2               | 0.6556359621651207           |


## Final Model
such as the nutritional information, such as total fat (```total_fat```), sugar (```sugar```), 'carbs' (```carbs```), 'sodium' (```sodium```), 'protein' (```protein```), 'saturated_fat' (```saturated_fat```), the number of steps (```n_steps```), and the number of minutes (```minutes```) in a comprehensive recipe dataset.

| Metric            | Test Score                    |
| ------------------| ------------------------------|
| RMSE              | 47.97538413056438            |
| R^2               | 0.9933687791149496           |


## Fairness Analysis
We want to see whether our final model demonstrates a difference in performance between recipes with n_step less than or equal to 10 and recipes with n_step greater than 10. We will explore this question with a permutation test, shuffling the n_step groupings to assess the model's accuracy.

Our two groups are recipes that have `n_step` less than or equal to 10 and recipes with `n_step` greater than 10. This is because 10 is the mean n_step in the recipes dataset.

**Null Hypothesis**: Our model is fair. Its accuracy among recipes with n_step less than or equal to 10 is roughly the same as its accuracy among recipes with n_step greater than 10

**Alternative Hypothesis**: Our model is not fair. Its accuracy among recipes with n_step less than or equal to 10 is different from its accuracy among recipes with n_step greater than 10.

**Test Statistic**: We will use the absolute difference in accuracy as our test statistic. This involves calculating the absolute difference between the accuracy for recipes with n_step less than or equal to 10 and the accuracy for recipes with n_step greater than 10.


