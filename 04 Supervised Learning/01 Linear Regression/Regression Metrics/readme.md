# Regression Metrics

## Mean Absolute Error (MAE)

MAE measures the **average absolute difference** between actual and predicted values.

For a single data point:
- Actual value → yᵢ  
- Predicted value → ŷᵢ  

Absolute error:
```
|yᵢ − ŷᵢ|
```
MAE is computed by taking the average of absolute errors over all data points:
```
MAE = (1 / n) × Σ |yᵢ − ŷᵢ|
```
<img width="533" height="286" alt="Screenshot 2025-12-21 at 7 56 59 PM" src="https://github.com/user-attachments/assets/b1c1545f-8cbd-4206-9fb3-2884e57fffb7" />

#### ✅ Advantages
1. **Same units as output**
   - If predicting Package (LPA), MAE is also in **LPA**
   - Easy to interpret

2. **Robust to outliers**
   - Errors grow linearly, not exponentially
   - Large errors don’t dominate the loss

#### ❌ Disadvantages
- Absolute value function is **not differentiable at 0**
- Makes optimization using **gradient descent difficult**
- Less convenient for mathematical optimization compared to squared error

## Mean Squared Error (MSE)

MSE is similar to MAE, but instead of taking absolute error, it **squares the error**.

For a single data point:
- Actual value → yᵢ  
- Predicted value → ŷᵢ  

Squared error:
```
(yᵢ − ŷᵢ)²
```

MSE is the average of squared errors over all data points:
```
MSE = (1 / n) × Σ (yᵢ − ŷᵢ)²
```

#### Intuition
- Each error is visualized as a **square**
- MSE sums the areas of all these squares
- The model tries to **minimize the total squared area**

<img width="534" height="301" alt="Screenshot 2025-12-21 at 8 01 32 PM" src="https://github.com/user-attachments/assets/97b02ab2-e23b-4d2c-9683-222e36c49ded" />

#### ✅ Advantages
1. **Differentiable everywhere**
   - Makes optimization (gradient descent) easy  
2. Works as a proper **loss function**
3. Strongly penalizes large errors

#### ❌ Disadvantages
1. **Not interpretable**
   - If output is in LPA, MSE is in **(LPA)²**
2. **Penalizes outliers heavily**
3. **Not robust to outliers**

## Root Mean Squared Error (RMSE)

RMSE is simply the **square root of MSE**.

For a dataset with actual values `yᵢ` and predictions `ŷᵢ`:
```
RMSE = √MSE = √[(1 / n) × Σ (yᵢ − ŷᵢ)²]
```

<img width="256" height="122" alt="Screenshot 2025-12-21 at 8 04 16 PM" src="https://github.com/user-attachments/assets/75013f4c-a82f-4a5b-8e45-d5b0bca0181f" />

#### ✅ Advantages
- **Same unit as output**
  - If output is Package (LPA), RMSE is also in **LPA**
- Easy to interpret compared to MSE
- Widely used as a **loss/metric in Deep Learning**

#### ❌ Disadvantages
- **Not robust to outliers**
- Large errors are still penalized heavily

## R² Score (Coefficient of Determination / Goodness of Fit)

R² tells us **how good the regression line fits the data** compared to a dumb baseline (mean line).

<img width="533" height="373" alt="Screenshot 2025-12-21 at 8 09 57 PM" src="https://github.com/user-attachments/assets/f94b338b-f90a-4694-bc21-1253f15cb8d0" />

```
R² = 1 − (SSR / SSM)
```
Where:
- **SSR** → Sum of Squared Residuals  
  (error made by the regression line)
- **SSM** → Sum of Squared deviations from Mean  
  (error made by the mean line)

#### 🔹 Intuition (Regression Line vs Mean Line)

- **Mean line** → predicts the same value (ȳ) for every point  
- **Regression line** → tries to do better using input features  

R² measures **how much better regression is compared to just predicting the mean**.

#### 🔹 R² Values Interpretation

✅ R² = 1
- SSR = 0  
- Regression line makes **zero error**
- Perfect fit (dream scenario)

⚠️ R² = 0
- SSR = SSM  
- Regression line and mean line make **same error**
- Model is **useless**

❌ R² < 0
- SSR > SSM  
- Regression line performs **worse than mean**
- Model is trash (usually happens when fitting linear model on highly non-linear data)

##### 🔹 Desired Direction
- We always want **R² → 1**
- Higher R² = better explanation of data variance

### 🔹 Variance Explanation Interpretation

Another powerful way to understand R²:

> **R² = percentage of variance in output explained by input features**

Example:
- R² = 0.80  
- CGPA explains **80% of variance** in Package  
- Remaining 20% is due to:
  - Other factors
  - Noise
  - Unmodeled variables

Multiple Features Example:
- Inputs: CGPA + IQ  
- R² = 0.80  
- Together, CGPA and IQ explain **80% of variance in Package**


## Adjusted R² Score

Adjusted R² fixes the **major flaw of R²** in multiple linear regression.

#### Flaw in R²
R² **never decreases** when we add more input features.

Example:
- Model: CGPA → Package  
  R² = 0.80

- Add a useful feature (IQ):  
  R² = 0.90 ✅ (good)

- Add an irrelevant feature (Temperature):  
  R² may **increase or stay same** ❌  
  even though the feature adds **no real value**

👉 This makes plain R² **misleading**.

#### 🔹 Adjusted R² (Fixes This Problem)

Adjusted R² **penalizes unnecessary features**.

Formula :
```
Adjusted R² = 1 − (1 − R²) × (n − 1) / (n − k − 1)
```

<img width="1024" height="526" alt="image" src="https://github.com/user-attachments/assets/fd91b147-745f-49a2-9f9c-195474743c6d" />

Where:
- R² → original R² score  
- n → number of data points (rows)  
- k → number of independent features  

#### 🔹 How It Behaves
- If a **useful feature** is added → Adjusted R² **increases**
- If an **irrelevant feature** is added → Adjusted R² **decreases**
- If feature adds nothing → Adjusted R² may stay same or drop

#### Example:
- Add **IQ** → Adjusted R² ↑ ✅  
- Add **Temperature** → Adjusted R² ↓ ❌  

#### 🔹 Why Adjusted R² is Important
- Prevents fake improvement in model quality  
- Encourages **meaningful features only**  
- Best metric for **Multiple Linear Regression**
- Use **Adjusted R²** when:
  - Multiple input features exist
  - Feature selection matters

🔥 If R² ↑ but Adjusted R² ↓ → you added garbage features.

