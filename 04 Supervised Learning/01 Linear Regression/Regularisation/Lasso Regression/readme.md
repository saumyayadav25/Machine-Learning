# Lasso Regression (L1 Regularization)

Lasso Regression adds an **L1 penalty** to the Mean Squared Error (MSE).

Loss function:
```
L = Σ (yᵢ − ŷᵢ)² + λ ||w||
```
Here:
- The first term is MSE.
- `||w||` represents the **L1 norm**.

L1 norm expanded:
```
||w|| = |w₁| + |w₂| + |w₃| + ... + |wₙ|
```

So the loss becomes:

```
L = Σ (yᵢ − ŷᵢ)² + λ (|w₁| + |w₂| + ... + |wₙ|)
```

## Key Properties of Lasso

- Performs **feature selection**.
- As λ increases, some coefficients become **exactly 0**.
- Input columns with near-zero contribution are effectively **removed from the model**.
- Commonly preferred in **high-dimensional datasets** where many input features are not important.
- Feature selection happens **inherently**, without an explicit feature selection step.

## Bias–Variance Tradeoff (Lasso)

As λ increases:
- Overfitting decreases
- Bias increases
- Variance decreases

This tradeoff helps control model complexity.

<img width="958" height="702" alt="image" src="https://github.com/user-attachments/assets/f92efa84-fd37-4085-ae9b-a89ee61a52b8" />

---

# Why Lasso Regression Creates Sparsity (Important for Interviews)

A key difference between **Lasso** and **Ridge** regression is that **Lasso can produce exact zero coefficients**, while Ridge cannot. This property is called **sparsity**.

### Core Observation

- In **Ridge**, no matter how large you make λ (alpha), coefficients **never become exactly 0**.  
  They only move closer to 0.
- In **Lasso**, coefficients **can become exactly 0**.
- If λ is extremely large, **all coefficients can become 0** in Lasso.

ridge:

<img width="673" height="269" alt="Screenshot 2025-12-29 at 6 16 40 PM" src="https://github.com/user-attachments/assets/00f7d552-7c9a-43fa-a5f4-e1ef841be723" />

lasso:

<img width="631" height="217" alt="Screenshot 2025-12-29 at 6 18 41 PM" src="https://github.com/user-attachments/assets/101ba762-ab36-4cf4-9ad6-bb8bd0849ba4" />

### Why Lasso DOES Create Sparsity

Lasso regression uses an L1 penalty:
```
L = Σ (yᵢ − ŷᵢ)² + λ ||w||
```
The L1 norm is:
```
||w|| = |w₁| + |w₂| + ... + |wₙ|
```
During optimization, the update involves **subtracting λ from the coefficient magnitude**.

Intuition:
- λ is **directly subtracted** from the coefficient.
- As λ increases, the coefficient decreases.
- Once it reaches **0**, it stops there.

This is why coefficients hit **exact zero**.

<img width="644" height="210" alt="Screenshot 2025-12-29 at 6 20 54 PM" src="https://github.com/user-attachments/assets/d03ee694-2bbd-4119-a138-751f94bac895" />

<img width="681" height="292" alt="Screenshot 2025-12-29 at 6 22 56 PM" src="https://github.com/user-attachments/assets/66654190-40d9-4714-a857-d96eb0eb4127" />

<img width="694" height="326" alt="Screenshot 2025-12-29 at 6 24 27 PM" src="https://github.com/user-attachments/assets/43e5bbb5-f3b3-4ce4-a18f-64a2744b4ae6" />

<img width="684" height="346" alt="Screenshot 2025-12-29 at 6 28 58 PM" src="https://github.com/user-attachments/assets/647e1a5b-d4ea-495c-a9d0-524c9e66507d" />

#### Why Coefficients Do Not Become Negative

> If λ is subtracted, why doesn’t the coefficient go negative?

- Once the coefficient reaches **0**, the sign would flip if subtraction continued.
- That would require switching to a **different update rule** (where λ gets added instead).
- Adding λ would **increase the magnitude again**, which increases loss.
- To avoid this oscillation, the optimization **clips the value at 0**.

So:
- Coefficient decreases → reaches 0 → stays at 0.

<img width="657" height="329" alt="Screenshot 2025-12-29 at 6 30 53 PM" src="https://github.com/user-attachments/assets/24880988-2444-46a0-9d2c-c0a413eaf774" />

### Why Does Ridge NOT Create Sparsity?

Ridge regression uses an L2 penalty:
```
L = Σ (yᵢ − ŷᵢ)² + λ ||w||²
```
During optimization, the coefficient update effectively looks like:
```
w = numerator / (denominator + λ)
```
Key point:
- λ appears in the **denominator**.
- As long as the numerator is not zero, increasing λ only **shrinks w**, it never makes it exactly 0.
- Therefore, Ridge **cannot eliminate features**.

Geometric intuition:
- Ridge constraint is **circular**.
- The minimum of the loss rarely touches the axes.
- Hence, coefficients stay non-zero.

<img width="602" height="187" alt="Screenshot 2025-12-29 at 6 32 35 PM" src="https://github.com/user-attachments/assets/3114570f-bc41-4d69-8947-829523580d58" />

## Final Contrast: Lasso vs Ridge

- **Lasso**
  - λ is subtracted(in numerator)
  - Coefficients can become **exactly 0**
  - Leads to **sparse models**
  - Performs **feature selection**

- **Ridge**
  - λ appears in the denominator
  - Coefficients **never reach 0**
  - No feature selection