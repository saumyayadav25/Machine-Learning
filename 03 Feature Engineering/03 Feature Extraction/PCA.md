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

## Problem Formulation

We are given a **2D dataset**, and our goal is to **reduce it to 1D** while preserving as much information as possible.

The data is spread in 2D space (as shown in the figure).

<img width="268" height="213" alt="Screenshot 2025-12-19 at 6 54 57 PM" src="https://github.com/user-attachments/assets/588a1508-6daa-4eaf-a7d4-26bce25e9851" />

👉 We want to find **one single axis** onto which we can project all data points such that:
- The projected data still represents the original structure well
- Information loss is minimal

### Vector Representation

- Each data point has coordinates `(x, y)`  
- So every point can be represented as a **vector** `X̄`
- We assume all points are vectors in 2D space

We choose a **unit vector `ū`**:
- This vector represents the **new axis**
- Length of `ū` = 1

### Projection of a Point

For a point `X̄`, its projection onto unit vector `ū` is:

```
Projection = uᵀ X
```

Why?
- General projection magnitude = (u · X) / |u|
- Since `u` is a **unit vector**, |u| = 1
- So projection simplifies to **dot product**

👉 The result is a **scalar value**  
This scalar represents the **position of the point in 1D space**.

<img width="478" height="289" alt="Screenshot 2025-12-19 at 6 58 53 PM" src="https://github.com/user-attachments/assets/d5f38df1-92aa-4542-9534-076f5dede9db" />

### Projection of All Points

If we have `n` data points:
```
X₁, X₂, ..., Xₙ
```

Their projections on `u` will be:

```
X′ = [ uᵀX₁ , uᵀX₂ , ... , uᵀXₙ ]
```

Now the entire dataset is represented in **1D**.

#### Objective: Maximize Variance

We want the projected data to be as informative as possible.

👉 Information is captured by **variance**.

So our goal is:

>Choose unit vector u such that variance of projected data X′ is maximum

<img width="475" height="204" alt="Screenshot 2025-12-19 at 7 01 10 PM" src="https://github.com/user-attachments/assets/4a9a5870-3d96-4564-838e-68d785f2d04e" />

### Variance of Projected Data

Mean of projected values:
```
μ = (1/n) Σ (uᵀXᵢ)
```

Variance:
```
Variance = (1/n) Σ (uᵀXᵢ − μ)²
```

This variance **depends on the direction of `u`**.

### 🔹 Final PCA Objective

- Try different unit vectors `u`
- Compute variance of projections
- Select the **unit vector that gives maximum variance**

👉 This unit vector is **PC1 (First Principal Component)**

## Covariance and Covariance matrix

#### Variance Alone is Not Enough
In the two datasets shown (left and right):

- **Variance along X** is same  
- **Variance along Y** is same  

So just looking at variance, both datasets seem identical.

<img width="475" height="268" src="https://github.com/user-attachments/assets/81219a55-92b2-4f00-bb6d-09179ea40fbc" />

But clearly, the **shape and orientation** of data is different.

#### 🔹 What Covariance Tells Us
**Covariance measures the relationship between two variables (X and Y).**

- **Positive covariance** → X increases, Y also increases  
- **Negative covariance** → X increases, Y decreases  
- **Zero covariance** → No linear relationship  

So even if variance is same:
- **Covariance will be different** for left and right datasets.

<img width="493" height="276" src="https://github.com/user-attachments/assets/0069bc18-f449-4067-8391-510f283bb678" />

👉 This is why covariance is crucial for understanding **data orientation**, not just spread.

### Covariance Formula
Covariance between X and Y:
```
Cov(X, Y) = average of (Xi − mean(X)) * (Yi − mean(Y))
```

covariance matrix:

### Covariance Matrix

For a 2D dataset (X, Y), the covariance matrix is:
```
[ Var(X) Cov(X,Y) ]
[ Cov(Y,X) Var(Y) ]
```

- Diagonal elements → **variances**
- Off-diagonal elements → **covariances**

<img width="458" height="272" alt="Screenshot 2025-12-19 at 7 27 31 PM" src="https://github.com/user-attachments/assets/d9a6cc10-09c4-488e-a434-63cc38afbe19" />

