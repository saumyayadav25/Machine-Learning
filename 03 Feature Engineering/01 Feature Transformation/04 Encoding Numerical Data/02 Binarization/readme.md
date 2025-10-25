## Binarization

- special case of Discretization

- Converts **numerical features into binary (0/1) values** based on a **threshold**.  

### How It Works
- For each value in a feature:  
  - If value > threshold → 1  
  - If value ≤ threshold → 0  


### 🔹 Example
Feature: **Income**, threshold = 30  
- Income 25 → 0  (not taxable)
- Income 35 → 1  (taxable)

### Use Case
- Useful for **feature engineering**, **simplifying data**, and preparing features for **models that require binary input**.

## Binarization using Scikit-learn

### Syntax
```python
from sklearn.preprocessing import Binarizer

binarizer = Binarizer(threshold=30, copy=False)
x_binarized = binarizer.fit_transform(x[['income']])
```

[Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Binarizer.html)