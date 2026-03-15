# BigMart Sales Prediction

## What is this project?
BigMart is a retail chain with stores across different cities. 
This project predicts how much of each product a store will sell, 
using information about the product and the store.

## Dataset
- Source: [Kaggle - BigMart Sales Data](https://www.kaggle.com/datasets/brijbhushannanda1979/bigmart-sales-data)
- 8,523 rows of product and store data
- Target: `Item_Outlet_Sales` (how much each product sells)

## Steps

### 1. Handling Missing Values
- `Item_Weight` — filled with the average weight
- `Outlet_Size` — filled using the most common size for each outlet type
- `Item_Visibility` — some items had 0% visibility which is not realistic, 
  so filled with average visibility per item type

### 2. Feature Engineering
- Created `Outlet_Age` — how long the store has been open (2013 minus opening year)
- Removed `Outlet_Establishment_Year` since age is more meaningful

### 3. Encoding Categorical Features
- `Outlet_Size` — manually mapped (Small=0, Medium=1, High=2) to preserve order
- All other text columns — converted to numbers using Label Encoding

### 4. Model — XGBoost
- Used XGBoost Regressor for prediction
- Tuned hyperparameters using GridSearchCV (5-fold cross validation)
- Best settings found: `n_estimators=150, max_depth=3, learning_rate=0.05`

## Results
| | R² Score |
|--|--|
| Training | 0.629 |
| Testing | 0.589 |
| Cross Validation | 0.601 |

## How to Run
1. Open the notebook in Google Colab
2. Add your Kaggle API key where indicated
3. Run all cells in order

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](YOUR_COLAB_LINK_HERE)
