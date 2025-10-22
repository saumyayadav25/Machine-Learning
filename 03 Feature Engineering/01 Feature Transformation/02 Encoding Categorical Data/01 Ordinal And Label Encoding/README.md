# Ordinal Encoding and Label Encoding (FOR ORDINAL CATEGORICAL DATA)

### OrdinalEncoder

- Used when **input features (X)** contain **ordinal categorical data** (data with a natural order).  
- Converts categories into integers **based on order**. 
- We **manually define** which category has **higher or lower order**.  
- Example: `{"Low": 1, "Medium": 2, "High": 3}`  
- Used **for input data**.

```python
```python
from sklearn.preprocessing import OrdinalEncoder

encoder = OrdinalEncoder()
X_encoded = encoder.fit_transform(X)
```

### LabelEncoder

- Used when **output/target (y)** is **categorical**(especially in classification problems).

- Similar to ordinal encoding but **specifically designed for target labels.**
- The encoder **automatically assigns integer values** (we don’t specify order).
- Example: `{"Cat": 0, "Dog": 1, "Horse": 2}`

- Used **for output data.**

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
y_encoded = le.fit_transform(y)
```

| Encoder            | Used For           | Handles                  | Example                         |
| ------------------ | ------------------ | ------------------------ | ------------------------------- |
| **OrdinalEncoder** | Input features (X) | Ordinal categorical data | `Low → 1, Medium → 2, High → 3` |
| **LabelEncoder**   | Output labels (y)  | Categorical targets      | `Dog → 1, Cat → 0`              |
