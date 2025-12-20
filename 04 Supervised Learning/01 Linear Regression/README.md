# 📈 Linear Regression

Linear Regression is a **supervised machine learning algorithm** that models the relationship between input features and a **numerical output**.

- Easy to understand and highly intuitive  
- Forms the foundation for many advanced ML algorithms  
- Widely used in prediction tasks

👉 Since the output is numerical, it falls under **regression problems**.

## 🔹 Types of Linear Regression

### 1️⃣ Simple Linear Regression
- **1 input feature**, **1 output feature**
- Assumes a linear relationship between input and output

**Example:**  
- Dataset: `CGPA vs Package`  
- Input → CGPA  
- Output → Package  

### 2️⃣ Multiple Linear Regression
- **More than 1 input feature**, **1 output feature**
- Output depends on multiple factors

**Example:**  
- Inputs → CGPA, Gender, 12th Marks, State  
- Output → Package  

### 3️⃣ Polynomial Linear Regression
- Used when the relationship between input and output is **not linear**
- Input features are transformed into **polynomial terms**
- Still called “linear” because the model is linear in parameters

**Example:**  
- Curved relationship between CGPA and Package  
- Simple LR fails → Polynomial LR fits better

### 🔹 Regularization
- Used to prevent **overfitting**
- Penalizes large coefficients
- Common techniques:
  - Ridge Regression
  - LASSO Regression
