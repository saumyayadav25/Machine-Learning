# Stochastic Gradient Descent (SGD)

SGD is introduced to fix the **scalability and performance problems of Batch Gradient Descent**.

### 🔴 Problems with Batch Gradient Descent

1. Heavy Computation
Assume:
- Number of rows (n) = 1000  
- Number of features = 5  
- Total coefficients = 6 (including intercept)  
- Epochs = 50  

Then:
- For **one coefficient** → 1000 derivatives per epoch  
- For **6 coefficients** → 6000 derivatives per epoch  
- Over 50 epochs → **300,000 derivative computations**

👉 As data grows, computation becomes **very slow**.

2. Memory Limitation
- Batch GD requires the **entire X_train matrix in memory**
- For large datasets, this may **not fit into RAM**
- Vectorized operations fail for very large data

👉 Not practical for big datasets.

### ✅ Solution: Stochastic Gradient Descent

### 🔹 Core Idea
- Instead of using **all rows** to compute gradient,
- Use **only one randomly chosen row** to update coefficients.

### 🔹 How SGD Works
- For each data point:
  - Compute gradient using **one row**
  - Update coefficients immediately
- If there are `n` rows:
  - **n updates per epoch**

```
for each epoch:
shuffle data
for each row:
compute gradient using that row
update coefficients
```

#### 🔹 Why SGD is Faster
- Each update is **cheap**
- Requires **fewer epochs**
- Reaches a good solution faster (not exact, but close)

👉 Faster convergence in practice.

#### 🔹 Hardware Advantage
- Processes **one row at a time**
- Even if dataset is **1 GB**, only one row is loaded
- No need to store full dataset in RAM

👉 Memory-efficient and scalable.

## 🔹 Why It’s Called *Stochastic*
- Rows are picked **randomly**, not sequentially
- Updates have **randomness**
- Hence:
  - Path to minimum is noisy
  - Final solution may differ every run

👉 SGD does **not give a static exact solution**.

## ⏱️ Time Comparison: Batch GD vs Stochastic GD

Assume:
- Number of epochs = e = 100  
- Number of rows = n  

Batch Gradient Descent
- **Updates per epoch** = 1  
- **Total updates** = e = 100  

👉 If epochs are fixed, **Batch GD performs fewer updates**.

Stochastic Gradient Descent
- **Updates per epoch** = n  
- **Total updates** = e × n  

👉 Much larger number of updates.

### ⚠️ Important Clarification
- If **epochs are fixed and equal**, **Batch GD is faster per training run**
- But in practice:
  - Batch GD needs **many more epochs** to converge
  - SGD converges in **fewer epochs**

<img width="365" height="256" alt="Screenshot 2025-12-27 at 4 05 31 PM" src="https://github.com/user-attachments/assets/e63850ee-2375-4a35-8269-81f8840cc574" />

## ✅ When to Use Stochastic Gradient Descent (SGD)

1. Large Datasets
- Dataset is very large
- Batch GD becomes slow and memory-heavy
- SGD processes **one row at a time**

👉 Scales well with big data.

🔹 Faster Convergence (In Practice)
- SGD makes frequent updates
- Reaches a **good solution quickly**
- Needs fewer epochs than Batch GD

2. Non-Convex Loss Functions
- Batch GD may get stuck at:
  - Local minima
  - Saddle points
- SGD’s randomness helps:
  - Escape local minima
  - Move out of flat regions

#### 🔹 Important Caution
- Learning rate must be **carefully tuned**
- High learning rate → divergence
- Low learning rate → slow learning

### 🔹 Disadvantages of SGD
- Loss does not decrease smoothly
- More variance in updates
- Never settles exactly at minimum (keeps oscillating around it)

## 📉 Learning Rate Schedule

A learning rate schedule means **changing the learning rate over time** instead of keeping it constant.

The learning rate is made a **function of epochs**.

<img width="425" height="192" alt="Screenshot 2025-12-27 at 4 35 54 PM" src="https://github.com/user-attachments/assets/cedb0a29-7343-4f3a-bd31-79418f5747fb" />

Why Use Learning Rate Scheduling?
- Large learning rate helps move **fast initially**
- Small learning rate helps **fine-tune near the minimum**
- Prevents overshooting and oscillations

> Basic Idea
As epochs increase:
```
learning rate ↓
```

## 🔹 Example
Assume:
- Epochs = 100

Learning rate progression:
```
Epoch 1 → η = 0.1
Later → η = 0.03
```
So after some iterations, the step size becomes smaller.

#### 🔹 Common Learning Rate Schedules
- **Time-based decay**  
  η decreases gradually with epochs
- **Step decay**  
  η drops after fixed number of epochs
- **Exponential decay**  
  η decreases exponentially
- **Adaptive methods**  
  (Adam, RMSProp adjust η automatically)