The covariance matrix tells us **everything about the data geometry**:

- **Spread of each axis**  
  - Diagonal elements → variance of each feature  
  - Shows how much data is spread along every axis  

- **Relationship between feature pairs**  
  - Off-diagonal elements → covariance between two axes  
  - Shows how two features change together  

<img width="351" height="220" alt="Screenshot 2025-12-19 at 7 29 46 PM" src="https://github.com/user-attachments/assets/8e2a142c-23f7-4678-9d2a-9abeff04256e" />

#### Interpretation
- **Positive covariance (+ve)** → if one feature increases, the other also increases  
- **Negative covariance (−ve)** → if one feature increases, the other decreases  
- **Zero covariance** → no linear relationship  

👉 So the covariance matrix captures both:
- **Spread (variance)**  
- **Correlation / direction of data**

This is why PCA relies on the covariance matrix to find the correct orientation of maximum variance.

## Eigen Vectors and Eigen Values

Eigenvectors and eigenvalues describe **how a transformation changes space**.

https://www.geogebra.org/m/YCZa8TAH

<img width="687" height="385" src="https://github.com/user-attachments/assets/e6cfe06a-aec6-4160-8c6c-54294cd541cd" />

### 🔹 What is an Eigenvector?
An **eigenvector** is a special direction that **does not change its direction** when a linear transformation (like scaling, stretching, or rotating) is applied.

- Direction remains the same  
- Only the **magnitude (length)** may change  

### 🔹 What is an Eigenvalue?
An **eigenvalue** tells us **how much the eigenvector is stretched or compressed**.

- Large eigenvalue → more stretching along that direction  
- Small eigenvalue → less stretching  
- Eigenvalue = 0 → direction collapses  

#### Mathematical Idea
For a matrix `A`:
```
A · v = λ · v
```

Where:
- `v` = eigenvector (direction unchanged)
- `λ` = eigenvalue (scaling factor)

<img width="218" height="111" alt="Screenshot 2025-12-19 at 7 47 46 PM" src="https://github.com/user-attachments/assets/c6495cf7-014e-457c-a421-a93a34d186fd" />

#### 🔗 Why Eigenvectors & Eigenvalues Matter for PCA

- PCA is based on the **covariance matrix**
- Eigenvectors of the covariance matrix give the **new axes (PCs)**
- Eigenvalues tell **how much variance lies along each axis**

##### PCA Connection
- **Eigenvector with largest eigenvalue → PC1**  
- **Eigenvector with second largest eigenvalue → PC2**  

👉 PCA keeps eigenvectors with **highest eigenvalues**  
👉 Drops directions with very small eigenvalues (low variance / noise)

# Step by Step Solution

Assume we have:
- 3 input features: `f1, f2, f3`
- 1 target column (target is **NOT used** in PCA)

Data lies in **3D space** and we want to reduce it to **2D or 1D**.

### 🔹 Step 1 — Mean Center the Data
- Compute mean of each feature (`f1, f2, f3`)
- Subtract the mean from corresponding feature values

Purpose:
- Moves data so that it is centered around the origin

👉 PCA can work without this step, but **mean centering is strongly recommended** and used in practice.

### 🔹 Step 2 — Compute Covariance Matrix
- Calculate covariance between all feature pairs
- Result is a **3 × 3 matrix** (since we have 3 features)

What it captures:
- Diagonal → variance of each feature  
- Off-diagonal → relationship between features

In practice:
- `np.cov()` or internally handled by sklearn

### 🔹 Step 3 — Find Eigenvalues & Eigenvectors
- From covariance matrix, compute:
  - **3 eigenvectors**
  - **3 eigenvalues**

Interpretation:
- Each eigenvector → a **principal direction**
- Each eigenvalue → amount of variance along that direction

Sorting:
- Sort eigenvectors by **descending eigenvalues**

Selection:
- For **1D reduction** → choose top 1 eigenvector (PC1)
- For **2D reduction** → choose top 2 eigenvectors (PC1, PC2)

