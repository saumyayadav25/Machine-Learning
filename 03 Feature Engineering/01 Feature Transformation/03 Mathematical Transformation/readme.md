# Mathematical Transformation

Transforms feature values so that their **distribution becomes closer to Normal (Gaussian)** — this helps many ML models (like Linear Regression, SVM, etc.) perform better.

### 🎯 Why We Use It
- Reduces **skewness** in data  
- Stabilizes **variance**  
- Improves **model performance** and **interpretability**  
- Makes data more suitable for **parametric algorithms**

### Function Transformer
Used for applying simple mathematical transformations.

1. **Log Transform** → Compresses large values, useful for right-skewed data  
   _Example_: Income, Price  

2. **Reciprocal Transform** → Takes inverse of the values (`1/x`), reduces effect of large outliers  

3. **Power Transform (Square / Square Root)** → Reduces right skew or stabilizes variance  

4. Custom Function Transformer
It allows you to apply **any custom Python function** to transform your data.

#### Example:
```python
from sklearn.preprocessing import FunctionTransformer
import numpy as np

# Custom log1p transformation (log(1 + x))
log_transformer = FunctionTransformer(func=np.log1p, inverse_func=np.expm1)

X_transformed = log_transformer.fit_transform(X)
```

Useful when:

You want to apply a **domain-specific formula**

### Power Transformer
Used when we want **automatic and optimal normalization** of data.

1. **Box-Cox Transform** → Works only on **positive data**

2. **Yeo-Johnson Transform** → Works on **both positive and negative data**


# 📈 How to Check if Data is Normally Distributed

1. **Seaborn – `distplot()` / `histplot()`**
   - Visualize distribution shape  
   - Bell-shaped curve → approximately normal  
   ```python
   import seaborn as sns
   sns.histplot(data['feature'], kde=True)
   ```

2. **Pandas** – `skew()` Function

    - Measures asymmetry of data

    - `skew() ≈ 0` → nearly normal

    - Positive → right-skewed, Negative → left-skewed
    ```python
      data['feature'].skew()
    ```

3. **Q-Q Plot (Quantile-Quantile Plot)** ✅ Most Reliable

  - Compares data quantiles with a normal distribution

  - If points lie roughly on the diagonal line → data is normal
  ```python
  import scipy.stats as stats
  stats.probplot(data['feature'], dist='norm', plot=plt)
  plt.show()
  ```

  <img width="631" height="616" alt="image" src="https://github.com/user-attachments/assets/2cb32491-520a-4508-805e-5c3c4b6e4dee" />

  <img width="391" height="119" alt="Screenshot 2025-10-23 at 3 47 51 PM" src="https://github.com/user-attachments/assets/c839aa0e-2ac3-4bde-9b55-4c6d28cf67a0" />

