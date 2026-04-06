## 📁 `feature_engineering/`

This folder documents the transformations applied to the dataset to better represent realistic healthcare scenarios.

---

The original dataset ([link for reference](https://www.kaggle.com/datasets/prasad22/healthcare-dataset/versions/2?resource=download)) contained 
several variables that were uniformly distributed. 
As a result, variables such as medical condition, length of stay and blood group did not reflect real-world patterns or dependencies.

To improve realism, key variables were resimulated using probability distributions and structured relationships that 
better represent healthcare, demographic and biological behaviour.


### Data Cleaning

The dataset contained minimal missing or inconsistent values, so only light preprocessing was required.

Variables not relevant to the analysis, such as patient names, hospital names and doctor identifiers were removed.


### Blood Groups

In the original dataset, blood groups were uniformly distributed, which does not reflect real-world population patterns. To address this, blood group 
proportions were resampled based on publicly available data from the
[Australian Red Cross Lifeblood](https://www.lifeblood.com.au/donors/blood-plasma-platelets/learn/blood/blood-types).
This adjustment ensures that blood group distribution aligns more closely with observed population-level frequencies.

### Medical Conditions

  Medical conditions were assigned using age-dependent probabilities. Older patients were more likely to be associated with conditions
  such as arthritis and hypertension, while younger patients had a higher likelihood of conditions such as asthma. This reflects known 
  demographic patterns in disease prevalence.
  
### Test Results

  Test outcomes were structured to introduce class imbalance and clinical realism. The majority of cases were classified as normal,
  with abnormal results more likely among older patients. This aligns with the expectation that risk of adverse outcomes increases with age.

### Admission Type

  Admission types were adjusted to reflect typical hospital operations, with most cases being elective,
  followed by urgent and a smaller proportion of emergency admissions. Older patients were more likely to require 
  emergency care, reflecting increased clinical risk.

These transformations introduce meaningful dependencies between variables, allowing the dataset to better capture patient risk 
profiles and support more realistic modelling and analysis.

✅ Overall, these changes ensure that the dataset captures realistic structure and dependencies, making subsequent modelling and 
statistical analysis more meaningful and interpretable.