<img width="481" height="318" alt="Screenshot 2025-12-19 at 8 03 19 PM" src="https://github.com/user-attachments/assets/1b3bd144-c6de-484b-a1d1-5af537201541" />

### 🔹 Step 4 — Transform Data (Projection)
- Project original data onto selected eigenvectors
- Done using **dot product**

Conceptually:
```
Projected Data = Uᵀ · X
```

Where:
- `U` = matrix of selected eigenvectors
- `X` = original mean-centered data

Result:
- 3D → 2D or 1D data
- Maximum variance preserved

<img width="428" height="253" alt="Screenshot 2025-12-19 at 8 07 11 PM" src="https://github.com/user-attachments/assets/93f8264d-b92d-44d8-a08e-4b5c6af41a6b" />

---

# Practical Example — PCA on MNIST Dataset

The **MNIST dataset** contains images of **handwritten digits (0–9)**.  
The task is to **predict which digit** is written in each image.


https://www.kaggle.com/code/nitsin/pca-demo-1

#### Dataset Details
- Each image size → **28 × 28 pixels**
- Total pixels per image → **784 features**
- Total images → **42,000**

So the dataset shape is:
```
42000 rows × 784 columns
```

Each pixel is treated as a **separate feature**.

#### Problem with High Dimensions
- 784 features → very **high-dimensional space**
- Causes:
  - Curse of Dimensionality  
  - High computation cost  
  - Slower model training  

Also, many pixels (especially at borders) contain **little or no useful information**.

#### Key Idea
Digits are usually centered in the image.  
Border pixels are often empty → low variance → not useful.

PCA automatically:
- Finds directions where pixel values vary the most
- Keeps those directions (principal components)
- Drops directions with very low variance (noise)

https://www.kaggle.com/code/saumyayadav25/pca-demo

## Finding optimum number of Principle Components

Each **eigenvalue (λ)** tells us **how much variance** its corresponding eigenvector (PC) explains.

#### 🔹 Variance Explained by a Principal Component
Percentage of variance explained by a PC:

```
Variance % = (λᵢ / Σλ) × 100
```

Where:
- `λᵢ` → eigenvalue of the i-th principal component  
- `Σλ` → sum of all eigenvalues  

#### 🔹 Cumulative Variance Explained
To decide how many PCs to keep, we compute **cumulative variance**:
```
PC1 → λ1
PC1 + PC2 → λ1 + λ2
PC1 + PC2 + PC3 → λ1 + λ2 + λ3
...
```

### 🔹 Rule of Thumb
- Choose the **minimum number of PCs** such that:

Cumulative variance ≥ 90%

(Sometimes 95% is also used depending on the problem.)

##### Example
Suppose:
- λ1 to λ15 together explain **90% variance**

Then:
- We keep **15 principal components**
- Drop the remaining PCs (low variance → low information)

# ❌ When PCA Does NOT Work

PCA is powerful, but it is **not always useful**. There are situations where applying PCA gives **no benefit** or even **loses important information**.

<img width="519" height="209" alt="Screenshot 2025-12-19 at 10 21 31 PM" src="https://github.com/user-attachments/assets/0dbdff85-2b0d-47d4-988e-ef8f9c1c08fe" />

### 1️⃣ Same Variance in All Directions
If after rotating the coordinate system:

- Variance along X and Y is still **almost the same**
- No single direction has clearly higher variance

👉 PCA cannot decide a “better” axis  
👉 Reducing 2D → 2D gives **no advantage**

(In such cases, dimensionality reduction is meaningless.)

### 2️⃣ Projection Causes Overlapping
If after projection onto a lower dimension:

- Different data points fall into the **same or very close range**
- Classes or points start **overlapping**

👉 PCA loses the **true distance** between points  
👉 Distance-based models (like KNN) will perform poorly  
👉 Information is compressed too much

### 3️⃣ Data Has Important Non-Linear Patterns
PCA captures only **linear relationships**.

If the dataset has **non-linear structure**, PCA will fail.

#### Example:
- Data follows a **sine wave pattern**
- Pattern is clear in higher dimensions
- After PCA projection → pattern gets destroyed

👉 PCA cannot preserve curves, circles, or complex shapes  
👉 Important structure is lost
