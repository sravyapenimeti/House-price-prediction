# 🏠 House Price Prediction Using Machine Learning

## 📌 Project Overview

This project focuses on building a **machine learning regression model to predict house prices** based on various property-related features.

The project includes complete data preprocessing, exploratory data analysis (EDA), feature engineering, categorical encoding, feature scaling, model training, model comparison, evaluation, residual analysis, and saving the best-performing model for future predictions.

Two regression algorithms are implemented and compared:

* **Linear Regression**
* **Random Forest Regression**

The best model is selected based on its **RMSE, MAE, and R² Score** performance.

---

## 🎯 Objective

The main objective of this project is to develop a reliable regression model that can predict house prices accurately.

### Key Objectives

* Explore and understand the house-price dataset.
* Check and handle missing values.
* Verify duplicate records.
* Perform exploratory data analysis.
* Apply feature engineering.
* Perform log transformation where appropriate.
* Encode categorical variables.
* Scale numerical features.
* Train multiple regression models.
* Compare model performance.
* Perform residual analysis.
* Select and save the best-performing model.
* Demonstrate how to use the saved model for predictions.

---

## 📊 Dataset

The dataset used in this project is the **House Price Prediction dataset** available on Kaggle.

**Dataset Source:**

https://www.kaggle.com/datasets/bhanupratapbiswas/house-price-prediction

Download the dataset from Kaggle and place the CSV file in the project directory before running the notebook.

### Target Variable

The target variable used for prediction is:

```text
SalePrice
```

The target represents the sale price of a house.

---

## 🔍 Exploratory Data Analysis

The following EDA techniques are performed:

* Dataset shape and structure
* Data type analysis
* Statistical summary
* Missing-value analysis
* Duplicate-value checking
* Target-variable distribution
* Log-transformed target distribution
* Correlation analysis
* Correlation heatmap
* Feature vs. target visualization
* Outlier and relationship inspection

The dataset was checked for duplicate rows. Since no duplicate records were found, no duplicate-removal operation was performed.

---

## 🛠️ Data Preprocessing

### 1. Missing Value Handling

Missing numerical values are handled using the **median**.

Missing categorical values are handled using the **most frequent category**.

### 2. Categorical Encoding

Categorical variables are converted into numerical representations using:

```text
OneHotEncoder
```

The encoder uses:

```python
handle_unknown="ignore"
```

to safely process previously unseen categories.

### 3. Feature Scaling

Numerical features are standardized using:

```text
StandardScaler
```

### 4. Log Transformation

A logarithmic transformation using:

```python
np.log1p()
```

is used to examine and reduce skewness in the house-price distribution.

---

## 🧠 Feature Engineering

Additional features are created where the corresponding columns are available in the dataset.

Examples include:

### Total Bathroom

```text
TotalBath = FullBath + 0.5 × HalfBath
```

### Total Porch Area

The available porch-area features are combined to create:

```text
TotalPorchSF
```

### Total House Area

Basement and floor-area features are combined to create:

```text
TotalHouseArea
```

### Total Rooms

The available total-room feature is retained as:

```text
TotalRooms
```

Feature engineering helps the models capture more meaningful relationships between property characteristics and house prices.

---

## 🤖 Machine Learning Models

Two regression algorithms are trained and evaluated.

### 1. Linear Regression

Linear Regression is used as a baseline model for predicting house prices based on the relationship between the input features and target variable.

### 2. Random Forest Regression

Random Forest is an ensemble learning algorithm that combines multiple decision trees.

It is useful for capturing:

* Non-linear relationships
* Feature interactions
* Complex relationships between property characteristics and prices

---

## 📈 Model Evaluation

The models are evaluated using the following metrics.

### RMSE — Root Mean Squared Error

RMSE measures the average magnitude of prediction errors while giving greater weight to larger errors.

**Lower RMSE indicates better performance.**

### MAE — Mean Absolute Error

MAE measures the average absolute difference between actual and predicted house prices.

**Lower MAE indicates better performance.**

### R² Score

R² measures how well the model explains the variation in house prices.

**Higher R² indicates better performance.**

---

## 📊 Model Comparison

The notebook generates a comparison table containing:

| Model             |                   RMSE |                    MAE |               R² Score |
| ----------------- | ---------------------: | ---------------------: | ---------------------: |
| Linear Regression | Calculated in Notebook | Calculated in Notebook | Calculated in Notebook |
| Random Forest     | Calculated in Notebook | Calculated in Notebook | Calculated in Notebook |

