# Handling Categorical Missing Data

## 1. Most Frequent Value Imputation
- For **MCAR** and **<5% missing data** → use the **mode** (most frequent category).  
- Simple and quick to apply.  
- ❌ May **distort the distribution** if missing values are not random.  

## 2. "Missing" Category Imputation
- Used when **a large portion of data (≥10%)** is missing.  
- A new category like **“Missing”** is created to capture that information.  
- ✅ Preserves all data and may provide **useful signal** if missingness itself carries meaning.  
- ❌ Adds an **artificial category**, which can sometimes confuse the model.
