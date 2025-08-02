# DataMining_GroupProject_Group2
Apply the full data pipeline from ETL → Data Mining → Insights &amp; Storytelling to a chosen dataset or  the previously cleaned data. Use mining techniques to uncover patterns, trends, and insights that can  inform decision-making.

# TEAM MEMBERS & Contributions
- Mitchel_413 - Responsible for the Data Mining
- Queen_897 - Responsible for Data Cleaning and Enrichment.
- Claire_470
- Kyra_619
- Esther_399 -  Responsible for EDA & dashboard visualizations.
- Julie_996 -  Responsible for EDA & dashboard visualizations.

# Data Cleaning and Enrichment (By Queen)
This script processes finance_dataset.csv by cleaning (handling missing values, standardizing formats, removing outliers) and enriching with calculated fields (Profit_Margin, Revenue_Growth).
# Section by Queen Data Extraction
<img width="749" height="403" alt="image" src="https://github.com/user-attachments/assets/601a18b3-b794-4c4f-9198-790bee87905b" />

# Load Data
<img width="893" height="664" alt="image" src="https://github.com/user-attachments/assets/6844baf4-60fd-4cce-b63e-c677719afcda" />
# Loaded Original data Results
<img width="1208" height="719" alt="image" src="https://github.com/user-attachments/assets/390348a1-c79f-47bf-a874-1b17f76c1149" />

# Data Cleaning 
<img width="1124" height="569" alt="image" src="https://github.com/user-attachments/assets/e7cd4401-6f0d-4b74-aabd-e7b0af4c0f95" />
# Results for clean Data
<img width="870" height="721" alt="image" src="https://github.com/user-attachments/assets/751ecc98-b8f0-4d8a-be3c-f89582d84c77" />

# Data Enrichment
<img width="924" height="422" alt="image" src="https://github.com/user-attachments/assets/6bb50240-f444-41e5-b6f4-e7e4b9b24fac" />
# Results for enriching data
<img width="858" height="670" alt="image" src="https://github.com/user-attachments/assets/cfe934dd-ca25-45ba-b490-23ba580548da" />

# Exploratory & Statistical Analysis (By Julie & Esther)

This section focuses on exploring and statistically analyzing the dataset to uncover meaningful patterns, trends, and differences across companies based on their financial indicators.

---

## Tools Used
- **Pandas**: For data manipulation and grouping.
- **Seaborn & Matplotlib**: For data visualization (boxplots, barplots, correlation heatmaps).
- **SciPy Stats**: For statistical hypothesis testing (ANOVA and t-tests).
- **NumPy**: For numerical operations.
- **itertools**: For efficient pairwise testing combinations.

---

##  1. Distribution Analysis
- **Objective**: Understand the distribution shapes of key financial variables.
- **Approach**:
  - Plotted histograms for variables like `Revenue_Growth`, `EPS`, and `Stock_Price`.
  - Interpreted symmetry, spread, and outliers.
- **Findings**:
  - `EPS` and `Stock_Price` are approximately normal.
  - `Revenue_Growth` has both positive and negative values, indicating company-level performance shifts.

---

##  2. Categorical Feature Frequency
- **Objective**: Examine how data is distributed across companies and time periods.
- **Approach**:
  - Created countplots for `Company` and `Date`.
- **Findings**:
  - All five companies are equally represented.
  - More entries are concentrated in recent years.

---

##  3. Correlation Matrix
- **Objective**: Identify linear relationships between numerical variables.
- **Approach**:
  - Calculated correlation matrix and visualized it using a heatmap.
- **Key Insights**:
  - `Stock_Price` is highly correlated with `Market_Cap_Billions`, `EPS`, and `Net_Income_Millions`.
  - `Profit_Margin` shows positive relationships with both `EPS` and `Net_Income_Millions`.
  - `Revenue_Growth` has weak correlations with other variables.

---

##  4. Group Comparisons (Company-Level)
###  Boxplot Visualization
- Compared `Net_Income_Millions` across companies using boxplots.
- Observed variations in medians and spreads among different companies.

###  ANOVA Test
- **Objective**: Test whether mean `Net_Income_Millions` significantly differs between companies.
- **Result**:
  - F-statistic: **498.32**, P-value: **< 0.0001**
  - Strong evidence of differences in net income across companies.

###  Pairwise T-tests
- **Objective**: Identify which company pairs differ significantly.
- **Method**: Performed Welch’s t-tests for all pairs (unequal variance).
- **Results**:
  - All company pairs showed statistically significant differences (p < 0.01).
  - `TechCorp` and `FinServ` had significantly higher incomes compared to others.
  - `RetailCo` sits in the middle.

---

##  Summary of My Contributions
- Visualized distribution of numerical and categorical variables.
- Analyzed inter-variable relationships using correlation heatmaps.
- Conducted group-level analysis using ANOVA and pairwise t-tests.
- Interpreted statistical results to draw company-level performance insights.

## Data Mining Techniques(By Mitchel and Kyra)
File name : notebooks/`3-data_mining.ipynb`
**Clustering with K-Means**
- The codes loads the cleaned finance dataset and selects only numeric columns.
- It standardizes these features so they have a mean of 0 and standard deviation of 1.
- The "elbow method " is used to help choose the best number of clusters by plotting inertia for different values of k.
- K-Means clustering is then applied(k=3) and each record is assigned to a cluster.
- Finally, a scatter plot visualizes the clusters using the first two features.
![alt text](image.png)
![alt text](image-1.png)

**Anomaly Detection with Isolation Forest**
- The code uses the same numeric features from the dataset.
- It fits an Isolation Forest model, which is designed to detect outliers or anomalies in the data.
- The results are visualized in a scatter plot, with normal points in blue and anomalies in red.
![alt text](image-2.png)

**Classification and Decision Tree Analysis**
- First, create a target column for classification.

- This code block demonstrates how to train and evaluate a Decision Tree classifier to predict whether a company in the finance dataset is considered "High Performance."
```
# Train and evaluate Decision Tree classifier
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.metrics import classification_report, confusion_matrix

features = ['Stock_Price', 'Revenue_Millions', 'Net_Income_Millions',
            'Market_Cap_Billions', 'EPS', 'Profit_Margin', 'Revenue_Growth']
X_cls = df[features]
y_cls = df['High_Performance']

X_train, X_test, y_train, y_test = train_test_split(X_cls, y_cls, test_size=0.2, random_state=50)

clf = DecisionTreeClassifier(random_state=50)
clf.fit(X_train, y_train)

y_pred = clf.predict(X_test)

print("Confusion Matrix:")
print(confusion_matrix(y_test, y_pred))

print("\nClassification Report:")
print(classification_report(y_test, y_pred))
```
- First, it imports the necessary libraries for model training, evaluation, and visualization.
-  The `features` list specifies which columns from the dataset will be used as input variables (such as stock price, revenue, net income, market cap, EPS, profit margin, and revenue growth).
- The target variable, `y_cls`, is the 'High_Performance' column, which likely indicates whether a company meets a certain performance threshold.
- The data is split into training and testing sets using `train_test_split`, with 20% of the data reserved for testing.
- Finally, the code prints out a confusion matrix and a classification report. 
- The confusion matrix shows how many predictions were correct or incorrect for each class, while the classification report provides metrics such as precision, recall, f1-score, and accuracy, giving a detailed summary of the model's performance.

