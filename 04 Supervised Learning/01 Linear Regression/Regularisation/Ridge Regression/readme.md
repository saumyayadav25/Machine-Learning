# Ridge Regression (L2 Regularization)

Ridge Regression is Linear Regression with an **L2 penalty** added to control overfitting.

## 🔹 Loss Function
```
L = Σ (yᵢ − ŷᵢ)² + λ m²
```

- First term → data fit (MSE)
- Second term → penalty on model complexity

If there are multiple features:

```
L = Σ (yᵢ − ŷᵢ)² + λ (m₁² + m₂² + m₃² + ...)
```

### 🔹 Why It’s Called **L2**
- Coefficients are **squared**
- Squaring + summing = **L2 norm**
- Penalizes large weights heavily

### 🔹 Role of λ (Lambda)
- λ ∈ [0, ∞)
- **Hyperparameter** → must be tuned

Effects:
- λ = 0 → normal Linear Regression
- λ ↑ → coefficients shrink
- λ → ∞ → coefficients → 0 (underfitting)

### 🔹 Bias–Variance Tradeoff
- Ridge **increases bias slightly** (may not perform well on training data)
- Ridge **reduces variance significantly**
- Net effect → better generalization

👉 This is exactly what we want when overfitting happens.

### 🔹 What Ridge Does (Important)
- Shrinks coefficients **towards zero**
- **Never makes them exactly zero**
- Does **NOT perform feature selection**

All features remain in the model.

<img width="584" height="427" alt="Screenshot 2025-12-28 at 6 05 55 PM" src="https://github.com/user-attachments/assets/ecd2291a-faef-48fc-9642-5679dbc2e7ca" />

---

# Mathematical Formulation (Single Feature)

For simple linear regression with regularization:
```
L = Σ (yᵢ − m xᵢ − b)² + λ m²
```
Where:
- m → slope
- b → intercept
- λ → regularization parameter (λ ≥ 0)

1. Step 1: Differentiate w.r.t `b`
Set derivative to zero:
```
∂L/∂b = 0
```

Solving gives the same result as Linear Regression:
```
b = ȳ − m x̄
```

Where:
- x̄ → mean of x
- ȳ → mean of y

👉 **Important:** Regularization does NOT affect `b`.

2. Step 2: Substitute `b` into Loss
Substitute `b = ȳ − m x̄` into the loss:
```
L = Σ (yᵢ − m xᵢ − ȳ + m x̄)² + λ m²
```

Now the loss depends **only on `m`**.

## 🔹 Step 3: Differentiate w.r.t `m`
Set derivative to zero:
```
∂L/∂m = 0
```

After simplification, we get:
```
m = Σ (xᵢ − x̄)(yᵢ − ȳ) / [ Σ (xᵢ − x̄)² + λ ]
```

<img width="505" height="330" alt="Screenshot 2025-12-28 at 6 20 24 PM" src="https://github.com/user-attachments/assets/00738a72-4eae-4361-8192-b15e106f1daa" />

<img width="509" height="305" alt="Screenshot 2025-12-28 at 6 21 08 PM" src="https://github.com/user-attachments/assets/5e331256-dba8-469a-8c11-6bfc8f875a80" />

<img width="507" height="274" alt="Screenshot 2025-12-28 at 6 21 43 PM" src="https://github.com/user-attachments/assets/62b71bc3-2ed8-484a-82ca-fb83882425df" />

<img width="469" height="330" alt="Screenshot 2025-12-28 at 6 25 08 PM" src="https://github.com/user-attachments/assets/8cea5d61-d03e-4a63-bb5b-82fd9db01472" />

### 🔹 Compare with Linear Regression

**Linear Regression:**
```
m = Σ (xᵢ − x̄)(yᵢ − ȳ) / Σ (xᵢ − x̄)²
```

**Ridge Regression:**
```
m = Σ (xᵢ − x̄)(yᵢ − ȳ) / [ Σ (xᵢ − x̄)² + λ ]
```

#### 🔹 Effect of λ (Lambda)

- λ = 0 → Ridge becomes **Linear Regression**
- λ ↑ → denominator ↑ → **m decreases**
- Large λ → slope shrinks toward 0

👉 Larger λ ⇒ **less dependence on x ⇒ less overfitting**

# Mathematical Formulation for n-Dimensional Data

#### 🔹 Problem Setup
- Inputs: x₁, x₂, x₃, …, xₙ  
- Output: y  
- Dataset:
  - m rows (samples)
  - n + 1 columns (n features + intercept)

Let:
- Feature matrix → X (m × n)
- Target vector → y (m × 1)
- Weight vector → w = [w₁, w₂, …, wₙ]ᵀ

(Intercept is usually handled separately and **not regularized**.)

#### Normal Linear Regression (Matrix Form)

Loss function:
```
L = Σ (y − ŷ)²
```

Matrix form:
```
L = (Xw − y)ᵀ (Xw − y)
```

<img width="546" height="362" alt="Screenshot 2025-12-28 at 8 09 19 PM" src="https://github.com/user-attachments/assets/e7a43125-d418-4c62-a278-17d6b2a01213" />

#### 🔹 Ridge Regression Loss (L2 Regularization)

Add penalty on weights:
```
L = (Xw − y)ᵀ (Xw − y) + λ ||w||²
```

Where:
```
||w||² = wᵀw
```

So:
```
L = (Xw − y)ᵀ (Xw − y) + λ wᵀw
```

#### Expand the Loss Function
```
L = wᵀXᵀXw − 2wᵀXᵀy + yᵀy + λ wᵀw
```

This is still a **convex function**, so a unique global minimum exists.

<img width="555" height="300" alt="Screenshot 2025-12-28 at 9 35 29 PM" src="https://github.com/user-attachments/assets/ad37dbd2-ac8c-4bbf-838f-c1e493ebcc67" />

<img width="559" height="358" alt="Screenshot 2025-12-28 at 9 36 44 PM" src="https://github.com/user-attachments/assets/a872a5d3-9676-4660-8ad5-dadd9a723d27" />

#### 🔹 Differentiate w.r.t `w`
Take gradient and set it to zero:
```
∂L/∂w = 2XᵀXw − 2Xᵀy + 2λw = 0
```

Divide by 2:
```
XᵀXw + λw = Xᵀy
```

Factor out `w`:
```
(XᵀX + λI) w = Xᵀy
```

### 🔹 Closed-Form Solution (Normal Equation for Ridge)

```
w = (XᵀX + λI)⁻¹ Xᵀy
```

Where:
- I → identity matrix
- λI ensures numerical stability

<img width="525" height="275" alt="Screenshot 2025-12-28 at 9 45 19 PM" src="https://github.com/user-attachments/assets/19f90d45-739f-44d7-bd92-caea2c9c86e0" />

#### Compare with Linear Regression

**Linear Regression:**
```
w = (XᵀX)⁻¹ Xᵀy
```

**Ridge Regression:**
```
w = (XᵀX + λI)⁻¹ Xᵀy
```

👉 Ridge adds **λI** to avoid large coefficients and matrix singularity.