The best model is selected primarily based on the **lowest RMSE**, while MAE and R² Score are also considered.

> **Note:** Actual metric values are generated when the notebook is executed and may vary depending on the dataset and preprocessing configuration.

---

## 📉 Residual Analysis

Residual analysis is performed to understand the errors made by the selected model.

Residuals are calculated as:

```text
Residual = Actual Price − Predicted Price
```

The project includes:

* Residual distribution plot
* Actual vs. predicted price plot
* Residuals vs. predicted values plot

A good regression model should have residuals that are approximately centered around zero and do not show strong systematic patterns.

---

## 💾 Model Saving

The best-performing model is saved using `joblib`.

```python
joblib.dump(
    best_model,
    "house_price_model.pkl"
)
```

The saved model file is:

```text
house_price_model.pkl
```

This allows the trained model to be reused without retraining it every time.

---

## 🔮 Making Predictions

The saved model can be loaded using:

```python
import joblib

loaded_model = joblib.load(
    "house_price_model.pkl"
)
```

A sample house can then be passed to the model:

```python
sample_house = X_test.iloc[[0]]

predicted_price = loaded_model.predict(
    sample_house
)[0]

print("Predicted House Price:", predicted_price)
```

---

## 📁 Project Structure

```text
House_Price_Prediction/
│
├── house_price_prediction.ipynb
│
├── train.csv
│
├── house_price_model.pkl
│
├── house_price_predictions.csv
│
├── requirements.txt
│
└── README.md
```

### File Description

| File                           | Description                                                                            |
| ------------------------------ | -------------------------------------------------------------------------------------- |
| `house_price_prediction.ipynb` | Complete Jupyter Notebook containing EDA, preprocessing, model training and evaluation |
| `train.csv`                    | House-price dataset                                                                    |
| `house_price_model.pkl`        | Saved best-performing machine learning model                                           |
| `house_price_predictions.csv`  | Sample prediction results                                                              |
| `requirements.txt`             | Required Python libraries                                                              |
| `README.md`                    | Project documentation                                                                  |

---

## ⚙️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Joblib**
* **Jupyter Notebook**

---

## 🚀 How to Run the Project

### Step 1 — Clone the Repository

```bash
git clone <your-github-repository-url>
```

### Step 2 — Open the Project Directory

```bash
cd House_Price_Prediction
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4 — Download the Dataset

Download the dataset from Kaggle and place the CSV file in the project folder.

### Step 5 — Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
house_price_prediction.ipynb
```

### Step 6 — Run the Notebook

Execute the cells sequentially from beginning to end.

The notebook will:

1. Load the dataset
2. Perform EDA
3. Check duplicate rows
4. Handle missing values
5. Perform feature engineering
6. Apply log transformation
7. Encode categorical variables
8. Scale numerical features
9. Train Linear Regression
10. Train Random Forest Regression
11. Compare model performance
12. Perform residual analysis
13. Select the best model
14. Save the trained model
15. Demonstrate house-price prediction

---

## 📦 Requirements

The project requires:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
joblib
jupyter
```

Install them using:

```bash
pip install -r requirements.txt
```

---

## ✅ Project Outcome

The project demonstrates an end-to-end **house price prediction workflow using machine learning regression techniques**.

Linear Regression and Random Forest Regression are trained and evaluated using RMSE, MAE, and R² Score. The best-performing model is selected and saved as a `.pkl` file for future predictions.

---

## 🔮 Future Improvements

The project can be further improved by:

* Hyperparameter tuning using GridSearchCV or RandomizedSearchCV
* Cross-validation
* Advanced feature selection
* Outlier treatment
* Trying additional regression algorithms
* Model interpretability using SHAP
* Building a web application using Streamlit
* Deploying the model as a REST API
* Creating an interactive house-price prediction interface

---

## 👩‍💻 Author

**Sravya**

Machine Learning / Data Science Project

---

## ⭐ Conclusion

This project provides a complete machine learning pipeline for house-price prediction, starting from raw data exploration and preprocessing through model development, evaluation, residual analysis, and model saving.

The project demonstrates practical knowledge of **regression, feature engineering, data preprocessing, model evaluation, and machine learning model persistence**.
