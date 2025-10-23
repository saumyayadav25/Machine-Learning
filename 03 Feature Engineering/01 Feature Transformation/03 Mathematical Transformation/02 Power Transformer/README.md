# Power Transformer

## Box Cox Transform

<img width="379" height="286" alt="Screenshot 2025-10-23 at 6 55 30 PM" src="https://github.com/user-attachments/assets/7235d101-c5f4-4476-98fe-fd404222a9c9" />

A **power transformation** that makes data more **normally distributed** by finding the **best λ (lambda)** value to stabilize variance and reduce skewness.

- Works **only on positive data** (no zeros or negative values).  
- Automatically finds the **optimal λ** using `scipy` or `sklearn`.  

## Yeo - Johnson Transform

<img width="432" height="213" alt="Screenshot 2025-10-23 at 6 58 02 PM" src="https://github.com/user-attachments/assets/031f77db-0a34-424a-9718-0c467aad7507" />

An extension of the **Box–Cox transform** that can handle **zero and negative values** too.  
It also aims to make data **more normally distributed** and **stabilize variance**.

- Works with **positive, zero, and negative** values.  
- Also finds the **best λ** automatically.  
