# 📈 Ridge Regression on 2D Data (with Custom Implementation)

This project demonstrates how **Ridge Regression** works on a simple 2D dataset, using both **scikit-learn’s Ridge** and a **custom-built Ridge class**.  
The goal is to understand how the regularization parameter **alpha** affects coefficients, intercept, and overfitting.

---

## 🛠️ Libraries Used
- **numpy**  
- **matplotlib**  
- **scikit-learn**  
  - datasets (make_regression)  
  - model_selection (train_test_split)  
  - linear_model (LinearRegression, Ridge)  

---

## 📂 Dataset
We generated synthetic regression data using scikit-learn:  

```python
from sklearn.datasets import make_regression

X, y = make_regression(
    n_samples=100,
    n_features=1,
    n_informative=1,
    n_targets=1,
    noise=20,
    random_state=13
)
This created a 2D dataset with noise.

The data was plotted to check the linear relationship.

🔎 Project Steps
Train/Test Split on the dataset.

Linear Regression:

Coefficient: 28.12

Intercept: -2.27

R² Score: 0.6345

Ridge Regression (alpha = 0):

Coefficient & intercept same as Linear Regression.

R² Score: 0.6345

✅ This proves Ridge with alpha = 0 = Linear Regression.

Ridge Regression (alpha = 10):

Coefficient: 24.83

Intercept: -2.21

R² Score: 0.6387 (slight improvement, less overfitting).

Ridge Regression (alpha = 100):

The line clearly underfits due to high regularization.

Visualization:

Plotted all three regression lines → showed how alpha controls overfitting/underfitting.

🧑‍💻 Custom Ridge Class
We created a custom Ridge class named MyRidge to replicate Ridge Regression manually.

Implementation details:
Constructor: accepts alpha (default = 0.1).

Parameters: slope m, intercept b, and regularization alpha.

In fit(X, y):

Calculates numerator and denominator.

Adds alpha to denominator (regularization term).

Formula is the same as OLS but adjusted with alpha.

Slope m is calculated using the modified denominator.

Intercept b = y.mean - (m * x.mean).

Results:
With alpha = 10, results matched scikit-learn’s Ridge.

Coefficient, intercept, and R² were the same ✅.

📊 Results Comparison
Model	Coefficient	Intercept	R² Score
Linear Regression	28.12	-2.27	0.6345
Ridge (alpha = 0)	28.12	-2.27	0.6345
Ridge (alpha = 10)	24.83	-2.21	0.6387
Ridge (alpha = 100)	~smaller	~-2.2	↓ Underfit

🎯 Conclusion
Ridge Regression works like Linear Regression when alpha = 0.

Increasing alpha reduces overfitting but too large alpha causes underfitting.

Our custom Ridge class gave the same results as scikit-learn’s Ridge ✅.

