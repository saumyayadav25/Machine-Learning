# Mini-Batch Gradient Descent

Mini-batch Gradient Descent is a **middle ground** between Batch GD and Stochastic GD.

## 🔹 Core Idea
- Instead of using:
  - **All rows** (Batch GD)
  - **One row** (SGD)
- We use a **small group of rows** called a **batch**

Example
- Total rows (n) = 1000  
- Batch size = 100  

Then:
- Total batches = 1000 / 100 = **10**
- Updates per epoch = **10**

👉 Each batch produces **one update** of parameters.

#### 🔹 How It Works
```
for each epoch:
split data into batches
for each batch:
compute gradient using batch
update parameters
```

<img src="mini_batch_contour_plot.gif">

<img width="709" height="229" alt="Screenshot 2025-12-27 at 4 57 13 PM" src="https://github.com/user-attachments/assets/ba70308a-2251-4529-afae-00b697c037c0" />
