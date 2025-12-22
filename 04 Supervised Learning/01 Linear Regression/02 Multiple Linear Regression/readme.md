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

---

# Mathematical Formulation

#### Example
Inputs:
- CGPA → x₁
- IQ → x₂
- Gender → x₃  

Output:
- LPA → y  

So each data point lies in **4D space** (3 inputs + 1 output).

### 🔹 Model Equation (Scalar Form)

For a single data point:
```
ŷ = β₀ + β₁x₁ + β₂x₂ + β₃x₃
```
Where:
- β₀ → intercept (bias)
- β₁, β₂, β₃ → weights of input features

#### 🔹 Dataset Shape
Suppose:
- Number of students = n (e.g., 100)
- Number of input features = m (e.g., 3)

<img width="490" height="215" alt="Screenshot 2025-12-22 at 7 39 16 PM" src="https://github.com/user-attachments/assets/d509ec56-03cd-42c5-960c-36585c36b45e" />

Then:
- Feature matrix X → shape (n, m+1)  
  (extra 1 column for bias term)
- Target vector y → shape (n, 1)

<img width="490" height="344" alt="Screenshot 2025-12-22 at 7 41 52 PM" src="https://github.com/user-attachments/assets/1515ed07-e325-45ac-8469-7bddc50ef195" />


Example:
```
X → (100, 4)
y → (100, 1)
```

## 🔹 Matrix Representation

#### Feature Matrix (X)
```
X = [ 1 x11 x12 x13
1 x21 x22 x23
...
1 xn1 xn2 xn3 ]
```

(The first column of 1s is for β₀)

#### Coefficient Matrix (β)
```
β = [ β₀
β₁
β₂
β₃ ]
```

### Predicted Output (Ŷ)
```
Ŷ = X · β
```

<img width="450" height="230" alt="Screenshot 2025-12-22 at 7 44 27 PM" src="https://github.com/user-attachments/assets/cb941830-67a0-4899-bb75-2bcd94b9d283" />

This gives predictions for **all n samples at once**.

So:
- ŷ₁ = β₀ + β₁x₁₁ + β₂x₁₂ + β₃x₁₃
- ŷ₂ = β₀ + β₁x₂₁ + β₂x₂₂ + β₃x₂₃
- ...
- ŷₙ = β₀ + β₁xₙ₁ + β₂xₙ₂ + β₃xₙ₃

### 🔹 Error / Residual Vector

For each sample:
```
eᵢ = yᵢ − ŷᵢ
```

For all samples:
```
E = y − Ŷ
```
<img width="358" height="210" alt="Screenshot 2025-12-22 at 7 46 30 PM" src="https://github.com/user-attachments/assets/b45b0f9b-80d4-42f2-af79-15dea3663913" />

### 🔹 Error Function (Loss)

For Multiple Linear Regression, the loss is:
```
Loss = Eᵀ · E
```

This represents the **sum of squared errors** over all data points.

<img width="469" height="134" alt="Screenshot 2025-12-22 at 7 50 54 PM" src="https://github.com/user-attachments/assets/dd2b6908-3b19-47d0-b3a4-f0b43016c023" />

<img width="480" height="258" alt="Screenshot 2025-12-22 at 7 52 05 PM" src="https://github.com/user-attachments/assets/afd03b45-4ac4-4e75-97d5-804234f3c63c" />

<img width="450" height="256" alt="Screenshot 2025-12-22 at 7 53 39 PM" src="https://github.com/user-attachments/assets/633b2ae6-9e06-4413-8a57-a14f36f54c1f" />

<img width="491" height="304" alt="Screenshot 2025-12-22 at 7 56 32 PM" src="https://github.com/user-attachments/assets/1dad553a-84e4-41d8-8e1a-18ac013ca37c" />

<img width="507" height="325" alt="Screenshot 2025-12-22 at 7 59 00 PM" src="https://github.com/user-attachments/assets/7f0f29f9-1398-4a1f-83cf-bcd17851fac0" />

<img width="504" height="302" alt="Screenshot 2025-12-22 at 8 01 22 PM" src="https://github.com/user-attachments/assets/1f96577c-af64-4cab-95aa-c373c0701b64" />

<img width="386" height="301" alt="Screenshot 2025-12-22 at 8 01 55 PM" src="https://github.com/user-attachments/assets/de9c0ba5-8052-4f26-a064-b1fda6e86de6" />

<img width="500" height="329" alt="Screenshot 2025-12-22 at 8 03 35 PM" src="https://github.com/user-attachments/assets/0d2eb541-6e18-4409-bcc9-b1cbf61578d1" />

<img width="515" height="282" alt="Screenshot 2025-12-22 at 8 04 24 PM" src="https://github.com/user-attachments/assets/e15fd2bd-a775-4296-9f3f-7a11d22f6e79" />
