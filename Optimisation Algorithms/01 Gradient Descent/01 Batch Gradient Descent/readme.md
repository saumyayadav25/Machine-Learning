# Batch Gradient Descent (BGD)

<img width="530" height="334" alt="Screenshot 2025-12-24 at 8 32 24 PM" src="https://github.com/user-attachments/assets/2e4958bb-bff6-4916-9833-01577e01a84c" />

- Computes the **gradient using the entire dataset**
- Parameters (`m`, `b`, or β) are updated **once per epoch**
- Uses exact gradient → stable updates

#### ❌ Disadvantages
- **Very slow** for large datasets
- High memory usage
- Not scalable

#### ✅ When Used
- Dataset is **small**
- Loss function is **convex**
- Exact convergence is required

👉 The Gradient Descent we studied was **Batch GD**.

### 🔹 Stochastic Gradient Descent (SGD)
- Gradient is computed using **only one data point**
- Parameters are updated **after every row**

- Much **faster**
- Less memory usage
- Can escape saddle points and shallow local minima

👉 Because of speed, **SGD is used more often** in practice.

### 🔹 Mini-Batch Gradient Descent
- A **balance between Batch and SGD**
- Uses a **small batch of data** to compute gradient

Example
- Total rows = 300  
- Batch size = 30  

Then:
- 300 / 30 = **10 updates per epoch**

Comparison:
- Batch GD → 1 update per epoch  
- SGD → 300 updates per epoch  
- Mini-Batch → 10 updates per epoch  

#### ✅ Advantages
- Faster than Batch GD
- More stable than SGD

| Method        | Data Used per Update | Speed | Stability |
|--------------|---------------------|-------|-----------|
| Batch GD     | Full dataset        | Slow  | High      |
| SGD          | 1 row               | Fast  | Low       |
| Mini-Batch   | Small batch         | Fast  | Medium    |


## Extension to Higher Dimensions
Earlier:
```
y = mx + b
```

Now (multiple features):
```
y = β₀ + β₁x₁ + β₂x₂ + β₃x₃
```

Rule:
- If input has `n` features  
- Total parameters to learn = **n + 1** (including intercept)

Example:
- CGPA, IQ, Gender → 3 features  
- Parameters → β₀, β₁, β₂, β₃

# Mathematical Formulation (Multiple Linear Regression)

(with only 2 rows)
Inputs:
- CGPA → x₁
- IQ → x₂  

Output:
- LPA → y  

Model:
```
y = β₀ + β₁x₁ + β₂x₂
```

Goal:
> Find optimal values of **β₀, β₁, β₂** that minimize the loss.

1. **Step 1 — Initialize Parameters**
Start with random / default values:
```
β₀ = 0 (intercept usually initialized to 0)
β₁ = 1
β₂ = 1
```

2. **Step 2 — Define Loss Function**
Using Mean Squared Error (without 1/n for simplicity):
```
L = Σ (yᵢ − ŷᵢ)²
```

Where:
```
ŷᵢ = β₀ + β₁x₁ᵢ + β₂x₂ᵢ
```

So:
```
L = L(β₀, β₁, β₂)
```

This loss depends on **three parameters**.

### 🔹 Loss Surface
- Parameters → (β₀, β₁, β₂)
- Loss → L

This forms a **4D surface** (3 parameters + loss).

<img width="528" height="345" src="https://github.com/user-attachments/assets/78f21a03-fecf-434e-81b9-f2b639e0f819" />

3. Step 3 — Compute Gradients
We compute **partial derivatives** (gradients):
```
∂L/∂β₀
∂L/∂β₁
∂L/∂β₂
```

Each gradient tells:
> How much the loss changes if that parameter changes.

4. Step 4 — Gradient Descent Updates
Choose:
```
epochs = 100
learning rate (η) = 0.1
```

Update rules:
```
β₀ = β₀ − η × (∂L/∂β₀)
β₁ = β₁ − η × (∂L/∂β₁)
β₂ = β₂ − η × (∂L/∂β₂)
```

All parameters are updated **simultaneously**.

5. Step 5 — Iterate
Repeat updates for all epochs:

for each epoch:

compute gradients
```
update β₀, β₁, β₂
```
