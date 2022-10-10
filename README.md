# House-Price-Regression-Kaggle
- Predictions were to be made on the test dataset.
- Evaluation of the final predictions were done by Kaggle itself and every submission gets a score. 
- Standings were based on the score, better models result in lower score.

## Importing Data
- Data was downloaded from Kaggle, this is an ongoing Kaggle competition.
- There was data from training and for testing, already split.

## Cleaning the Data
- Ensured proper data types for each feature.
- The train as well as the test dataset contained a lot missing values.
- Combined the both the train and test datasets for better understanding of the data. 
  *This was done only to handle the missing values and this step was well within the realm of competition rules*
- The data had missing data - both categorical and numerical.
#### Categorical data was handled based on 2 cases:
1. Missing values had a meaning i.e., NaN meant "Not Available" for that corresponding cell for a particular column. *for ex: Alley column had missing values meaning the property had no alley.*
2. Missing values had no meaning. These were filled bby using the mode for the corresponding column.

#### Numerical data:
- These were handled by using the *K-neighbors Regressor*.
- Every row with na values was filled with the value of the corresponding predicted neighborhood it is belonging to, with the help of Regressor trained over the non-na targets.


## Feature Engineering and Transformations
- Engineered some new features from the existing ones.
- Transformed *skewed* features into *log(1+x)* with the help of *Numpy*. 
- - *log(1+x)* as *log(x)* is undefined at *x = 0*
- Transformed *cyclical* features into *cosine*
- - For ex: Months - a cyclical feature- was cosine transformed.
- As the features were log transformed, the result will be in a log transfered output.
- Hence, the target was also log transformed.

![](https://github.com/AnandBallure/house-price-regression-kaggle/blob/main/log-transform.png)

## Encode Categoricals
- Encoded categorical features with the help of *pandas get_dummies* function.
 
 
 ## Scaling
 - Scaled features using *Sklearn's Standard Scaler* library.

## Split Data
- Now the train and test data is split into their earlier versions. 
- - *This was possible as the data was never shuffled.*

## Model Selection
- Best performing models were selected and compared amongst each other with the help of an automated machine learning tool - *PyCaret* 
- Top 5 models were
1. Bayesian Ridge
2. CatBoost
3. Lightgbm
4. Ridge
5. OrthogonalMatchingPursuit

![](https://github.com/AnandBallure/house-price-regression-kaggle/blob/main/CV.png)

## Hyperparameter Optimization
- Top 5 models were optimized with the help of *Optuna*
- *Optuna* creates a study for each model and then optimizes the hyperparameters for the corresponding model.
- Best parameters were selected and used in further training.


## Bagging Ensemble
- Tuned models were bagged together and trained over the training set.

## Evaluation and Results
- Results were evaluated by monitoring the cross validation score for each model in 10 fold evaluation.
- As the results were log transformed, each models' results were hence transformed back by exponentiating.
- Results were aggrigated for each model.
- Final predictions were made with 40% contribution from CatBoost, 20% from Bayesian Ridge, 20% from Lightgbm, 10% from Ridge, 10% from OrthogonalMatchingPursuit.
- Final results were then joined with their respective ids and the dataframe was converted to a CSV file.
- After submission, a score of 0.12108, was achieved. 
- Secured a rank in the top 10%.
