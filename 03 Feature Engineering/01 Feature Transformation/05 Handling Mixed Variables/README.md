# Handling Mixed Variables

When a single column contains **both numerical and categorical data**, we separate them for proper preprocessing.

### Example 1

| Mixed_Column | Category | Number |
|:-------------:|:---------:|:-------:|
| b5            | b         | 5       |
| c3            | c         | 3       |
| a2            | a         | 2       |

👉 Split the mixed column into:
- **Category column** → contains letters (categorical)
- **Number column** → contains digits (numerical)

### Example 2

| Mixed_Column | Category | Number |
|:-------------:|:---------:|:-------:|
| 7             | NaN       | 7       |
| 3             | NaN       | 3       |
| A             | A         | NaN     |
| C             | C         | NaN     |
| 4             | NaN       | 4       |

👉 For mixed data like `[7, 3, 1, A, C, 4...]`:
- Create **two new columns**
- Fill **NaN** where that data type doesn’t exist


### 🎯 Why Do This?
- Ensures correct preprocessing:
  - **Scaling** → on numeric values  
  - **Encoding** → on categorical values  
- Makes the dataset **clean, structured, and ML-ready**.

---

# Handling Date and Time Variables

Date and time columns contain **multiple pieces of information** that can be extracted into separate features for better analysis or model performance.


### 🧩 Example 1 — Date
| Date        | Day | Month | Year | Day_of_Week | Quarter | Semester | Weekend |
|:------------:|:---:|:-----:|:----:|:------------:|:--------:|:----------:|:--------:|
| 23-Aug-2012  | 23  | 8     | 2012 | Thursday     | 3        | 2          | No       |

👉 From `23-Aug-2012`, we can extract:
- **Day, Month, Year**
- **Day of Week** (e.g., Monday, Tuesday…)
- **Quarter** (1–4)
- **Semester** (1–2)
- **Weekend or not** (Yes/No)


## 🕒 Example 2 — Time
| Time     | Hour | Minute | Second |
|:---------:|:----:|:------:|:------:|
| 08:05:40  | 8    | 5      | 40     |

👉 From `08:05:40`, we can extract:
- **Hour**
- **Minute**
- **Second**


###  Why Do This?
- Helps ML models **capture temporal patterns**  
  (e.g., weekend sales, rush-hour traffic)
- Converts **complex datetime objects** into **numeric or categorical features**
- Enables better **feature scaling and encoding** later.
