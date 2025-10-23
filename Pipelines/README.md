# Scikit Learn Pipelines

**Pipelines** chains together multiple steps so that the output of each step is used as input to the next step.

Pipelines makes it easy to apply the same preprocessing to train and test, making the workflow clean, reproducible, and less error-prone.

<img width="1400" height="827" alt="image" src="https://github.com/user-attachments/assets/e136f29d-7c0e-476b-a865-92376794d06e" />


- Pipeline we are going to follow in titanic dataset:

<img width="454" height="128" alt="Screenshot 2025-10-23 at 3 21 17 PM" src="https://github.com/user-attachments/assets/1cdbd32c-4ba9-4a00-be86-7a9261fffdb2" />

1. **Imputation** → Fill missing values (e.g., `age`, `embarked`)  
2. **Encoding** → Apply One-Hot Encoding on categorical columns (`sex`, `embarked`)  
3. **Scaling** → Standardize numerical features for uniform range  
4. **Feature Selection** → Select top 5 most relevant features  
5. **Model Training** → Train Decision Tree on processed data  
