# 🛠️ Feature Construction
- There is **no fixed algorithmic process**.  
- It is **manual** and depends entirely on **domain knowledge**.  
- You create new meaningful features from existing ones based on understanding of the problem.

---

# ✂️ Feature Splitting
- Used when data in a **single column is not tidy** and contains **multiple pieces of information** packed into one cell.
- We split the column into separate features so that each column represents **one atomic piece of information**.

Example:  
`Name = "Mr. Ankit"`  
- Split into:  
  - `Title = "Mr"`  
  - `First_Name = "Ankit"`

This helps the model understand and use information more clearly.
