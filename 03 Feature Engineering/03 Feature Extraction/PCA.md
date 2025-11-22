# PCA — Principal Component Analysis

- An **unsupervised ML technique**.  
- A **feature extraction** method used to reduce dimensions.  
- Goal: Helps to solve the **Curse of Dimensionality (COD)**.  
- Transforms high-dimensional data → **lower-dimensional space** while keeping the **maximum information (essence)**.

### 📷 Analogy (Super Easy to Understand)

A photographer clicks a photo of a **3D stadium** during a soccer match.  
The photo becomes **2D**, but still captures the **important details**.

PCA works the same way:
- It takes **high-dimensional data**  
- Projects it to **fewer dimensions**  
- While keeping the **important structure** of the original data.

#### 🎯 Why PCA is Used? (Benefits)

1. Faster Algorithm Execution
- Reduces number of features → models train faster.

2. Better Visualization
- Humans can only visualize **1D, 2D and 3D**.  
- PCA can convert even **10–100+ dimensional** data into **2D/3D**, making visual analysis possible.

3. Reduces Noise
- PCA removes redundant / correlated / noisy features.

4. Helps Overfitting
- Fewer dimensions → simpler model → less chance of overfitting.


# 📌 How PCA Decides Important Features  
*(Feature Selection Intuition)*

This example helps understand **why PCA prefers directions with high variance**.

#### 🧪 FEATURE SELECTION EXAMPLE

<img width="456" height="219" src="https://github.com/user-attachments/assets/ecc92639-afed-4130-9ae6-e936ad484fec" />

Suppose we want to predict **house price**, and we have:

- Number of rooms  
- Number of grocery shops  
- Price  

Domain knowledge says “rooms” affects price more than grocery shops.  
But what if we **don’t** have domain knowledge?

PCA looks at **variance** to decide what’s important.

#### 🏠 Intuition

Plot the data:

- **X-axis → Rooms**  
- **Y-axis → Grocery Shops**

Look at the **spread** of the points:

- Rooms vary a lot → **high variance**  
- Grocery shops barely vary → **low variance**

👉 Feature with **higher variance** → contains more information  
👉 PCA will **prefer this direction**

That’s why PCA keeps the direction (axis) with maximum variance and ignores the one with very low variance.

This is feature selection intuition:  
**d(rooms) > d′(grocery shops)**  
(where d is the high-variance direction)

## 🧩 FEATURE EXTRACTION INTUITION (PCA)

Now consider a different data:

- Number of rooms  
- Number of washrooms  
- Price  

<img width="468" height="188" src="https://github.com/user-attachments/assets/ca146b81-4b7a-484a-9dec-56b11aa9ddbc" />

In this case:

Rooms <-> Washrooms  
Both vary similarly and both matter.  
Feature selection will **not** help here.

So instead, PCA performs **feature extraction**:

> It creates a **new feature** that captures the combined information of rooms + washrooms  
> (like “overall house size”).

This new feature did **not** exist earlier.

# 🔷 GEOMETRIC / MATHEMATICAL INTUITION OF PCA

<img width="494" height="202" alt="Screenshot 2025-11-22 at 4 22 04 PM" src="https://github.com/user-attachments/assets/2fa0eca5-33b9-4363-97d4-e3d43d91cc92" />

Think of the original axes:

- X = rooms  
- Y = washrooms  

PCA will:

#### 🔹 Step 1 — Rotate the Coordinate System
PCA finds a **new set of axes** (PC1, PC2, …) by rotating the original feature space.

- **PC1** → the direction with **maximum variance**  
- **PC2** → the direction **perpendicular** to PC1 (captures leftover variance)  

You can think of these new axes as conceptual “rooms′” and “washrooms′” —  
new rotated directions formed by combining the original features.

#### 🔹 Step 2 — Project Data onto These New Axes
The original data (rooms, washrooms, etc.) is **transformed** onto PC1, PC2, …

This produces **new features**:
- **PC1** → major information (e.g., overall house size)  
- **PC2** → minor variations or noise  

These new features did not exist earlier — they are **extracted**.

#### 🔹 Step 3 — Keep Only the Important Components
Check how much variance each PC explains.

- If **PC1** explains most variance → keep PC1  
- If **PC2** adds very little → drop PC2  

This reduces dimensions while preserving maximum information.


### 🧠 Important Rule
Number of principal components:

`Number of PCs <= Number of Original Features`

So if original data has 3 features → PCA can create at most 3 PCs.

## 🎯 Why is Variance Important?

Variance tells us **how much the data spreads out**.  
Mean alone cannot tell the full story.

#### 🔹 Mean is NOT enough

<img width="499" height="303" src="https://github.com/user-attachments/assets/ecaf7820-380f-4ac5-b9f9-2aa7da8fc9e8" />

Example:

- Data = [-5, 5] → Mean = 0  
- Data = [-10, 10] → Mean = 0  

The **mean is the same**, but the **data spread is very different**.  
Only **variance** (or standard deviation) can capture this difference.

### 🔹 Spread vs Variance
Spread ≠ Variance  
But variance is **proportional** to spread.

- **Variance** → average squared distance from mean  
- **Standard deviation** → √variance, so it’s in the same units as data  
- **Mean absolute variation (MAV)** is not preferred because  
  - absolute values are not differentiable at 0  
  - squared values are smooth & mathematically better

## 📌 Now coming to PCA: Why Variance Matters?

Consider a scatter plot with red and green points (classes).  
Your ML model must **separate** them.

If we project incorrectly (onto low-variance axis), we lose the real distance:

<img width="233" height="184" src="https://github.com/user-attachments/assets/dfb52dc3-359b-4bfd-ab2c-288c7852194f" />

- On the **Y-axis**, two points look very close → wrong story  
- On the **X-axis**, their distance is clear → correct story  

If we reduce dimensions (2D → 1D) by projecting onto an axis:

#### Projection on Y-axis:
- The red and green points fall **very close**
- Their actual distance is lost  
- A distance-based model (like **KNN**) would fail  
- PCA hates this because **information is lost**

#### Projection on X-axis:
- Distance between red and green remains **large**
- Their separation is preserved  
- PCA prefers this direction because **variance is higher**

👉 **Goal of PCA = choose the direction where data varies/spreads the most.**  
👉 More variance = more information retained.

---

# Problem Formulation

we have a dataset in 2d and hume ise reduce krke 1d me laana hai.

dataset spread: in image(in 2d)

i have to find a single axis jiske upar mai apne data ko project kr pau and utne hi ache result mile jitne 2d mai mil rhe h