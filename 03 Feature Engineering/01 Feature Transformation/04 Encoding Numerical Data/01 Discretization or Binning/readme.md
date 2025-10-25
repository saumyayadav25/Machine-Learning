## Discretization (Binning)

<img width="441" height="188" alt="Screenshot 2025-10-23 at 7 08 28 PM" src="https://github.com/user-attachments/assets/2243370f-9f2e-4a8d-ae7d-42120a491f73" />

Discretization (or **Binning**) is the process of converting **continuous numerical features** into **categorical bins or intervals**.

### 🔹 Why Use It?
- Simplifies continuous data and makes patterns easier to detect.  
- Helps capture **non-linear relationships**.  
- Makes model **less sensitive to outliers**.  
- Improves **interpretability** of results.

#### Example
If we have a continuous feature like **Age**,  
we can convert it into bins such as:  
- 0–18 → Child  
- 19–40 → Adult  
- 41–60 → Middle-aged  
- 60+ → Senior

# Types od Discretization

<img src="https://miro.medium.com/v2/resize:fit:1400/1*I2cKrbSBnfInj-raQUYddg.png">

-> Supervised Binning(will be doing after Decision Trees)

## Unsupervised Binning

1. Equal Width / Uniform Binning

<img width="442" height="123" alt="image" src="https://github.com/user-attachments/assets/e89258f4-e953-4a53-a215-560b692020e1" />

- Divides the **entire range** of a continuous feature into **bins of equal size** (width).  

### 🔹 How It Works
- Calculate the range: `max value - min value`  
- Divide by the number of bins → each bin gets the same width.  
- Assign each value to the corresponding bin based on its interval.

### 🔹 Example
Feature: **Age** (0–80), 4 bins → bin width = 20  
- 0–20 → Bin 1  
- 21–40 → Bin 2  
- 41–60 → Bin 3  
- 61–80 → Bin 4

- Advantage: Simple to implement.  
- Limitation: If data is **skewed**, some bins may have very few or very many points.

- **No change in spread of data** → original range remains divided uniformly.  
- Works best when data is **roughly uniformly distributed**.

2. Equal Frequency / Quantile Binning

- Divides the data into **bins such that each bin contains roughly the same number of data points**.

### 🔹 How It Works
- Sort the data values in ascending order.  
- Split into `n` bins so that each bin has approximately `total_samples / n` points.  

### 🔹 Example
Feature: **Age**, 12 samples, 3 bins → 4 samples per bin  
- Bin 1 → smallest 4 ages  
- Bin 2 → next 4 ages  
- Bin 3 → largest 4 ages  

- Advantage: **Handles skewed data** better than equal-width binning.  
- Values spread is uniform
- Limitation: Bin widths may **vary**, so intervals are not uniform.  

<img width="353" height="309" alt="Screenshot 2025-10-25 at 6 34 23 PM" src="https://github.com/user-attachments/assets/b28dfef7-7d76-4fc6-a6c2-db498a84635f" />


<img width="512" height="192" alt="image" src="https://github.com/user-attachments/assets/47518597-7b1a-45c2-9041-bef3089f5c0d" />

3. KMeans Binning

- Uses **clustering (KMeans)** to divide a continuous feature into **bins based on natural groupings** in the data rather than fixed intervals or frequencies.

### 🔹 How It Works
- Treat each feature value as a 1D point.  
- Apply **KMeans clustering** to group values into `k` clusters.  
- Each cluster represents a **bin**, and points in the same cluster are assigned to the same bin.  

### 🔹 Example
Feature: **Income** with varying values  
- KMeans clusters data into 3 clusters based on similarity:  
  - Cluster 1 → Low income  
  - Cluster 2 → Medium income  
  - Cluster 3 → High income  

- Advantage: Captures **natural structure of data**, handles skewness and outliers better.  
- Limitation: Requires **choosing number of clusters (bins)** and clustering is **computationally heavier** than uniform or quantile binning.

<img width="640" height="956" alt="image" src="https://github.com/user-attachments/assets/344ea2a6-d680-49d7-b198-a6aa449585b7" />


# Scikit-Learn: KBinsDiscretizer

[Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.KBinsDiscretizer.html)

`KBinsDiscretizer` is used to **discretize continuous features into bins**.

### 🔹 Important Parameters

1. **bins**  
   - Number of bins for each feature (can be an integer or array specifying bins per feature).  

2. **strategy**  
   - How to create bins:  
     - `'uniform'` → Equal width  
     - `'quantile'` → Equal frequency  
     - `'kmeans'` → KMeans clustering  

3. **encode**  
   - How to encode the binned features:  
     - `'ordinal'` → Integers (0,1,2…)  
     - `'onehot'` → One-Hot Encoding  
     - `'onehot-dense'` → Dense one-hot array


### 🔹 Example
- Feature: **Age**, 4 bins, strategy=`'quantile'`, encode=`'ordinal'`  
- Ages get mapped to bins 0, 1, 2, 3 based on distribution.

## Custom/Domain Based Binning

- Bins are **manually defined** based on **domain knowledge** or **business rules** rather than automatic statistical methods.

### How It Works
- Decide meaningful intervals or categories for a feature based on understanding of the data.  
- Assign each value to the corresponding bin.

### Example
Feature: **Age**  
- 0–18 → Child  
- 19–40 → Adult  
- 41–60 → Middle-aged  
- 61+ → Senior  

Feature: **Income**  
- 0–50k → Low  
- 50k–150k → Medium  
- 150k+ → High  

- Advantage: **Highly interpretable** for business decisions.  
- Limitation: May **ignore natural distribution** or skew in data.

- **Custom / Domain-Based Binning** cannot be done directly using `scikit-learn`.  
- Typically implemented using **Pandas `cut()` or `apply()`** to assign values to bins based on custom intervals.
