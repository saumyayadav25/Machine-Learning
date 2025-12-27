# Regularization

Regularization is a technique used to **prevent overfitting** by **penalizing large model coefficients**.

#### What is Overfitting?
Overfitting occurs when:
- Model performs **very well on training data**
- But performs **poorly on test / unseen data**
- Model learns **noise instead of pattern**
- Variance becomes very high

### 🔹 Why Coefficients Matter (Intuition)

In Linear Regression:
```
y = mx + b
```

- If **m is very large** →  
  y depends too much on x → model becomes very sensitive → **overfitting**

- If **m ≈ 0** →  
  y barely depends on x → model is too simple → **underfitting**

👉 So controlling the value of `m` (and other coefficients) is critical.

### What Regularization Does
- Adds a **penalty term** to the loss function
- Penalizes **large coefficient values**
- Forces the model to stay **simple and stable**

### 🔹 Types of Regularization

- Ridge Regression (L2 Regularization)

- LASSO Regression (L1 Regularization)

- Elastic Net (L1 + L2)
