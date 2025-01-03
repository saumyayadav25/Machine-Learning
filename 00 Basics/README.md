# What is machine learning? 
Machine learning is a field of computer science that uses statistical techniques to give computer systems the ability to "learn" with data, without being explicitly programmed.

![Traditional programming vs Machine learning](https://github.com/user-attachments/assets/9e503178-f54f-43b4-ba72-051c94a89d28)

# AI vs ML vs DL vs generative AI
![image](https://github.com/user-attachments/assets/96a24ede-dfc9-4162-b6dd-f7e554881c02)

# Types of Machine Learning
![image](https://github.com/user-attachments/assets/d247ab3d-8730-4a09-bd92-b94017ad7ea4)

## Supervised Machine Learning
Supervised learning is defined as when a model gets trained on a “Labelled Dataset”. Labelled datasets have both input and output parameters. In Supervised Learning, algorithms learn to map points between inputs and correct outputs; give output for new input.
#### Data is of two types - categorical and numerical

**Types of supervised learning**
1. Regression - output column is numerical
2. Classification - output column is categorical 

## Unsupervised Machine Learning
- have only input.

The primary goal of Unsupervised learning is often to discover hidden patterns, similarities, or clusters within the data.

**Types of unsupervised learning**
1. Clustering - Clustering is the process of grouping data points into clusters based on their similarity.
2. Dimensionality reduction - when you have a lot of input columns; remove extra columns, and merge related columns into single column using feature extraction techniques like PCA. Reduce the dimensionality of data while preserving its essential information.
3. Anomaly detection - detect and remove outliers from systems
4. Association rule learning - Association rule learning is a technique for discovering relationships between items in a dataset. It identifies rules that indicate the presence of one item implies the presence of another item with a specific probability.

## Semi - supervised Machine Learning
partially supervised and partially unsupervised.

eg: Google Photos uses facial recognition technology to identify people and group their photos automatically.

## Reinforcement Machine Learning
Reinforcement machine learning algorithm is a learning method that interacts with the environment by producing actions and discovering errors. In this technique, the model keeps on increasing its performance using Reward Feedback to learn the behavior or pattern. example: self driving cars.

# Offline(Batch) learning vs Online Learning
production: server on which our code is going to run.
### Batch learning
Type of learning where the model undergoes a training process from the entire batch of data.

No incremental training.

Once trained, the model is not updated by default; the only way to rebuild a given model is restructuring it with new data.

![image](https://github.com/user-attachments/assets/7cdebe32-7d5b-49c6-a551-021f6cbfa070)

### Online learning
Machine learning with online learning is completed in stages, where the learned model is updated with a new model as new data arrives.

Done incrementally.

![image](https://github.com/user-attachments/assets/840da2a9-3949-4338-ab15-e0d3e846efce)

eg: chatbots

When to use?
- when there is a concept drift(nature of problem keeps on changing)
- cost effective (due to working in small chunks)

#### Learning Rate
rate at which model learns.

#### Out of core learning
When data is too large that you cannot train using batch learning.

Convert huge data into small chunks of data which can be further trained using batch learning or online learning.

![image](https://github.com/user-attachments/assets/da094cc1-8bb0-4ec9-8afe-66b2b1df326e)


# Instance Based Learning vs Model Based Learning
Instance Based Learning - memorising

Model Based Learning - generalising

### Instance Based Learning 
The machine compares the new data to the instances it has seen before and uses the closest match to make a prediction.

In instance-based learning, no model is created. Instead, the machine stores all of the training data and uses this data to make predictions based on new data. Instance-based learning is often used in pattern recognition, clustering, and anomaly detection.

An example of instance-based learning is the k-nearest neighbor algorithm.

![image](https://github.com/user-attachments/assets/e7393420-26f7-408c-8907-a72dc5073d7f)


### Model Based Learning
Model-based learning involves creating a mathematical model that can predict outcomes based on input data. The model can be thought of as a set of rules that the machine uses to make predictions.

In model-based learning, the training data is used to create a model that can be generalized to new data. The model is typically created using statistical algorithms such as linear regression, logistic regression, decision trees, and neural networks.

![image](https://github.com/user-attachments/assets/82834343-435a-4fb3-987c-27249d453174)

![image](https://github.com/user-attachments/assets/1f640901-5b31-4c68-8e08-8f490ed4b3be)


# Challenges in Machine Learning
1. Data Collection
- API
- Web Scraping
2. Insufficient Data / Unlabelled Data
3. Non Representative Data
- The training data must cover all cases that are already occurred as well as occurring.
- Sampling Noise: If data is collected inconsistently or if significant portions are omitted, the resulting gaps or biases in our data can be misleading.
- Sampling bias: occurs when a dataset does not reflect the realities of the environment in which a model will run.
4. Poor Quality Data
5. Irrelevant Features
6. Overfitting

Memorise data.

7. Underfitting

Opposite of overfitting
![image](https://github.com/user-attachments/assets/cd271d32-6c10-4b87-8c34-49f7d9880bdb)

8. Software Integration
9. Offline Learning/ Deployment
10. Cost involved
