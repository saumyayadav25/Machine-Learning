# Logistic Regression

### Pre-requisite
- Data should be **linearly separable**.

## Perceptron Trick (Intuition Behind Logistic Regression)

> Note: Perceptron **does not guarantee the best possible solution**. It only finds *a* separating boundary if one exists.

Example :
- X-axis: CGPA  
- Y-axis: IQ  
- Blue points: not placed  
- Green points: placed  

#### Decision Boundary Representation

In logistic regression (and perceptron), the decision boundary is **not written as**:
```
y = mx + b  
```
Instead, we use the **general equation of a line**:
```
Ax + By + C = 0
```
Rewriting in feature form:
```
A x₁ + B x₂ + C = 0
```
Where:
- x₁ = CGPA  
- x₂ = IQ  
- C = intercept  

If there are 3 input features:
```
A x₁ + B x₂ + C x₃ + D = 0
```
and so on...

Goal:
- Find parameters **A, B, C (and more if needed)** such that the data is correctly classified.

#### Perceptron Trick: Step-by-Step

1. **Initialize weights randomly**  
   Example:
   - A = 1
   - B = 1
   - C = 0

2. **Run a loop**
   - Either for a fixed number of iterations (e.g., 1000)
   - Or until convergence (no misclassified points left)

3. **At each iteration**
   - Pick a **random data point** (student)
   - Check whether the current line classifies it correctly

4. **If the point is correctly classified**
   - Do nothing
   - No change in A, B, C

5. **If the point is misclassified**
   - Update A, B, C
   - Move the decision boundary slightly **towards the misclassified point**
   - So that this point is no longer misclassified in future iterations

Intuition:
- A misclassified blue point will “pull” the line towards itself.
- A misclassified green point will push the line away.

6. **Repeat**
   - Continue until all points are correctly classified
   - Or maximum iterations are reached

<img width="534" height="398" alt="Screenshot 2025-12-30 at 5 37 38 PM" src="https://github.com/user-attachments/assets/a0c8ed3e-fc97-4d7f-8d90-04dc19a487e5" />

#### How to Label Regions (Positive / Negative Side of a Line)

Tool used for visualization: https://www.desmos.com/calculator

Consider the line:
```
2x + 3y + 5 = 0
```
This line divides the plane into **two regions**.

1. Step 1: Pick any test point
Choose a point **not lying on the line**.  
Common choice: (0, 0)

2. Step 2: Substitute the point into the equation

2(0) + 3(0) + 5 = 5

3. Step 3: Decide the region

- If 2x + 3y + 5 > 0  
  → the point lies in the **positive region**
- If 2x + 3y + 5 < 0  
  → the point lies in the **negative region**

So for this example:
- (0, 0) gives a positive value  
- Hence, the side containing (0, 0) is the **positive side of the line**

### Transformations (Perceptron Updates)

General form of a line:
```
ax + by + c = 0
```

#### Effect of Changing Parameters

- Changing **c**  
  → The line shifts **up or down parallelly** (no change in slope).

<img width="302" height="239" alt="Screenshot 2025-12-30 at 5 53 50 PM" src="https://github.com/user-attachments/assets/7e77dec6-422c-4725-9ba3-6ad16dab2f78" />

- Changing **a**  
  → Line rotates around the **y-axis**  
  → Slope changes due to y-axis rotation.

- Changing **b**  
  → Line rotates around the **x-axis**  
  → Slope changes due to x-axis rotation.

<img width="605" height="345" alt="Screenshot 2025-12-30 at 5 56 17 PM" src="https://github.com/user-attachments/assets/fdb91f2a-d5fe-4979-9e42-63fbbbd022b8" />

#### Applying Transformation (Perceptron Trick)

Assume the current line is:
```
2x + 3y + 5 = 0
```
There are misclassified points.

**Case 1: Blue point misclassified as Green**

Misclassified point:
- (4, 5) → Blue but predicted Green

Perceptron trick:
- Add a constant 1 to the point  
  → (4, 5, 1)

Write coefficients of the line:
```
2   3   5  
4   5   1  
```
Subtract (move towards +ve region):
```
2−4   3−5   5−1  
= −2  −2   4
```
New decision boundary:
```
−2x − 2y + 4 = 0
```

**Case 2: Green point misclassified as Blue**

