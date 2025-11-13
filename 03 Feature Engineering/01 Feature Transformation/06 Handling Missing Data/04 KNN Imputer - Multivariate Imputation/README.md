# KNN Imputer

- Based on the **K-Nearest Neighbors (KNN)** algorithm.  
- Concept: **“You are like your neighbors.”**  
  - If a value is missing, it’s filled using the values of the **most similar rows** (neighbors).  

### 🔹 How It Works
1. **Find k nearest neighbors**  
   - Similarity between rows is measured using **Euclidean distance** (or `nan_euclidean_distances` in sklearn).  
2. **Compute replacement value**  
   - If `k > 1`, the missing value is replaced with the **average (mean)** of its neighbors’ corresponding values.

<img width="578" height="318" alt="Screenshot 2025-11-13 at 3 27 21 PM" src="https://github.com/user-attachments/assets/491b1657-7a26-493e-8cd3-45b894043687" />

<img width="580" height="238" alt="Screenshot 2025-11-13 at 3 34 12 PM" src="https://github.com/user-attachments/assets/9885be62-329e-403d-b336-574e492989bd" />

<img width="488" height="94" alt="Screenshot 2025-11-13 at 3 30 37 PM" src="https://github.com/user-attachments/assets/b5cd3472-0e84-4a58-8cd9-fe6b6c7bdaaa" />

[Nan_euclidean_distances](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.nan_euclidean_distances.html)

adv: more accurate, good with small or medium datasets.
disadv: more no. of calculations
when deployed on server, toh poora training dataset dalna padega. speed slow krdega and memory badh jayegi

### 🔹 Example
If a student’s “Math Score” is missing →  
find other students with similar marks in “Science” and “English” →  
take their average Math score and fill the missing value.

### ✅ Advantages
- More **accurate** than simple imputations.  
- Works well for **small to medium datasets**.  
- Maintains relationships between features.

### ❌ Disadvantages
- **Computationally expensive** (distance calculations for every sample).  
- During deployment, the **entire training dataset** must be stored → increases **memory and latency**.  
- **Slow for large datasets**.