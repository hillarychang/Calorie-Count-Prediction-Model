by Hillary Chang (hic001@ucsd.edu) and Paige Pagaduan (ppagaduan@ucsd.edu)

## Framing the Problem

Our exploratory data analysis on this dataset can be found [here](https://hillarychang.github.io/Association-between-Protein-and-Calorie-Count/).

In an era where mindful eating and wellness are in the spotlight, there's a growing emphasis on understanding the nutritional content of our meals. The calorie count of a recipe isn't just a number—it has evolved into a crucial piece of information, guiding individuals to make informed decisions about their dietary choices. For athletes, health enthusiasts, and even individuals living a normal lifestyle, having awareness of protein count and calorie content in recipes is essential for weight management, reaching fitness objectives, and fostering mindful decision-making. Our specific aim is to predict the caloric content ```calories``` of a recipe based on its features of the data set, such as ```n_ingredients``` and ```rating```. This is a regression problem since we aim to predict a continuous numeric variable, calories. To model our prediction, we will be training a RandomForestRegressor model. 

**Response Variable**: Our response variable will be an engineered column titled `calories` that we created during the exploratory data analysis process of this project. In the real world, the calorie count of a recipe is very important, as it can help consumers dictate what to eat to maintain or meet dietary goals. Therefore, trying to correctly predict the calorie count of a recipe can be very important for many consumers.

**Evaluation Metrics**: Since our model is a regressor, we will evaluate our model with the R^2 of the model. We believe that (explain why we chose the response variable and why the metric we chose is best for identifying it in context of the problem). 

**Information Known**: At the time of prediction, we would know (columns to train on).


## Base Model



## Final Model
such as the nutritional information, such as total fat (```total_fat```), sugar (```sugar```), 'carbs' (```carbs```), 'sodium' (```sodium```), 'protein' (```protein```), 'saturated_fat' (```saturated_fat```), the number of steps (```n_steps```), and the number of minutes (```minutes```) in a comprehensive recipe dataset.
