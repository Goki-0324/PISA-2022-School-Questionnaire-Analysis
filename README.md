# PISA-2022-School-Questionnaire-Analysis
## 📌 Project Overview
This repository contains Python code for performing unsupervised clustering analysis on school questionnaire data from the OECD PISA (Programme for International Student Assessment) survey.  
The project includes:
- Data preprocessing
- Automatic detection and reconstruction of Likert-scale items
- Encoding of nominal variables
- Dimensionality reduction using PCA
- School clustering using K-means
- Visualization and interpretation of results
## 📂 About the Data (Important)
This repository **does not include any PISA data files** (e.g., .sav, .csv, or any derived datasets).  
PISA data is copyrighted by the OECD, and **redistribution is strictly prohibited** under the usage agreement.  
Therefore, the following files are not included:
- Extracted Japanese school dataset (df_school.csv)
- Any processed or transformed datasets
- Any files derived from the original .sav data
### 🔗 How to Obtain the Data
Please request and download the PISA datasets directly from the OECD website.  
https://www.oecd.org/en/about/programmes/pisa.html
### 🛠 How to Use This Repository
#### 1. Obtain the PISA dataset
Download the school questionnaire .sav file from the OECD website after completing the required application.
#### 2. Extract Japanese school data
```python
import pyreadstat

df, meta = pyreadstat.read_sav("CY07_MSU_SCH_QQQ.sav")
df_school = df[df["CNT"] == "JPN"].copy()

# (Optional) Save for faster processing
df_school.to_csv("df_school.csv", index=False)
```
#### 3. Load the CSV and run the analysis
```python
import pandas as pd

df_school = pd.read_csv("df_school.csv")
# Continue with preprocessing, PCA, and clustering
```
### 🧩 Reconstruction of Likert Scales
The original .sav file contains SPSS value labels, including the ordering of Likert-scale responses.  
When converting to CSV, this information is lost.  
To address this, the code in this repository:
- Detects Likert-scale items using text patterns
- Reconstructs ordinal values using a custom likert_map
- Encodes nominal variables using LabelEncoder
- Combines numerical and encoded categorical variables for analysis
This ensures that the original measurement structure is preserved even without SPSS labels.
### 📦 Required Libraries
```python
pandas  
numpy 1.26.4  
pyreadstat  
scikit-learn 1.3.2  
matplotlib  
seaborn
```
### 📝 License
The code in this repository is released under the MIT License.  
However, **PISA data is copyrighted by the OECD and cannot be redistributed.**
### 🔗 Related Article
Detailed explanation of the analysis is available here:  
https://qiita.com/The_Sun/items/aa000118f4c231ff7b9d

