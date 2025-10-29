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

## Automatically select best Imputation Technique
