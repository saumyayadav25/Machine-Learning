# What are tensors (n-dimensional arrays)?

A **tensor** is a container for storing numbers.

![image](https://github.com/user-attachments/assets/f81daa68-5984-423c-a861-8e197dff4be8)

### 0D Tensor/ Scalar

It is a single numerical value.

### 1D Tensor/ Vector/ 1D array

It is a list or sequence of numbers.

### 2D Tensor/ Matrices

It is a table of numbers with rows and columns.

### Rank, Axes, Shape

- **Rank**: Number of axes (dimensions).
- **Shape**: The number of items in each axis. For example, a 3x3 matrix has a shape of (3, 3).
- **Size**: The total number of elements in the tensor.  
  - For example:  
    - Scalar: Size = 1  
    - 1D Tensor: Size = 3 (for [1, 2, 3])  
    - 2D Tensor (3, 3): Size = 9 (3 * 3)

**Example of 1d tensors** 

1d tensor, but 3d vector:

<img width="446" alt="img" src="https://github.com/user-attachments/assets/43ef6a11-1bb1-45a8-bfba-0efee097ee44" />

**Example of 2d tensors** 

2d tensor, but 3d vector:

<img width="279" alt="img" src="https://github.com/user-attachments/assets/8193e923-b603-49f5-8738-4ec3aeacc6ac" />

**Example of 3d tensors** 

shape: (3,2,4)

size/number of items: 24

<img width="449" alt="img" src="https://github.com/user-attachments/assets/b3d36196-a4d6-4ea8-b0f9-306af3cb8f3b" />

**Example of 4d tensors**

1 color image:

let shape of 1 channel: (1200,800)

Shape: (3, 1200, 800) → 3D Tensor  

50 color images: (50, 3, 1200, 800) → 4D Tensor

<img width="426" alt="img" src="https://github.com/user-attachments/assets/d781b008-e592-432e-8e45-8c8cb8632169" />

**Example of 5d tensors**

- videos: frames per second

1 frame : 1 image

<img width="464" alt="img" src="https://github.com/user-attachments/assets/445b944b-b1e8-4ab9-bc37-53bc32e7dec3" />