Misclassified point:
- (1, 3) → Green but predicted Blue

Add constant 1:
- (1, 3, 1)

Now add (move towards −ve region):
```
2   3   5  
+1  +3  +1  
= 3   6   6
```
New decision boundary:
```
3x + 6y + 6 = 0
```

#### Direction Rule
- Move towards **positive region** → subtract
- Move towards **negative region** → add

#### Problem with Large Updates

Direct addition/subtraction causes **very large jumps** in the decision boundary.  
This makes learning unstable.

#### Learning Rate (η)

To make updates gradual, we introduce a **learning rate**.

Common values:
- 0.01
- 0.1 (depends on data)

Now multiply point coordinates by learning rate before updating.

Example:
- Point (1, 3, 1)
- Learning rate = 0.01

Becomes:
- (0.01, 0.03, 0.01)

#### Final Update Rule
```
coeff_new = coeff_old − η × coordinates
```
This ensures:
- Small, controlled updates
- Stable convergence
- Smoother movement of the decision boundary

<img width="527" height="365" alt="Screenshot 2025-12-30 at 6 50 36 PM" src="https://github.com/user-attachments/assets/88fa454c-3bec-4412-af2a-89e320b34bb6" />

### Algorithm (Perceptron Learning Rule)

Till now, we were writing the line equation as:
```
ax + by + c = 0
```
We rewrite it using weights:
```
w₀ + w₁x₁ + w₂x₂ = 0
```
Where:
- w₀ = c  
- w₁ = a  
- w₂ = b  

To make it uniform, we introduce an extra feature:
```
x₀ = 1 (added as a new column for all rows)
```
Now the equation becomes:
```
w₀x₀ + w₁x₁ + w₂x₂ = 0
```
This can be written in summation form:
```
Σ wᵢxᵢ = 0
```
This is the **general equation of the decision boundary**.

Here:
- x₁ = CGPA  
- x₂ = IQ  

### Prediction Rule

For a given input x:

- If Σ wᵢxᵢ ≥ 0  
  → model predicts **placement ho jayega**
- If Σ wᵢxᵢ < 0  
  → model predicts **placement nahi hoga**

This operation is a **dot product** between weight vector `w` and input vector `x`.

It can also be written in **matrix form**:

<img width="547" height="338" alt="Screenshot 2025-12-30 at 7 07 09 PM" src="https://github.com/user-attachments/assets/5588bf35-ba9e-4508-94bf-00221d189ac1" />

### Perceptron Algorithm

1. Decide:
   - Number of epochs (e.g. 1000)
   - Learning rate η (e.g. 0.01)

2. Loop for given epochs:
```
for i in range(epochs):
- Randomly select a data point (student)
- Compute prediction using Σ wᵢxᵢ
```

Cases:

- If point belongs to **negative class** 

  and Σ wᵢxᵢ ≥ 0  

  (model predicts placement but actual is no placement)

  Update:
  ```
  w_new = w_old − η × xᵢ
  ```
- If point belongs to **positive class**  

  and Σ wᵢxᵢ < 0  

  (model predicts no placement but actual is placement)

  Update:
  ```
  w_new = w_old + η × xᵢ
  ```
<img width="504" height="336" alt="Screenshot 2025-12-30 at 7 12 29 PM" src="https://github.com/user-attachments/assets/e1689aa8-662e-4aaf-b9f2-a9bdb7e6a17f" />

## Simplified Algorithm

Instead of handling two separate conditions, we can use a single update rule.

Update formula:
```
w_new = w_old + η (yᵢ − ŷᵢ) xᵢ
```
Where:
- yᵢ = actual label  
- ŷᵢ = predicted label  

<img width="517" height="364" alt="Screenshot 2025-12-30 at 7 19 10 PM" src="https://github.com/user-attachments/assets/ac2843b5-d963-4cda-85c4-659babe81ef7" />
 
### Final Simplified Loop

for i in range(epochs):
- Select a random student
- Update weights as:
```
w_new = w_old + η (yᵢ − ŷᵢ) xᵢ
```
<img width="447" height="167" alt="Screenshot 2025-12-30 at 7 21 08 PM" src="https://github.com/user-attachments/assets/7c417d47-6bea-4196-9b13-222ad3e7f98b" />