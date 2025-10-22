# Column Transformer

<img width="335" height="338" alt="Screenshot 2025-10-22 at 9 49 17 PM" src="https://github.com/user-attachments/assets/c88d6c0c-145a-42f1-b21f-af76a5cfc41c" />


`ColumnTransformer` is a utility in **scikit-learn** that allows you to **apply different preprocessing steps to different columns** of your dataset in a single pipeline.


#### Why it is Useful
- Real-world datasets often contain **mixed data types**:  
  - Numerical features → need scaling (`StandardScaler`, `MinMaxScaler`)  
  - Categorical features → need encoding (`OneHotEncoder`, `OrdinalEncoder`)  
- `ColumnTransformer` allows you to **process each type appropriately without manually separating columns**.  
- Helps **keep preprocessing organized** and can be combined with **Pipeline** for ML models.  

### Example
```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder, StandardScaler

ct = ColumnTransformer([
    ('num', StandardScaler(), ['age', 'salary']),
    ('cat', OneHotEncoder(drop='first'), ['gender', 'city'])
])

X_transformed = ct.fit_transform(X)
```
- `num` → applies `StandardScaler` to numerical columns `['age','salary']`

- `cat`→ applies `OneHotEncoder` to categorical columns `['gender','city']`

- Output → **single processed array** ready for ML models

## Advantages of ColumnTransformer

- Handles **mixed data types automatically**  
- Keeps preprocessing **clean and reproducible**  
- Works seamlessly with **Pipeline**, making workflow end-to-end  
- Avoids **manual concatenation** of transformed columns  

## ❌ Without ColumnTransformer

- Need to **manually separate** numerical and categorical columns.  
- Apply **different preprocessing** to each subset (`StandardScaler` for numeric, `OneHotEncoder` for categorical).  
- After transformation, **manually concatenate** the processed columns back into a single dataset.  
- More **error-prone** and harder to maintain, especially with large datasets or pipelines.