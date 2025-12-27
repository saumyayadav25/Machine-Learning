# Polynomial Regression

When the data shows a **non-linear relationship**, a straight line (Linear Regression) does not perform well.

Instead of changing the algorithm, we **extend Linear Regression by adding polynomial terms**.

## 🔹 Core Idea
- Use the **same Linear Regression model**
- But **increase the power of input features**

This allows the model to capture **non-linear patterns**.

**Example**

Original feature:
```
x
```

After polynomial expansion:
```
x, x², x³, ...
```

Model becomes:
```
y = β₀ + β₁x + β₂x²
```

<img width="508" height="340" alt="Screenshot 2025-12-27 at 7 55 44 PM" src="https://github.com/user-attachments/assets/f119d541-1b0e-40c2-a9d7-bbafe7f55153" />

#### 🔹 Important Clarification
- The relationship between **y and x** is **non-linear**
- But the relationship between **y and coefficients (β₀, β₁, β₂)** is **linear**

👉 That’s why it is called: **Polynomial Linear Regression**

#### 🔹 Why It Works
- Polynomial terms help model **curves**
- Extracts non-linear relationships from data
- Uses the same optimization techniques (OLS / GD)

#### 🔹 Geometric Intuition
- Linear Regression → straight line  
- Polynomial Regression → curve  
- Still solved using **Linear Regression machinery**