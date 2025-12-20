# Simple Linear Regression

<img width="313" height="233" alt="Screenshot 2025-12-20 at 5 13 09 PM" src="https://github.com/user-attachments/assets/53b90ed8-f00e-4729-b27c-714ac569d4ea" />

<img width="534" height="286" alt="Screenshot 2025-12-20 at 5 16 43 PM" src="https://github.com/user-attachments/assets/e2050c66-64d8-425c-a6b7-5bd087d6ffc8" />

Intuition:

Linear Regression finds the **best-fit line**:
```
y = m x + b
```

For example:
```
Package = m × CGPA + b
```

This equation represents the **mathematical relationship** between CGPA and Package.

#### 🔹 Meaning of Parameters

**m (Slope / Weight)**
- Tells how much **Package changes when CGPA changes by 1 unit**
- Measures **dependency of output on input**

Interpretation:
- Small `m` → Package depends **less** on CGPA  
- Large `m` → Package depends **more** on CGPA  

So `m` controls the **importance / weightage** of CGPA.

**b (Intercept / Bias)**
- Value of `y` when `x = 0`
- Represents the **baseline output**

Interpretation:
- Even if CGPA were zero, `b` is the predicted Package
- Helps position the line correctly on the graph

---

# 📐 Simple Linear Regression (Mathematical Foundation)

## How do we find `m` and `b`?

We want to find the **best-fit line**:

y = m x + b

Such that the error between actual and predicted values is minimum.

#### Two Ways to Find `m` and `b`

**1. Closed Form Solution (Exact Solution)**
- Uses a **direct mathematical formula**
- Also called **Ordinary Least Squares (OLS)**
- Used internally by **sklearn LinearRegression**
- Best for **small number of features**

This method directly computes optimal `m` and `b`.

**2. Non-Closed Form Solution (Approximate Solution)**
- Uses **iterative optimization**
- Based on **differentiation**
- Uses **Gradient Descent**
- Best for **large / high-dimensional data**

In sklearn:
- `SGDRegressor` uses gradient descent

### 🔹 Formula for Simple Linear Regression

Let:
- x = CGPA (input)
- y = Package (output)

**Slope (m)**
```python
m = Σ (xi − x̄)(yi − ȳ)  /  Σ (xi − x̄)²
```

**Intercept (b)**
```python
b = ȳ − m x̄
```

<img width="523" height="283" alt="Screenshot 2025-12-20 at 5 34 19 PM" src="https://github.com/user-attachments/assets/959ff157-6f8f-43c6-a769-9bde83624ac5" />

#### 🔹 Steps to Compute

1. Compute mean of x → x̄  
2. Compute mean of y → ȳ  
3. Use the formula to calculate `m`  
4. Substitute `m` to compute `b`

---

# Best Fit Line & Error Minimization

The best-fit line is the line that tries to pass **as close as possible to all data points**.

- It minimizes the **distance between the line and every point**
- The goal is NOT to pass exactly through every point, but to minimize overall error

### 🔹 Error / Residual
For a data point:

- Actual value → yi  
- Predicted value → ŷi  

Residual (error):
```python
di = yi − ŷi
```

<img width="537" height="306" alt="Screenshot 2025-12-20 at 6 12 58 PM" src="https://github.com/user-attachments/assets/f2782ce1-aa15-4de1-9f59-ff5aef285ed1" />

This shows how far the prediction is from the actual value.

#### 🔹 Total Error (Loss Function)
If we simply add errors, positive and negative errors cancel out.

So we **square the errors** and sum them:
```python
Total Error = Σ (di)²
```

This is called:
- **Error function**
- **Loss function**
- **Cost function**
- Represented as **J**

<img width="510" height="304" alt="Screenshot 2025-12-20 at 6 10 43 PM" src="https://github.com/user-attachments/assets/f771e62e-5059-42a3-9710-13e9ae0a31cb" />

### 🔹 Why Square the Error (Why NOT Modulus)?

#### ❌ Why not |error| ?
1. Absolute value is **not differentiable at 0**
2. We cannot optimize it using calculus easily

<img width="675" height="1088" alt="image" src="https://github.com/user-attachments/assets/14931505-f531-4751-b197-c21dcf97fc05" />

#### ✅ Why square?
1. Squaring penalizes **outliers more**
2. Squared error is **differentiable everywhere**
3. Makes optimization mathematically simple

## 🔹 Error Function in Terms of m and b

Predicted value:
```python
ŷi = mxi + b
```

So error becomes:
```python
Error(m, b) = Σ (yi − (mxi + b))²
```

<img width="535" height="383" alt="Screenshot 2025-12-20 at 6 16 22 PM" src="https://github.com/user-attachments/assets/93f6f784-740c-4ef2-97a3-1a1f1eb0d378" />

Now the error depends on **m and b**.

Our goal:
> Find values of `m` and `b` that **minimize this error**

## 🔹 Understanding m and b Separately

### Case 1: Fix b = 0, vary m
```python
Error(m) = Σ (yi − mxi)²
```

- Only slope changes
- Line rotates but does not shift up/down

<img width="526" height="273" alt="Screenshot 2025-12-20 at 6 20 22 PM" src="https://github.com/user-attachments/assets/af588122-6a47-4cb3-ba52-160f26054143" />

### Case 2: Fix m = 1, vary b
```python
Error(b) = Σ (yi − xi − b)²
```

- Only intercept changes
- Line shifts up/down but slope stays same

<img width="513" height="309" alt="Screenshot 2025-12-20 at 6 22 03 PM" src="https://github.com/user-attachments/assets/3e0f2f0c-9bca-43cb-96cd-e0066c7225fd" />

### Case 3: Vary both m and b
- Error becomes a **3D surface**
- x-axis → m  
- y-axis → b  
- z-axis → error  

We need the **minimum point** on this surface.

<img width="531" height="301" alt="Screenshot 2025-12-20 at 6 24 17 PM" src="https://github.com/user-attachments/assets/89c31d45-bf7a-42e1-84a2-99a2cc34a93c" />

## 🔹 Optimization Using Partial Derivatives
To find minimum error:
```python
∂Error / ∂m = 0
∂Error / ∂b = 0
```

## 🔹 Solving for b
Differentiate error w.r.t b and solve:
```python
b = ȳ − m x̄
```

Where:
- x̄ = mean of x
- ȳ = mean of y

<img width="512" height="289" alt="Screenshot 2025-12-20 at 6 26 58 PM" src="https://github.com/user-attachments/assets/af5a74b6-ecab-41d0-994c-e77d3dca33ec" />

---

## 🔹 Solving for m
Substitute value of b into error function  
Differentiate w.r.t m and solve:
```python
m = Σ (xi − x̄)(yi − ȳ) / Σ (xi − x̄)²
```

<img width="353" height="203" alt="Screenshot 2025-12-20 at 6 29 12 PM" src="https://github.com/user-attachments/assets/6b28995e-0fb2-46bf-8c47-1dce5240f494" />

<img width="366" height="339" alt="Screenshot 2025-12-20 at 6 29 47 PM" src="https://github.com/user-attachments/assets/85aa9d2f-1a9d-4cd4-afde-24f33fdcaaaf" />

<img width="362" height="206" alt="Screenshot 2025-12-20 at 6 30 22 PM" src="https://github.com/user-attachments/assets/faa76b29-e719-4045-91ea-ed2384bc873a" />

### 🔹 Final Best-Fit Line
Once m and b are found:
```python
y = mx + b
```

This line:
- Minimizes total squared error
- Is the **best possible straight line** for the data

