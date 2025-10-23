# Function Transformer

Used to apply **mathematical transformations** to features for reducing skewness and making data closer to a **normal distribution**.

## Log Transform

- Used for **right-skewed data** (long tail on the right).  
- Converts large values closer together → makes distribution normal.  
- ❌ Cannot be used on **negative** values.  
- _Example_: Income, Price, Population

## Reciprocal Transform

- Formula → `1/x`  
- **Large values become small**, small values become large.  
- Can help with **both types of skewness**, but mostly right-skewed.  

## Square Transform

- Formula → `x²`  
- Used for **left-skewed data** (long tail on the left).  


## Square Root transform
- Formula → `√x`  
- Mildly reduces right skewness.  
- Not used very often, but sometimes helpful for count-type data (e.g., number of calls, visits).  
