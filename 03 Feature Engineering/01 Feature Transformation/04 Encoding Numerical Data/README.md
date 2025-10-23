# Encoding Numerical Features

1. Discretization(Binning)
2. Binarization

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
