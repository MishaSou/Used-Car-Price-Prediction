# 🚗 Used Car Price Prediction

## 📌 Overview
This project aims to predict the selling price of used cars using a dataset sourced from Kaggle. The dataset contains **558,837 rows** and includes various attributes such as car make, model, trim, body type, transmission type, odometer reading, and sale date. The machine learning models used for prediction are **Random Forest Regressor** and **XGBoost Regressor**.

---

## 📊 Data Preprocessing
To prepare the dataset for training, the following preprocessing steps were performed:

### 🛠️ Handling Missing Values
- Filled missing values in categorical columns (`transmission`, `make`, `model`, `trim`, `color`, `body`) with placeholder values.
- Dropped rows with missing values in critical numerical columns (`odometer`, `condition`, `mmr`, `saledate`, `vin`).

### 🔍 Feature Engineering
- Standardized `condition` values by scaling them (multiplying by 10 when ≤5) and categorizing them into a new `newcondition` feature.
- Extracted `carage` from `saledate` and `year` to represent vehicle age.
- Converted `saledate` into a datetime format and extracted `saleday` (day of the week).
- Created a new feature `profit` by subtracting `mmr` from `sellingprice`.

### 🧹 Data Cleaning
- Standardized manufacturer names (e.g., 'Mercedes-Benz' and 'Mercedes B' converted to 'Mercedes Benz').
- Grouped similar body types under common labels (e.g., different cab styles mapped to 'Pickup').

### 🎭 Encoding Categorical Features
- Applied one-hot encoding for `transmission`.
- Used Label Encoding for `make`, `model`, `body`, `state`, `color`, and `interior`.
- Saved label encoders using `pickle` for future reference.

## 🌍 Correlation Heatmap
- A correlation heatmap was generated to visualize relationships between numerical features.

### ✂️ Feature Selection
- Dropped non-essential columns: `trim`, `vin`, `condition`, `seller`, `saledate`, `saleday`, `carage`, `mmr`.

---

## 🤖 Model Training

Two machine learning models were trained to predict the selling price:

### 1️⃣ Random Forest Regressor
Hyperparameter tuning was performed using **GridSearchCV**, and the best parameters were:

- `n_estimators=100`
- `max_depth=20`
- `min_samples_split=2`
- `min_samples_leaf=3`
- `random_state=23`

### 2️⃣ XGBoost Regressor
Trained with the following parameters:

- `n_estimators=100`
- `learning_rate=0.1`
- `max_depth=20`
- `random_state=23`

---

## 📈 Model Performance

| Model | MAE | RMSE | R² Score | MAPE |
|--------|-------|---------|---------|---------|
| **Random Forest** | 1424.78 | 2611.95 | 0.93 | 16.78% |
| **XGBoost** | 1366.68 | 2645.71 | 0.93 | 14.40% |

---

## ✅ Conclusion

This project successfully predicts used car prices using machine learning models with high accuracy. Both **Random Forest** and **XGBoost** achieved **R² scores of 0.93**, making them strong predictors for vehicle price estimation. 

🚀 Future improvements include:
- Fine-tuning hyperparameters further.
- Incorporating additional features like regional pricing trends.
- Experimenting with deep learning models.

---

## 📜 License
This project is open-source and available under the [MIT License](LICENSE).

