# MICE - Multivariate Imputation by Chained Equations

MICE fills missing values by **building a separate model for each feature** that has missing data, using all other features to predict it.  
It works **iteratively** until predictions stabilize.

## 🧩 Assumptions for MICE
- Works best when data is **MAR (Missing At Random)**.

### Types of Missingness
- **MCAR** → Missing Completely at Random  
- **MAR** → Missing At Random  
- **MNAR** → Missing Not At Random 

### ⭐ Advantages
- Very **accurate** (uses relationships between features).  
- Preserves **covariance** and feature interactions.

### ⚠️ Disadvantages
- **Slow** (runs multiple regression models repeatedly).  
- Requires storing the **entire training dataset** in memory during deployment → high memory cost.  
- Not suitable for **very large datasets**.

## How MICE Works
(implemented only on input columns)
### 🔹 Step 1 — Apply only on **input features**
Start with the dataset (with missing values).

<img width="376" height="402" alt="Screenshot 2025-11-13 at 4 04 13 PM" src="https://github.com/user-attachments/assets/157e46d6-72b1-4236-9531-086e29650f69" />

### 🔹 Step 2 — Introduce fake NaNs  

To make the algorithm stable, MICE can introduce some **artificial missing values**.

<img width="313" height="220" alt="Screenshot 2025-11-13 at 4 05 59 PM" src="https://github.com/user-attachments/assets/8188b3e5-650f-4295-81fe-1ff99692a167" />

### 🔹 Step 3 — Initial Filling  
Fill all missing values with simple imputation (usually **mean**).  
This is called **Iteration 0** (baseline).

<img width="369" height="218" alt="Screenshot 2025-11-13 at 4 06 27 PM" src="https://github.com/user-attachments/assets/f38be845-87f6-4544-bdbd-e2285ecf6681" />

### 🔹 Step 4 — Chain of Models  
Move **left → right**, column by column:

For each column with missing values:
1. Treat this column as **target**  
2. Use all other columns as **features**  
3. Train a regression model  
4. Predict and replace missing values

Repeat for each column.

<img width="777" height="335" alt="Screenshot 2025-11-13 at 4 08 01 PM" src="https://github.com/user-attachments/assets/67d7dd0f-94c0-42bf-b221-9d4163d9682b" />

<img width="775" height="346" alt="Screenshot 2025-11-13 at 4 09 03 PM" src="https://github.com/user-attachments/assets/2570757d-ca9f-42fc-9e07-d250c958df81" />

<img width="779" height="360" alt="Screenshot 2025-11-13 at 4 10 13 PM" src="https://github.com/user-attachments/assets/8af2c3ed-694e-4d88-bdbf-e0a9cc9db4de" />

Now **Stage 1** ends → no missing values left.

## 🔁 Iterations

### Iteration 0  
- All missing values filled using simple methods (mean/median).

### Iteration 1  
- Use regression models to *predict* missing values more accurately.  
- Compute **difference** between Iteration 0 vs Iteration 1 values.

<img width="784" height="292" alt="Screenshot 2025-11-13 at 4 12 20 PM" src="https://github.com/user-attachments/assets/35c4e5bc-5a96-435f-8267-982f3dc15ff6" />

### Continue Iterating  
Repeat the cycle until:
- Differences become **zero or almost zero**, OR  
- A **fixed number of iterations** is reached.

Each new iteration uses the **previous iteration's predictions** as the starting point.

<img width="785" height="339" alt="Screenshot 2025-11-13 at 4 13 45 PM" src="https://github.com/user-attachments/assets/4a52ff8b-dd13-40c1-bad1-1714d03d50b2" />

