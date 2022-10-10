# House-Price-Regression-Kaggle
- Predictions were to be made on the test dataset.
- Evaluation of the final predictions were done by Kaggle itself and every submission gets a score. 
- Standings were based on the score, better models result in lower score.

## Importing Data
- Data was downloaded from Kaggle, this is an ongoing Kaggle competition.
- There was data from training and for testing, already split.

## Cleaning the Data
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


## 
