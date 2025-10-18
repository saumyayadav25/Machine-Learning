# Standardization (aka Z-score normalization)

- Converts the **Mean (μ) to 0**
- Converts the **Standard Deviation (σ) to 1**

> ⚠️ Standardization does **not** remove the impact of outliers — it only rescales the data around the mean and standard deviation.

### When to use Standardization
<img src="https://miro.medium.com/max/1400/1*qRmiffZgkNaXnTBZwDafCA.png">

### When it's not needed:
- Decision Trees: no need of scale in comparison.
- Random Forest
- Gradient Boost
- XG Boost