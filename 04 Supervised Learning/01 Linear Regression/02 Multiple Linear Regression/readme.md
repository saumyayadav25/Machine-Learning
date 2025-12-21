# Multiple Linear Regression

Multiple Linear Regression is a **supervised ML algorithm** where:
- There are **multiple input features**
- And **one numerical output feature**

### 🔹 Example
Inputs:
- CGPA (x₁)
- IQ (x₂)

Output:
- Placement Package (y)

So the data becomes **3D**.

### 🔹 Geometric Intuition
- Simple Linear Regression (1 input) → **line**
- Multiple Linear Regression (2 inputs) → **plane**
- 3 or more inputs → **hyperplane**

As dimensions increase, we no longer visualize, but the math remains the same.

### 🔹 Mathematical Equation

<img width="475" height="297" alt="Screenshot 2025-12-21 at 8 39 19 PM" src="https://github.com/user-attachments/assets/76f8e4a4-d0ca-40f9-a391-e7bf91a459b7" />

For 2 input features:
```
y = β₀ + β₁x₁ + β₂x₂
```

For 3 input features:
```
y = β₀ + β₁x₁ + β₂x₂ + β₃x₃
```

For `n` input features:
```
y = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ
```

Where:
- β₀ → intercept (bias / offset)
- β₁, β₂, ..., βₙ → weights (importance of features)

#### 🔹 Interpretation

Example:
```
LPA = β₀ + β₁(CGPA) + β₂(IQ)
```

- **β₁** → how much CGPA contributes to LPA  
- **β₂** → how much IQ contributes to LPA  

If:
```
β₁ > β₂
```

→ CGPA is more important than IQ in predicting LPA.

🔹 Meaning of β₀ (Intercept)
- Output value when all inputs are zero
- Acts as a **baseline / offset**
- Helps position the hyperplane correctly
