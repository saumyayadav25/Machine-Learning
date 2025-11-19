- First do **feature extraction**, then **feature selection** after training model(will do after learning some models).

# 🚫 Curse of Dimensionality (COD)

## 🔹 What is COD?
- Every feature is a **dimension** → more features = higher dimensions.  
- COD = “Curse of **too many features**.”  
- After a certain point, **adding more features does NOT help** and may even **hurt** the model.

### 🔹 Why It Happens?
#### 1. **Sparsity**
- In high dimensions, data becomes extremely **spread out**.  
- Hard for ML models to find patterns.

#### 2. **Model Performance Drops**
- Models get confused due to noise and irrelevant features.

#### 3. **Computation Increases**
- More features → more memory + more training time.

### 🎯 Example — MNIST
- Original image: **28×28 = 784 features**  
- But useful info is mainly in the **center** of the digit.  
- Borders are mostly **empty (0 values)** → do not help the model.  
- If you remove too much → digit gets cut off.

<img width="314" height="277" alt="Screenshot 2025-11-19 at 5 19 31 PM" src="https://github.com/user-attachments/assets/3f62e46b-cd37-42f2-8aae-700f4dbb7d22" />

So more features ≠ always better.

### 🎯 When COD is Common?
- **Images**
- **Text data (high-dimensional sparse vectors)**
- **Sensor data with too many attributes**

### 🛠️ How to Handle COD? → Dimensionality Reduction

There are **two main ways**:

## 1️⃣ Feature Selection
Select a **subset of useful features** from the original ones.

- Used **after model training**, because the model reveals which features matter.  
- Removes unnecessary dimensions.  
- Techniques:
  - **Forward Selection**
  - **Backward Elimination**

👉 Does **not** create new features — just picks the best ones.

## 2️⃣ Feature Extraction
Create **new features** by transforming the original ones.

- Reduces dimensions by compressing information.  
- Very important before training ML models on high-dimensional data.  
- Techniques:
  - **PCA (Principal Component Analysis)**  
    - Creates new features (principal components)
  - **LDA (Linear Discriminant Analysis)**
  - **t-SNE / UMAP** (visualization)

👉 Creates **new columns**, not subsets.