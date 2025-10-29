# Complete Case Analysis

<img width="474" height="92" alt="Screenshot 2025-10-29 at 7 55 27 PM" src="https://github.com/user-attachments/assets/fd7b45e5-07c3-4858-a0b5-1b328cf406a2" />

## When to Use Complete Case Analysis (CCA)

1. When data is **Missing Completely at Random (MCAR)**.  
2. When **less than 5% of data** is missing — so dropping rows won’t significantly impact results.

### Assumption for Complete Case Analysis (CCA)

- Data must be **Missing Completely at Random (MCAR)** —  
  meaning the probability of a value being missing is **independent of both observed and unobserved data**.

👉 If this assumption is violated, removing rows may **introduce bias** and distort model performance.

### 📊 After Dropping Missing Values

- Plot **histograms** (before vs after dropping missing data).  
- If both distributions **overlap closely**, it means the missing data was **random** and **dropping rows didn’t distort** the dataset.

### Advantages and Disadvantages

<img width="357" height="223" alt="Screenshot 2025-10-29 at 7 59 17 PM" src="https://github.com/user-attachments/assets/485480a7-8873-4066-95dc-18536a4ce13d" />

- The **model never learns how to handle missing data**, since all missing rows were removed during training. So in **production**, if new unseen data has missing values, the model may **fail or give unreliable predictions**.