# 🚨 Outliers in Machine Learning

## 🔹 What are Outliers?
Outliers are data points that are **very different** from the rest of the observations.

- They **pull the model** towards themselves, especially in regression.  
- The best-fit line should pass through most points, but outliers **distort** it badly.

<img width="214" height="210" src="https://github.com/user-attachments/assets/1d1c842c-19a9-456d-9ed0-46365626a3bb" />

### 🔹 Are Outliers Always Bad?
Outliers can be:
- **Dangerous** → e.g., someone accidentally enters **Age = 300**  
- **Useful** → in **Anomaly Detection**, “outliers” *are* the actual signal.

## ⚠️ Effect of Outliers on ML Algorithms

#### 📌 Algorithms Highly Affected (weight-based)
Because these algorithms use **weights**, outliers heavily distort them:

- **Linear Regression**
- **Logistic Regression**
- **AdaBoost**
- **Deep Learning (neural nets)**

#### 📌 Algorithms Less Affected
Tree-based models are **robust** against outliers:

- **Decision Trees**
- **Random Forest**
- **XGBoost / Gradient Boosting**

They split based on thresholds — outliers don’t change splits much.

# 🛠️ How to Treat Outliers?

### 1️⃣ **Trimming (Delete Outliers)**
- Remove outlier rows completely.
- **Advantage:** Very fast  
- **Disadvantage:** If too many outliers → dataset becomes small

### 2️⃣ **Capping (Winsorization)**
Outliers are always at the **ends** — extremely high or low, never in the middle.

So set limits:

```
Lower Cap = lower threshold
Upper Cap = upper threshold
```

All values below/above are clipped to these limits.

<img width="171" height="85" src="https://github.com/user-attachments/assets/c5187a2c-ac1e-4a9b-92d6-9243e75fbf58" />

#### 3️⃣ **Mark as Missing**
(Not widely used)
- Convert outliers → NaN  
- Later handle using imputation  

#### 4️⃣ **Discretization**
(Not commonly used)
- Convert continuous feature → bins  
- Outliers get absorbed into large ranges  

# 🔍 How to Detect Outliers?

## 1️⃣ **For Normal Distribution → Z-Score**
Outliers if:

`|Z| > 3`

<img width="342" height="302" src="https://github.com/user-attachments/assets/0fff8638-d708-4425-bec7-8d559db9bb3e" />

## 2️⃣ **For Skewed Distribution → IQR Method**
Outliers if:

```
Value < Q1 − 1.5IQR
Value > Q3 + 1.5IQR
```

<img width="370" height="261" src="https://github.com/user-attachments/assets/bb9c6994-7a7f-410c-b570-40170a9f57ef" />

## 3️⃣ Other Distributions: **Percentile-Based Approach**
Mark values as outliers if they are:

```
Below 2.5% (or 5%)
Above 97.5% (or 99%)
```

<img width="365" height="262" src="https://github.com/user-attachments/assets/69bc8ccd-659a-4470-b1cf-1498129aeddb" />

# 🧰 Techniques for Outlier Detection & Removal
- **Z-score method**
- **IQR based filtering**
- **Percentile-based filtering**
- **Winsorization (Capping)**
