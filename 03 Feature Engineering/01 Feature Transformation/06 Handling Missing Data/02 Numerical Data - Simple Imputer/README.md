# Handling Missing Numerical Data (Univariate)

## 1. Mean / median Imputation
| Distribution Type | Recommended Strategy |
|:------------------|:----------------------|
| **Normal Distribution** | Use **Mean** (since mean ≈ median ≈ mode). |
| **Skewed Distribution** | Use **Median** (less affected by outliers). |

#### When to Use
- When data is **MCAR (Missing Completely at Random)**.  
- When **less than 5%** of the data is missing.

#### ✅ Benefits
- Simple and quick to apply.  
- Works fine for small missing portions (<5%).

#### ❌ Disadvantages
- Changes the **shape of the distribution**.  
- **May create new apparent outliers:** mean imputation reduces variance, making some previously normal values appear as outliers.
- Alters relationships with other columns (**covariance/correlation changes**).  
- Not preferred in **production models**.

## 2. Arbitrary Value Imputation

- Replace missing values with a fixed or uncommon value (e.g., **-999**, **9999**, or **"Missing"**).  
- **Mostly used for categorical data** (e.g., filling `"Missing"`).  
- For numerical data, used only to **differentiate missingness**.

**When to use:**  
- When data is **Not Missing At Random (NMAR)** — missingness itself carries information.

**Advantages:**
- Easy to apply  

**Disadvantages:**
- Distorts distribution (PDF)  
- Changes variance and covariance  
- Not preferred for numerical data

## 3. End of Distribution Imputation
- Extension of **arbitrary value imputation** — used when finding a reasonable replacement value is difficult.  
- Replace missing values with **extreme ends of the distribution**.

**When to use:**  
- When data is **Not Missing At Random (NMAR)**.  
- Missingness may indicate an **extreme condition or boundary case**.

For **normally distributed data:**  
- Use `mean + 3*std` or `mean - 3*std`.

For **skewed data:**  
- Use **IQR rule:**  
  - Lower end → `Q1 - 1.5*IQR`  
  - Upper end → `Q3 + 1.5*IQR`  
  - where `IQR = Q3 - Q1`

**Advantages:**
- Easy to apply

**Disadvantages:**
- Distorts distribution (PDF)  
- Changes variance and covariance  

## 4. Random Sample Imputation
#### Can be applied to both categorical and numerical data.  
- Missing values are filled with **random samples** selected from the **existing (non-missing)** values in the same column.  

**Advantages:**  
- Easy to apply  
- **Preserves variance and distribution**, unlike mean/median imputation  

**Disadvantages:**  
- **Covariance may get slightly affected** since replacement is random  
- Results can vary on each run  
- **Not available in sklearn**, must be implemented using **pandas**

**When to Use:**  
- When you want to **retain the original spread** of the feature while keeping the process simple

<img width="527" height="91" alt="Screenshot 2025-11-12 at 2 54 25 PM" src="https://github.com/user-attachments/assets/6664166c-f03f-4e69-b66d-9668ba0652a7" />

## 5. Missing Indicator  

- Create a **new column** for every feature that has missing values.  
- This new column contains **True/False (or 1/0)** values:  
  - **True (1)** → indicates the value was missing  
  - **False (0)** → indicates the value was present  

This helps the model **learn patterns associated with missingness** - sometimes the fact that data is missing can itself carry useful information.

# Automatically select best Imputation Technique

- Instead of manually testing different imputation methods, we can use **GridSearchCV** in scikit-learn.  
- It automatically tries **multiple combinations** of imputers, scalers, and models using cross-validation.  
- The combination giving the **best performance metric** (e.g., accuracy, RMSE) is selected automatically.  

👉 Helps in **automating preprocessing** and ensures you’re using the **most effective imputation strategy** for your dataset.