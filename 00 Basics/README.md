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
4. Association rule learning - Association rule learning is a technique for discovering relationships between items in a dataset. It identifies rules that indicate the presence of one item implies the presence of another item with a specific probability. For example, 93% of customers who purchased item A also bought item B. This rule helps identify frequent itemsets, showing which products are commonly bought together. Association rule learning can be used to understand customer purchasing behavior and optimize product recommendations or placements.

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
6. Overfitting: Memorise data.

7. Underfitting: Opposite of overfitting
![image](https://github.com/user-attachments/assets/cd271d32-6c10-4b87-8c34-49f7d9880bdb)

8. Software Integration
9. Offline Learning/ Deployment
10. Cost involved

# Applications of Machine Learning
1. Retail - Amazon/Big Bazaar
- Retailers use ML algorithms to analyze customer preferences and shopping behavior to provide tailored product recommendations, enhancing customer experience and increasing sales.
- Machine learning uses association rule learning to identify patterns in customer purchase behavior. This helps retailers understand which products are frequently bought together (e.g., bread and butter) and optimize store layouts, cross-selling strategies, and product placements accordingly.
2. Banking and Finance
3. Transportation
- OLA: Machine learning dynamically adjusts fares based on real-time demand and supply. Prices are higher during peak demand periods (e.g., rush hours or bad weather) to incentivize more drivers to come online and meet the increased demand.
- Swiggy : When a delivery executive has multiple orders from the same or nearby restaurants, ML algorithms group these orders and create the most efficient delivery route.
4. Manufacturing - Tesla
- Machine learning models predict equipment failures before they occur by analyzing historical data and real-time sensor readings
5. Consumer Internet - Twitter
- Machine learning is used to analyze public sentiment in tweets, helping brands and governments understand public opinion on various topics, products, or events. Positive or negative sentiment extracted from tweets can indicate potential movements in stock prices. 


# Machine Learning Development Life Cycle
![image](https://github.com/user-attachments/assets/6a6613ac-9cb3-47d5-a1c2-c2fc726ea956)

1. **Frame the problem**
- Understand what problem you need to solve.
- Who are your target customers?
- How much will it cost? 
- How many team members are needed?
- How will the final product look?
- Is the model supervised or unsupervised? 
- Will it run in online mode or batch mode?
- Which algorithms will be most effective?
- Where will you get your data from?
2. **Gathering the Data**
- CSV files
- Fetch data using APIs.
- web scraping
- Build a data warehouse from a database using the ETL (Extract, Transform, Load) process, then fetch the data from the warehouse for analysis.
- For large datasets, data is processed in clusters using tools like Apache Spark.
3. **Data preprocessing**
- Remove duplicates, missing values, outliers
- Scale values: Apply standardization to scale features to a mean of 0 and a standard deviation of 1, ensuring uniformity across variables.
4. **Exploratory Data Analysis(EDA)**
- helps in Visualization: Draw graphs such as histograms, scatter plots, box plots, and heatmaps to identify patterns, trends, and relationships.
- Univariate Analysis: Examine individual columns to understand their distribution (e.g., histograms for numerical data and count plots for categorical data).
Bivariate Analysis: Analyze relationships between two variables using scatter plots, box plots, or correlation heatmaps.
- outlier detection
- convert imbalanced data into balanced
5. **Feature Engineering and Selection**
- Features: Input columns in the dataset used to predict the output.
- Feature Engineering: Create new features by combining or transforming existing columns to improve model performance.
- Feature Selection: Identify and remove columns that do not significantly impact the target variable.
6. **Model Training, Evaluation and Selection**
- Training: Train different algorithms by providing them the same dataset, allowing each to learn patterns and relationships.
- Model Evaluation: Assess model performance using metrics such as accuracy, precision, recall, F1-score, and ROC-AUC.
- Model Selection: Optimize performance by tuning hyperparameters using methods like grid search or random search.
- Ensemble Learning: an ensemble model combines several individual models to produce more accurate predictions than a single model alone.
7. **Model Deployment**
- Save the model as a binary file (using pickle).
- Convert the binary file into an API (using Flask or FastAPI) that takes input in JSON format and returns predictions.
- The user inputs data through a form on your website.
- The input is sent to the Python app, which communicates with the API for predictions.
- The API sends the prediction back in JSON format, and the website displays the result.
8. **Testing**
- Beta Testing: Test the model with loyal users, gather their feedback, and identify any issues or improvements needed.
- A/B Testing: Compare two versions (A and B) of the model or feature to determine which one performs better.
9. **Optimise**
- Backup of Model: Keep a backup of the trained model to prevent data loss.
- Data Backup: Regularly back up the dataset to protect against accidental loss or corruption.
- Load Balancing: Use load balancing to handle high website traffic, ensuring smooth performance even with increased user requests.
- Re-training (Model Rotation): Decide the frequency for re-training the model to maintain its accuracy as new data comes in.
- Other Optimizations: Continuously monitor and improve system performance, including scalability, efficiency, and security.
