# Used Car Price Prediction

Predicts the fair market price of a used car (in Lakhs INR) from its specifications, and flags listings priced above or below market.

## Dataset
- File: `usedCars.csv` (1,064 listings, 19 raw columns, 30 columns after cleaning)
- Target: `Price_Lakhs`
- Source: [add dataset link here]

## Approach
1. Cleaning: standardised company and model names, colours, transmission and fuel; handled missing values
2. Feature engineering: car age, kilometres per year, luxury-brand flag, automatic flag, CNG flag
3. Preprocessing with a Scikit-Learn `ColumnTransformer` (scaling, one-hot encoding, target encoding for company and model)
4. 80/20 split (851 train / 213 test)
5. Models compared: Linear, Ridge, Lasso, KNN, Decision Tree, Random Forest, Gradient Boosting
6. Hyperparameter search for Random Forest and Gradient Boosting; final model is Gradient Boosting

## Results
| Check | R-squared | MAE (Lakhs) | MAPE |
|---|---|---|---|
| Hold-out test set (213 cars) | 0.847 | 1.13 | 13.3% |
| 5-fold out-of-fold (all 1,064 cars) | 0.703 | 1.23 | 13.6% |

- 50% of test predictions are within 10% of the actual price and 78% are within 20%.
- Error is lowest for mid-priced cars (MAPE 11.5%) and highest for luxury cars (26.9%, only 6 test cars).
- Most important features (permutation importance): car model and car age.

Note: the dataset is small, so the hold-out score is higher than the cross-validated score. Treat the cross-validated figure as the more conservative estimate.

## Outputs
Running the notebook saves the trained model (`used_car_price_model.joblib`), result tables and Power BI data in the `outputs/` folder.

## How to run
```bash
git clone https://github.com/tiwariswati186-alt/used-car-price-prediction.git
cd used-car-price-prediction
pip install -r requirements.txt
jupyter notebook Predicting_Used_Car_Prices.ipynb
```
Keep `usedCars.csv` in the same folder as the notebook.

## Tech stack
Python, Pandas, NumPy, Scikit-Learn, Joblib, Matplotlib, Seaborn, Power BI (dashboard)

## Author
Swati Tiwari | [GitHub](https://github.com/tiwariswati186-alt) | [LinkedIn](https://www.linkedin.com/in/swati-tiwari-37972317a)
