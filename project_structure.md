## Repository Structure

The project is organised to reflect the different stages of the analysis, from data preparation to modelling and business reporting.

```text
.
├── README
├── analytics/ 
├── analytics_SQL/ 
├── data/ 
├── feature_engineering/
├── modelling/
├── project_structure/
└── statistics/
```
### 📁 `analytics/`

Focused on business-facing analysis and reporting using SQL queries for aggregation and data exploration.

Turns analysis into useful information for making decisions.

### 📁 `analytics_SQL/`

Contains all SQL used to obtain the results shown in 'analytics/'

### 📁 `data/`

Contains raw and processed datasets used in the analysis.
Separates original data from transformed data to ensure transparency in modelling.

### 📁 `feature_engineering/`

Includes scripts used to transform and enhance the dataset, such as:

- generating realistic length of stay
- introducing structured relationships between variables
- preparing features for modelling

Ensures the data reflects meaningful patterns rather than artificial structure.

### 📁 `modelling/`

Covers predictive modelling and evaluation:

- logistic regression (baseline model)
- model comparison (Random Forest, XGBoost)
- ROC analysis and AUC
- threshold optimisation

Focuses on understanding model performance and decision trade-offs.

### 📁 `statistics/`

Contains statistical testing and inference:

- Chi-square tests of association
- Non-parametric tests
- analysis of statistical vs practical significance

Complements modelling by providing deeper insight into relationships within the data.

