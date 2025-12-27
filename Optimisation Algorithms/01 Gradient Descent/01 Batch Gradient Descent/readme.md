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
L = (1/n) * Σ (yᵢ − ŷᵢ)²
```

Where:
```
ŷᵢ = β₀ + β₁x₁ᵢ + β₂x₂ᵢ
```

<img width="478" height="273" alt="Screenshot 2025-12-27 at 1 43 09 PM" src="https://github.com/user-attachments/assets/5bc98917-cff5-4800-a2b3-ea866245f04f" />

So:
```
L = L(β₀, β₁, β₂)
```

<img width="513" height="326" alt="Screenshot 2025-12-27 at 1 18 15 PM" src="https://github.com/user-attachments/assets/7bbdce6a-aee4-4cd3-80e7-5beaeac5fc70" />

This loss depends on **three parameters**.

### 🔹 Loss Surface
- Parameters → (β₀, β₁, β₂)
- Loss → L

This forms a **4D surface** (3 parameters + loss).

<img width="512" height="351" alt="Screenshot 2025-12-27 at 1 15 29 PM" src="https://github.com/user-attachments/assets/c0c66c30-0467-44ca-a081-82e7d432eeb0" />

3. Step 3 — Compute Gradients
We compute **partial derivatives** (gradients):
```
∂L/∂β₀
∂L/∂β₁
∂L/∂β₂
```

<img width="526" height="327" alt="Screenshot 2025-12-27 at 1 22 53 PM" src="https://github.com/user-attachments/assets/b99fac9f-22b0-4d79-b4ae-bb4e08e0ae7f" />

<img width="502" height="310" alt="Screenshot 2025-12-27 at 1 29 43 PM" src="https://github.com/user-attachments/assets/8737bcfd-b4bb-4335-8cc9-fab6f7fbea3e" />

<img width="504" height="339" alt="Screenshot 2025-12-27 at 1 32 13 PM" src="https://github.com/user-attachments/assets/3940565e-23c6-4b7e-b3df-7f0c8bed5b97" />

```
∂L / ∂βₘ = −(2/n) Σ (yᵢ − ŷᵢ) xᵢₘ
```

- `βₘ` → coefficient of the m-th feature

- `xᵢₘ` → value of the m-th feature for the i-th data point

- `(yᵢ − ŷᵢ)` → residual (error)

- Sum is taken over all data points

<img width="503" height="241" alt="Screenshot 2025-12-27 at 1 35 10 PM" src="https://github.com/user-attachments/assets/c673e6b9-aba9-4a6c-99ef-36b47e804c14" />

<img width="508" height="314" alt="Screenshot 2025-12-27 at 1 47 35 PM" src="https://github.com/user-attachments/assets/faeeb48c-6541-496b-8f90-bcd95ffa1a1b" />

<img width="494" height="368" alt="Screenshot 2025-12-27 at 1 59 43 PM" src="https://github.com/user-attachments/assets/d4f3c183-aec6-487f-8c94-a2643c033599" />

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
