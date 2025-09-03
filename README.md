# 🧾 Tunisian Electricity & Gas Billing History — Data Preprocessing Summary

This notebook presents a comprehensive preprocessing workflow for the billing history dataset of the Tunisian electricity and gas company, covering customer records from 2005 to 2019. The objective is to prepare the data for analysis by exploring its structure, handling missing values, transforming categorical features, and cleaning irrelevant columns. These steps are essential for ensuring data quality and analytical reliability.

## ⚙️ Workflow Overview

### 1. Data Loading and Preview
The dataset was loaded using `pandas.read_csv()` and the first 10 rows were displayed to inspect the structure. These rows were stored in a variable named `client_0_bills`. The data type was confirmed to be a `DataFrame`, which supports tabular operations and is ideal for preprocessing tasks.

### 2. Dataset Inspection
Using `.info()`, we retrieved metadata including:
- Number of rows and columns
- Data types of each feature
- Memory usage
- Presence of categorical variables

This step helped identify which columns required transformation and which might contain missing values.

### 3. Handling Missing Values
Missing values were inspected using `.isnull().sum()`. Based on the nature of each column:
- **Numerical features** were imputed using the **median**, which is robust to outliers and preserves central tendency.
- **Categorical features** were imputed using the **mode**, ensuring the most frequent category is retained.

This strategy maintains data integrity while minimizing bias introduced by imputation.

### 4. Descriptive Analysis
The `.describe()` method was applied to numerical columns to summarize distributions, including mean, standard deviation, min/max values, and quartiles. This provided insight into billing patterns and potential anomalies.

### 5. Filtering Specific Client Records
To isolate billing records for `train_Client_0`, two methods were used:
- Boolean indexing: `df[df['client_id'] == 'train_Client_0']`
- Query method: `df.query("client_id == 'train_Client_0")`

This demonstrated flexible filtering techniques for targeted analysis.

### 6. Encoding Categorical Variables
The `counter_type` column was transformed using `LabelEncoder` from `sklearn.preprocessing`. This converted string categories into numeric codes, making the feature compatible with machine learning models and statistical analysis.

### 7. Feature Removal
The `counter_statue` column was dropped using `.drop()` due to irrelevance or redundancy. Removing unnecessary features helps reduce noise and improve model performance.

## 📌 Outcome

The dataset is now cleaned, structured, and ready for further analysis or modeling. Each preprocessing step was documented to ensure reproducibility and facilitate collaborative review. 