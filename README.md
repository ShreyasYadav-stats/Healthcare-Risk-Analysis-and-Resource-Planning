# Healthcare Risk Analysis for Patient Outcomes and Resource Planning
Project focusing on predictive and statistical modelling to support resource allocation and understand drivers of abnormal test outcomes.

## Project Structure

The repository is organised to reflect different stages of the analysis, including feature engineering, modelling, statistical testing and data analytics.

For a detailed breakdown of the folder structure, see:
 `project_structure.md`

## Overview

Hospitals operate under constant pressure to balance patient demand with limited resources. This project analyses patient-level healthcare data to understand:
- which patients are more likely to have abnormal outcomes
- how early these cases can be identified
- how these insights can support capacity planning and operational decisions

The focus is on translating statistical and modelling outputs into decision-relevant and practical insights for healthcare planning.

## Business Context

In a hospital and clinical settings, decisions need to be made under uncertainty:

- How early can we identify high-risk patients using available data and how many high-risk patients should we expect?
- Do we have sufficient capacity (beds, resources) for patients likely to have abnormal outcomes?
- Which patient groups are at higher risk and may require closer monitoring?
- What trade-offs exist between catching high-risk patients and avoiding false alarms?

## Key Questions

This analysis is designed to answer:

- Which factors are associated with abnormal test outcomes?
- How accurately can we identify high-risk patients?
- What classification threshold is appropriate in a healthcare setting?
- Are observed differences meaningful in practice, or only statistically significant?

## Approach
The project combines three components:

- Predictive Modelling
  - Logistic regression used as the primary model due to its interpretability
  - More complex models (Random Forest, XGBoost) were evaluated to test whether non-linear relationships improve performance
  - Model evaluated using ROC, AUC and confusion matrices

- Threshold Optimisation
  - Classification threshold tuned for real-world healthcare priorities
  - Focus on balancing sensitivity (detecting abnormal cases) and specificity

- Statistical Analysis
  - Chi-square tests to identify associations between patient attributes
  - ANOVA and non-parametric tests to analyse length of stay

## Key Results

### Model Performance

| Model               | AUC   |
| ------------------- | ----- |
| Logistic Regression | 0.6474 |
| Random Forest       | 0.50  |
| XGBoost             | 0.639 |

✅ Logistic regression performed best despite being the simplest model, suggesting that the underlying relationships in the data are relatively simple.

### Threshold Selection
Optimal threshold ≈ 0.140914

| Metric      | Value |
| ----------- | ----- |
| Accuracy    | ~0.6169763  |
| Sensitivity | ~0.6154576  |
| Specificity | ~0.6172054  |

✅ Lower thresholds significantly improve detection of abnormal patients compared to default settings. This highlights the importance of choosing thresholds based on decision context rather than relying on default settings.

### Statistical Testing of Associations
- Medical condition is associated with test outcomes
- Admission type is associated with both condition and outcomes
- No significant association found between gender and medical condition

✅ Not all variables contribute equally to patient risk. Risk is driven more by clinical and operational factors than by demographic variables.

### Patient Length of Stay
Statistically significant differences observed across conditions
However, distributions largely overlap, that is, patients with different medical conditions tend to stay in hospital for similar durations, even if small differences exist on average.

✅ Indicates limited practical impact despite statistical significance.

## Key Insights
1. Model complexity does not improve performance: More complex models (Random Forest, XGBoost) did not outperform logistic regression.

✅ Performance is constrained by available features, not model choice

2. Threshold selection is more important than the model: Default classification thresholds perform poorly in healthcare settings.

✅ Lower thresholds improve detection of abnormal cases, which is often more critical

3. Patient characteristics provide limited predictive signal: Age and medical condition contribute to prediction, but are insufficient for strong classification

4. Statistical significance does not imply practical impact: Large sample size leads to statistically significant results even when differences are small

✅ Decisions should focus on effect size and operational relevance

## Recommendations
- Use lower classification thresholds to prioritise detection of abnormal patients
- Avoid relying solely on demographic variables for decision-making
- Invest in richer clinical data (e.g. lab results, patient history)
- Prefer simple, interpretable models unless complexity adds clear value

## Feature Engineering

To improve realism and enable meaningful analysis, key features were engineered:

- Length of Stay (LOS)
  - Derived from admission and discharge dates and modelled as a right-skewed count variable to reflect real hospital stay patterns
- Medical Condition
  - Assigned using age-dependent probabilities to reflect realistic population trends
- Test Results
  - Structured to reflect class imbalance, with abnormal outcomes more likely in older patients
- Admission Type
  - Modelled to reflect typical hospital distributions, with emergency admissions more likely among older individuals

✅ These transformations ensure the data mirrors real-world structures, making the analysis much more meaningful.

## Deliverables
- Predictive modelling (classification and evaluation)
- Threshold optimisation analysis
- Statistical testing (Chi-square, ANOVA, Kruskal–Wallis)
- Visualisations (ROC curves, sensitivity-specificity trade-offs)
- Planned SQL and Power BI dashboard for operational insights
## Next Steps
- Build interactive Power BI dashboard for hospital decision-making
- Integrate SQL-based data pipelines
- Extend modelling with additional clinical variables

## Limitations

- The dataset is partially simulated and relationships between variables were introduced through modelling assumptions  
- Predictive performance is limited by the availability of features, particularly the absence of detailed clinical data  
- Results should be interpreted as illustrative of modelling approaches rather than definitive clinical conclusions  

✅ These limitations highlight the importance of data quality and feature richness in real-world healthcare modelling.
