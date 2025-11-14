# Outlier removal using Z score

- Used to detect outliers in **normally distributed data**.

`Z = (xi - u) / sigma`

Where:  
- xi = data point  
- u = mean  
- sigma = standard deviation  

### 🔹 How It Works
- A Z-score tells how many **standard deviations** a value is away from the mean.  
- Values within **-3 to +3** are considered **normal**.  
- Values **beyond this range** are treated as **outliers**.

This is effectively the same as checking:

`u - 3(sigma) < x < u + 3(sigma)`

<img width="509" height="306" src="https://github.com/user-attachments/assets/0b24fd6a-e62d-40d0-bd9a-2687d0ad82af" />

### 🚨 If an Outlier is Detected (Treatment)

#### 1️⃣ Trimming (Removing Rows)
- Simply **delete** rows containing outliers.  
- ⚠️ Issue: If too many outliers exist → dataset becomes small.

#### 2️⃣ Capping (Winsorization)
- Set **upper and lower limits**, and clip values:  
  - If a value is above upper cap → replace with upper cap  
  - If below lower cap → replace with lower cap  

Example caps for Z-score:
- Lower Cap = u - 3(sigma)
- Upper Cap = u + 3(sigma)