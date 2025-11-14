# Outlier Detection using Percentile (Winsorization Technique)

(CAPPING USING PERCENTILE METHOD IS KNOWN AS **WINSORIZATION**)

Percentile-based outlier detection identifies extreme values by looking at how far they lie in the distribution.

### 🔹 Understanding Percentiles
- **0th percentile (Min)** → Smallest value (everyone is ahead of you)  
- **100th percentile (Max)** → Largest value (you are ahead of everyone)  
- **50th percentile (Median)** → Half the data is below, half is above  

### 🔹 How Percentile-Based Outlier Detection Works

You select **symmetric cutoff percentiles**:

- **Below 1st percentile** → Outlier  
- **Above 99th percentile** → Outlier  

You **cannot** choose different lower and upper cutoffs (e.g., 1% and 97%) —  
the gap must be **equal on both sides** (like 1–99%, 2.5–97.5%, 5–95% etc.).

This keeps the treatment **balanced** and avoids biasing one side of the distribution.

## 🔹 Winsorization (Capping)
Instead of deleting outliers, replace:

- Values **below lower percentile** → replace with value at that lower percentile  
- Values **above upper percentile** → replace with value at that upper percentile  

Example:  
If 1st percentile = 10 and 99th percentile = 120  
- Any value < 10 → replace with 10  
- Any value > 120 → replace with 120  