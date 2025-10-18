# Normalization

- It is a technique often applied as part of data preparation for ML. 
- Goal: change the values of numeric columns in the dataset to use a **common scale**, without distorting differences in the ranges of values or losing information.

<img width="1024" height="537" alt="image" src="https://github.com/user-attachments/assets/42cb769e-9526-4db7-8fb9-be1cf35dc3fa" />

> 90% times we use **MinMax Scaling**

## MinMaxScaling

<img width="1400" height="933" alt="image" src="https://github.com/user-attachments/assets/8de236e5-6254-4f97-bc73-741dbd8fed66" />

#### Mean Normalizatoin

<img width="370" height="138" alt="image" src="https://github.com/user-attachments/assets/9e80af6a-ebe8-4c8a-b99f-d775d9ba1204" />

- Mean centering
- Range: [-1, 1]

<img width="130" height="100" alt="Screenshot 2025-10-18 at 9 39 19 PM" src="https://github.com/user-attachments/assets/221de672-0815-4123-bcb7-7c5483ef8020" />

- Rarely used(No class in sklearn for this, you have to manually implement it)

- Useful in algorithms where you need centered data(**Can use Standardization for that purpose**)

#### MaxAbsScaling

<img width="805" height="266" alt="image" src="https://github.com/user-attachments/assets/fd132e61-124f-4813-98a6-9441d397e024" />

- Sklearn Class : `MaxAbsScaler`
- Useful in sparse data, matrix(where you have zeros)

#### Robust Scaling

<img width="1400" height="933" alt="image" src="https://github.com/user-attachments/assets/f05f4c5e-912e-4457-ae98-105356227cec" />

- Where:
    - X is the feature value.
    - Median is the middle value of the feature values when sorted.
    - IQR (Interquartile Range) is the difference between the 75th percentile (Q3) and the 25th percentile (Q1).

