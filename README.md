# Ridge Regression on 2D Data  

This project demonstrates the concept of **Ridge Regression** (L2 Regularization) on a simple 2D dataset. The implementation includes both **Scikit-learn’s Ridge Regression** and a **custom Ridge Regression class** to understand the math behind it.  

---

## 📌 Project Workflow  

1. **Dataset Creation**  
   - Used `sklearn.datasets.make_regression` to generate synthetic data:  
     ```python
     X, y = make_regression(
         n_samples=100, 
         n_features=1, 
         n_informative=1, 
         n_targets=1, 
         noise=20, 
         random_state=13
     )
     ```
   - Plotted the dataset to check the linear relationship.  

2. **Train-Test Split**  
   - Split the data using `train_test_split` from `sklearn.model_selection`.  

3. **Linear Regression (Baseline)**  
   - Applied `LinearRegression` to train the model.  
   - Coefficient ≈ **28.12**, Intercept ≈ **-2.27**  
   - R² Score = **0.6345**  

4. **Ridge Regression with Scikit-learn**  
   - Imported `Ridge` from `sklearn.linear_model`.  
   - Trained with different `alpha` values:  
     - **alpha = 0** → Same as Linear Regression (no regularization).  
     - **alpha = 10** → Coefficient decreased to ≈ **24.83**, Intercept ≈ **-2.21**, R² improved slightly (**0.6387**).  
     - **alpha = 100** → Model underfits (coefficients shrink a lot).  
   - Plotted all three regression lines to visualize how `alpha` impacts the fit.  

5. **Custom Ridge Regression Class (`MyRidge`)**  
   - Implemented Ridge Regression manually.  
   - **Constructor Parameters:**  
     - `alpha` (default = 0.1)  
   - **Fit Function Logic:**  
     - Numerator and denominator similar to OLS but **add alpha to denominator**.  
     - Formula:  
       ```
       m = numerator / (denominator + alpha)
       b = y.mean() - (m * x.mean())
       ```  
   - Verified results with `alpha = 10` → Same as Scikit-learn’s Ridge Regression (coefficients, intercept, and R²).  

---

## 🧑‍💻 Technologies Used  

- Python  
- NumPy  
- Matplotlib  
- Scikit-learn  

---

## 📊 Key Results  

- **alpha = 0:** Ridge = Linear Regression.  
- **alpha = 10:** Reduced overfitting, slight improvement in R².  
- **alpha = 100:** Model underfits.  
- **Custom Class (`MyRidge`):** Matches Scikit-learn’s Ridge results.  

---

## 📌 Takeaways  

- Ridge Regression reduces overfitting by penalizing large coefficients.  
- Increasing `alpha` lowers variance but too high alpha leads to underfitting.  
- Custom implementation confirms how the regularization term works mathematically.  

---

## 📷 Visualizations  

- Scatter plot of dataset.  
- Regression lines for:  
  - Linear Regression (baseline)  
  - Ridge Regression (`alpha=10`)  
  - Ridge Regression (`alpha=100`)  
