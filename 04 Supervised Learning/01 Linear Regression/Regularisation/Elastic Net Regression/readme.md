# Elastic Net Regression (ENR)

Elastic Net Regression is a **regularization technique** that combines **Ridge (L2)** and **Lasso (L1)**.  
It is mainly used to **reduce overfitting** and to handle **multicollinearity** between input features.

#### Ridge Regression (L2)

Ridge regression adds an **L2 penalty** to Mean Squared Error.

Loss function:
```
L = Σ (yᵢ − ŷᵢ)² + λ ||w||²
```
Key points:
- Penalizes large weights using L2 norm.
- As λ increases, weights **shrink toward 0 but never become exactly 0**.
- Does **not perform feature selection**.
- Used when **all features are important** and none should be removed.

#### Lasso Regression (L1)

Lasso regression adds an **L1 penalty** to Mean Squared Error.

Loss function:
```
L = Σ (yᵢ − ŷᵢ)² + λ ||w||
```
Key points:
- Penalizes weights using L1 norm.
- As λ increases, some weights become **exactly 0**.
- Performs **feature selection automatically**.
- Used when you are confident that **some features are not important** for predicting the target.

### Elastic Net Regression (ENR)

Elastic Net combines **both L1 and L2 penalties**.

Loss function:
```
L = Σ (yᵢ − ŷᵢ)² + a ||w||² + b ||w||
```
Why Elastic Net:
- Useful when the dataset is **large** and you are unsure whether to use L1 or L2.
- Works better than Lasso when features are **highly correlated**.
- Can both **shrink weights** and **eliminate some features**.

#### scikit-learn Parameters (ElasticNet)

scikit-learn exposes two hyperparameters:

- `alpha` → overall regularization strength  
- `l1_ratio` → proportion of L1 penalty

Relationships:
```
λ = a + b  
l1_ratio = b / (a + b)
```
So:
- b = l1_ratio × λ   (L1 part)
- a = λ − b          (L2 part)

Defaults:
- alpha = 1
- l1_ratio = 0.5

This gives:
- a = 0.5
- b = 0.5

Meaning equal contribution from L2 and L1.

<img width="542" height="363" alt="Screenshot 2025-12-29 at 4 55 45 PM" src="https://github.com/user-attachments/assets/b316d887-bd37-4cdc-8d0c-f65e7176bf58" />

#### Effect of l1_ratio

- l1_ratio = 0 → Pure Ridge (only L2)
- l1_ratio = 1 → Pure Lasso (only L1)
- l1_ratio = 0.9 → Mostly Lasso with slight Ridge support

### When to Use Elastic Net

Elastic Net is preferred when:
- Input features show **multicollinearity**.
- Example: height (x₁) and weight (x₂).  
  If height increases, weight usually increases as well, so the features are correlated.
- Lasso alone may randomly drop one of the correlated features.
- Elastic Net keeps correlated features stable while still applying regularization.