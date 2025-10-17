# Feature Engineering

- Process of using **domain knowledge** to extract features from raw data. These features can be used to improve the performance of ML algorithms.

<img width="1400" height="732" alt="image" src="https://github.com/user-attachments/assets/034b8141-02be-490c-ab6a-a89ec69664a2" />

## Feature Transformation

### 1. Missing Values Imputation

When you will work with real-life data.You will realize that the data you are working with has missing values.It can be due to:

- Data is not being intentionally filled, especially if it is an optional field.
- Data being corrupted.
- Human error.
- If it was a survey, participants might quit the survey halfway.
- If data is being processed automatically by computer applications, then a malfunction could cause missing data. e.g., a sensor recording logs is malfunctioning.
Fraudulent behavior of intentionally deleting data.

-  Either remove the missing values or fill in the missing Value(**Imputation**).

### 2. Handling Categorical Values

<img width="1061" height="403" alt="image" src="https://github.com/user-attachments/assets/d4e4ce54-3546-4ab0-88b0-fae443b02fc0" />

The problem with this kind of data is that Scikit Learn can handle only numerical data. So you need to convert categorical values to numerical values.

### 3. Outlier Detection

<img width="1079" height="548" alt="image" src="https://github.com/user-attachments/assets/eafc18b4-5df2-4f9c-ac3c-51646a9def64" />

### 4. Feature Scaling

- It means bringing features on the same scale.

Age is in the range of tens, and salary is in the range of thousands.

<img width="758" height="619" alt="image" src="https://github.com/user-attachments/assets/644a69e6-bd00-46d8-897c-3fdf6a92d4d0" />

Imagine you are working on an algorithm. which works by calculating the Euclidian distance between two points (KNN).

<img width="286" height="155" alt="Screenshot 2025-10-17 at 8 31 29 PM" src="https://github.com/user-attachments/assets/f2147352-5a07-4d99-9580-beda521109ea" />

Feature scaling is important in some algorithms like KNN to prevent features with larger magnitudes from dominating the distance calculation, ensure fair comparisons between features, improve convergence speed, and reduce the influence of outliers.

---

## Feature Construction

In feature construction, you create new columns based on your **domain knowledge**.

<img width="1226" height="350" alt="image" src="https://github.com/user-attachments/assets/ebd409dd-488c-437f-9038-bbb06b16e73c" />

“sibsp” tells how many siblings and spouses you are traveling with, and “patch” tells how many parents and children you are traveling with.

In this scenario, what you can do is add them up and create a new column called “family” which represents the number of family members traveling with.

---

## Feature Selection

The best example of feature selection is the MNIST dataset. The MNIST dataset is a collection of 70,000 labeled images of handwritten digits (0–9). It is commonly used as a benchmark dataset for machine learning and computer vision tasks. Each grayscale image has a resolution of 28x28 pixels and is used for training and testing models in tasks such as digit recognition and image classification.

<img width="400" height="386" alt="image" src="https://github.com/user-attachments/assets/517f8fb7-92ee-4861-ad34-cb74b91062a5" />

They have converted images to table, where every row is one image. In this dataset, there are 784 features(each pixel is a feature). This huge dimensional ML model takes time train and run

<img width="989" height="333" alt="image" src="https://github.com/user-attachments/assets/26f8c7a8-af4e-46e1-b2db-4fe165fdd844" />

- Consider only pixels which are actually important(center region in image).

---

## Feature Extraction

- Process of **creating new features** from existing ones **programmatically**.  
- It helps to make data more informative and compact.  
- **Not the same as Feature Construction** (which is manual and domain-based).

<img width="264" height="172" alt="image" src="https://github.com/user-attachments/assets/36551829-41ac-431b-9c66-b90fd80206cd" />

**Example:**  
In a housing dataset, both *rooms* and *washrooms* affect the price.  
Instead of using both, combine them into one feature — **area (sq. ft.)** — since it better represents the house size.
Rather than going for two features, go for one feature that is sq. ft.

🧠 **Key Idea:**  
Extract features that capture the same information in a simpler or more meaningful form.
