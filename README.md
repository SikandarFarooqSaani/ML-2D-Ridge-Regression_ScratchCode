Ridge Regression on 2D Data

This project demonstrates the concept of Ridge Regression (also known as L2 Regularization) on a simple 2D dataset. The implementation includes both Scikit-learn’s Ridge Regression and a custom Ridge Regression class built from scratch to understand the math and logic behind it.

📌 Project Workflow

Dataset Creation

Used sklearn.datasets.make_regression to generate a synthetic dataset:

X, y = make_regression(
    n_samples=100, 
    n_features=1, 
    n_informative=1, 
    n_targets=1, 
    noise=20, 
    random_state=13
)


Plotted the data to visualize the linear relationship.

Train-Test Split

Split dataset using train_test_split from sklearn.model_selection.

Linear Regression (Baseline)

Applied LinearRegression to train the model.

Coefficient ≈ 28.12, Intercept ≈ -2.27

R² Score = 0.6345

Ridge Regression with Scikit-learn

Imported Ridge from sklearn.linear_model.

Trained with:

alpha = 0 → Same as Linear Regression (Coefficient & Intercept unchanged, R² unchanged).

alpha = 10 → Coefficient decreased to ≈ 24.83, Intercept ≈ -2.21, R² improved slightly (0.6387).

alpha = 100 → Model underfits (coefficients shrink heavily).

Plotted all three regression lines to show the effect of increasing alpha.

Custom Ridge Regression Class (MyRidge)

Implemented Ridge Regression manually.

Constructor Parameters:

alpha (default = 0.1)

Fit Function Steps:

Calculate numerator & denominator similar to OLS, but add alpha to denominator.

Formula ensures regularization impact.

Compute slope (m) and intercept (b):

m = numerator / (denominator + alpha)
b = y.mean() - (m * x.mean())


Verified results by running with alpha = 10 → Same as Scikit-learn’s Ridge Regression output.

🧑‍💻 Technologies Used

Python

NumPy

Matplotlib

Scikit-learn

📊 Key Results

Without Regularization (alpha=0): Ridge = Linear Regression.

With alpha=10: Slight improvement in R², reduced overfitting.

With alpha=100: Underfitting observed.

Custom Implementation: Matches Scikit-learn’s Ridge output.

📌 Takeaways

Ridge Regression works by adding a penalty term (alpha) to the denominator in the coefficient formula.

Increasing alpha reduces variance (overfitting) but too high alpha leads to underfitting.

Custom implementation deepens understanding of how regularization mathematically affects the model.

📷 Visualizations

Scatter plot of dataset.

Regression lines for:

Linear Regression (baseline)

Ridge Regression (alpha=10)

Ridge Regression (alpha=100)
