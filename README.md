# Employee-Attrition-Prediction-Analytics-Dashboard


A Data Analysis and Visualization project that combines exploratory data analysis, Tableau dashboards, and machine learning to understand and predict employee attrition using the IBM HR Analytics dataset.

**Course:** Data Analysis and Visualization (3CS103ME24)
**Institution:** Nirma University, Ahmedabad
**Authors:** Aditi Shah (23BEC177), Eera Bhargava (23BEI020)
**Submitted To:** Dr. Jai Prakash V. Verma

---

## Objective

Employee attrition is a costly and disruptive problem for organizations. This project analyzes and predicts employee attrition by identifying key contributing factors — such as overtime, work-life balance, salary, promotion history, and job satisfaction — and applies machine learning models to classify whether an employee is likely to leave. The goal is to bridge descriptive and predictive analytics, giving HR teams actionable, data-driven strategies for improving retention.

## Scope

- Data cleaning, encoding, outlier handling, and feature scaling
- Exploratory Data Analysis (EDA) to uncover attrition trends
- Interactive Tableau dashboards for department-wise, demographic, and satisfaction-based attrition insights
- Training and comparing 5 classification models to predict attrition
- Performance evaluation using accuracy, precision, recall, and F1-score
- Interpretation of results to guide HR retention strategy

---

## Dataset

**Source:** [IBM HR Analytics Employee Attrition & Performance (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibmhr-analytics-attrition-dataset?resource=download)

| Detail | Value |
|---|---|
| Rows | 1,470 |
| Columns | 35 |
| Target Variable | `Attrition` (Yes/No) |

Key features include `Age`, `MonthlyIncome`, `JobSatisfaction`, `OverTime`, `WorkLifeBalance`, `YearsAtCompany`, `YearsSinceLastPromotion`, `Department`, `JobRole`, and more — spanning numerical, ordinal, and categorical types.

---

## Tech Stack

- **Language:** Python
- **Libraries:** `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
- **Visualization/BI:** Tableau
- **Environment:** Jupyter Notebook

---

## Workflow

### 1. Data Preprocessing
- Loaded dataset and inspected structure using `df.info()`, `df.describe()`, and null checks (`df.isnull().sum()` — no missing values found)
- Dropped the `Over18` column (constant value, no analytical use)
- **Outlier Detection:** Applied the IQR method across all numeric columns to flag and quantify outliers (notable outlier counts in `TrainingTimesLastYear`, `PerformanceRating`, `MonthlyIncome`, `YearsAtCompany`)
- **Outlier Removal:** Removed flagged outlier rows to produce a cleaned dataset
- **Encoding:**
  - Label-encoded binary columns: `Attrition`, `Gender`, `OverTime`
  - Label-encoded multi-class categorical columns: `BusinessTravel`, `Department`, `EducationField`, `JobRole`, `MaritalStatus`
- **Scaling:** Applied Min-Max scaling to normalize all numeric features to a [0, 1] range

### 2. Visualization (Tableau)
Built an HR Analytics Dashboard covering:
- **KPI Summary:** Employee Count (1,470), Attrition Count (237), Attrition Rate (16.12%), Active Employees (1,233), Average Age (37)
- **Department-wise Attrition** (pie chart) — R&D has the highest attrition, followed by Sales, then HR
- **Marital Status & Gender Treemap** — married males show the highest attrition
- **Department & Job Role by Gender** (heat table) — R&D has the largest workforce; female representation is stronger in research/lab roles, weaker in managerial roles
- **Employees by Education Field** (bar chart) — Life Sciences and Medical dominate, suggesting a healthcare/pharma/biotech workforce
- **Attrition vs. Key Parameters** (histograms) — attrition is highest in the first 0–5 years of role tenure, 1–3 years since last promotion, at a "3" work-life balance rating, and within the first 10 years at the company

### 3. Machine Learning
- Selected features based on correlation with the target variable (`Attrition`)
- Split data into training (80%) and testing (20%) sets
- Trained and evaluated **5 classification models**:
  - Logistic Regression
  - Random Forest
  - Support Vector Machine (SVM)
  - Decision Tree
  - K-Nearest Neighbors (KNN)
- Evaluated each model using **accuracy, precision, recall, and F1-score**
- Visualized results with **confusion matrices** and a **comparative bar chart** of all metrics

---

## Results

| Model | Relative Performance |
|---|---|
| SVM | Best-performing (~53% accuracy/F1) |
| K-Nearest Neighbors | Comparable to SVM (~53% accuracy/F1) |
| Logistic Regression | Moderate (~48% accuracy) |
| Decision Tree | Lower (~38% accuracy) |
| Random Forest | Lowest (~35% accuracy) |

*Note: Performance was constrained by limited feature selection (correlation threshold filtering) — a larger, more carefully engineered feature set would likely improve model accuracy.*

---

## Key Insights

- **Attrition Rate:** 16.12% — moderately high, signaling retention concerns
- **Department:** R&D and Sales together account for the bulk of attrition
- **Tenure:** Employees are most likely to leave within their first 5 years, especially the first 2
- **Promotion:** Lack of promotion for 1–3 years correlates strongly with attrition
- **Work-Life Balance:** Even "average" (rating 3) work-life balance scores correlate with high attrition, suggesting under-addressed burnout
- **Demographics:** Married males show the highest attrition segment among gender/marital-status groups

---

## Repository Structure

```
├── DAV_SA.ipynb              # Jupyter notebook with full analysis & ML pipeline
├── DAV_Assignment.pdf        # Full project report with Tableau visuals & explanations
├── README.md                 # Project overview (this file)
```

---

## Future Improvements

- Use a broader feature selection strategy (e.g., feature importance from tree-based models, or domain-driven selection) instead of a simple correlation threshold
- Apply hyperparameter tuning (GridSearchCV) across all models
- Address class imbalance (attrition "Yes" is a minority class) using SMOTE or class weighting
- Deploy the best-performing model via a simple web app for HR teams to use interactively

---

## 📄 License

This project was created for academic purposes as part of the Data Analysis and Visualization course at Nirma University.
