# Handling Missing Data

<img src="https://miro.medium.com/v2/resize:fit:1358/1*ip2tYhtwCWVGo3Yen5fX7w.png">

Ways to handle missing data: 


| Method | Description | When to Use |
|:--------|:-------------|:-------------|
| **1. Remove Values** | Drop rows or columns with too many missing values. | When missing data is small (<5%) or not important. |
| **2. Impute Values** | Fill missing data using a strategy (mean, median, mode, etc.). | When you can estimate the missing values without bias. |

`SimpleImputer` (Univariate Imputation)
Used to fill missing values **column-wise** using a single feature’s statistics.