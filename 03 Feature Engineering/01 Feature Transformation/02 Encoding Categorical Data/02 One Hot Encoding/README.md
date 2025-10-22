# One Hot Encoding (FOR NOMINAL CATEGORICAL DATA)

<img width="415" height="158" alt="Screenshot 2025-10-22 at 8 21 18 PM" src="https://github.com/user-attachments/assets/20c22bf5-5897-409a-9a18-75c59ab845d0" />

[1,0,0]-> yellow

[0,1,0]-> blue

[0,0,1]-> red

- For a categorical feature with **N unique categories**, OHE creates **N binary columns** (one per category).
- If there are 50 different categories → 50 columns will be created.
- This increases dimensionality, but that’s the only way you can solve this problem.

## Dummy Variable Trap

- After OHE, remove any one column(generally first column).
- If you have `n categories` → `n columns` → remove one column → final `n - 1 columns`.  

<img width="4680" height="3576" alt="image" src="https://github.com/user-attachments/assets/c58c32a5-a673-4de9-965f-b8f7ddac4ff7" />

- Occurs when **one category can be predicted from others**, leading to **multicollinearity**.

- The dummy variables become **dependent on each other**, which should not happen in **regression models**. 

- For example, if we have 3 categories and create 3 dummy variables, the sum of all three = 1 always → perfectly correlated.

- Solution: **Drop one column** (e.g., `drop='first'` in `OneHotEncoder` or `pandas.get_dummies(df_name, columns)`).

- This avoids redundancy and makes the model stable.

## OHE using Most Frequent Categories

- When a categorical feature has **many unique categories** (e.g., 40), creating 40 columns with standard OHE can **slow down processing** and increase dimensionality.  
- To reduce this, we **keep only the most frequent categories** as separate columns.  
- The **less frequent categories** are grouped into a new category, often labeled `"Other"`.  
- Example: Instead of 40 categories → now only 10 columns (top 9 frequent + 1 "Other").  
- This technique is useful when some categories appear **very frequently** and others are **rare**, helping to reduce dimensionality and sparsity.  
- ⚠️ Keep in mind: Rare categories lose individual identity, which may slightly reduce model precision for those cases.

## One-Hot Encoding (OHE) Process

[Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)

1. **Select Categorical Columns**  
   - Choose columns in your dataset that are categorical and need encoding, e.g., `[['fuel', 'owner']]`.

2. **Apply OneHotEncoder**  
   ```python
   from sklearn.preprocessing import OneHotEncoder

   ohe = OneHotEncoder(drop='first', sparse=False, dtype=np.int32)
   x_train_new = ohe.fit_transform(x_train[['fuel','owner']])
   ```

    - Creates **binary columns** for each category (except first if `drop='first'` to avoid dummy variable trap).

    - Each original category is converted into 0/1 in the new columns.

3. **Merge with Original Numeric Columns**
    ```python
    import numpy as np
    x_train_final = np.hstack((x_train[['brand','km_driven']].values, x_train_new))
    ```
    - Combines numeric/non-encoded features with OHE columns.

    - Final array contains all features ready for ML models.

