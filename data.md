## 📁 `data/`
This folder contains the dataset used throughout the analysis.
### Source
  - Public healthcare dataset sourced from Kaggle:  ([Dataset link](https://www.kaggle.com/datasets/prasad22/healthcare-dataset?resource=download))

### Overview
  - Approx. 55,000 patient records
  - Includes demographic, clinical and operational variables
### Key Variables
  - Age - patient age
  - Gender - patient gender
  - Medical Condition - primary condition associated with the patient
  - Admission Type - elective, urgent or emergency admission
  - Length of Stay - number of days between admission and discharge
  - Test Results - outcome indicator (Normal / Abnormal / Inconclusive)

### Notes on Data Preparation

  The dataset was adjusted to better reflect realistic healthcare patterns, including:
  - introducing structured relationships between variables
  - ensuring realistic distributions for metrics, such as length of stay
  - aligning outcome proportions with typical healthcare scenarios

Further details on these transformations are provided in the `feature_engineering/` section.
