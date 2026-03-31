## 📁 `modelling/`

This section outlines the predictive modelling approach used to estimate the likelihood of abnormal patient outcomes.

---

### Modelling Approach

A classification framework was used to predict whether a patient’s test result would be normal or abnormal based on:

- age  
- gender  
- medical condition  

The dataset was split into training and test sets using a **70-30 split** to evaluate out-of-sample performance.

---

### Logistic Regression

Logistic regression was used as the primary model, as the outcome variable is binary (Normal vs Abnormal) and given its suitability for healthcare applications.

The model estimates the probability of an abnormal outcome given patient characteristics.

Performance was evaluated on the test set using:

- confusion matrix  
- sensitivity and specificity  
- ROC curve and Area Under the Curve (AUC)  

The model achieved an AUC of approximately **0.65**, indicating moderate predictive performance.

While the model performs better than random classification, its ability to clearly distinguish between normal and abnormal outcomes is limited.  

This suggests that the available features provide only partial information about patient risk, and additional variables would be required to improve classification performance.

✅ Logistic regression provides a useful and interpretable baseline, but highlights the limitations of the current feature set.

### Threshold Optimisation

Instead of using a default classification cutoff (0.5), model performance was evaluated across a range of probability thresholds.

Sensitivity, specificity and accuracy were calculated for each threshold to understand the trade-offs involved.

<img width="695" height="402" alt="image" src="https://github.com/user-attachments/assets/874dcf93-72c0-4439-b677-65b8ec907f2f" />

As the threshold increases:

- Sensitivity decreases (fewer abnormal cases detected)  
- Specificity increases (fewer false positives)  
- Accuracy increases overall  

An optimal threshold of approximately **0.14** was selected, where sensitivity and specificity are balanced.

At this threshold, accuracy, sensitivity, and specificity are all approximately **0.62**, indicating a balanced classification performance. 

✅ Although higher thresholds yield better accuracy, they significantly reduce the detection of abnormal cases.  
This highlights the importance of choosing thresholds based on decision context rather than maximising accuracy alone.

In practice, this depends on the question being asked. If the goal is to err on the side of caution, a lower threshold can be used to increase 
detection of abnormal cases, even at the cost of more false positives.  
Conversely, a higher threshold may be preferred when avoiding false alarms is more important.

✅ The choice of threshold should therefore be driven by the relative cost of missed detections versus false positives.

### Model Comparison

To assess whether more complex models could improve predictive performance, additional models were evaluated alongside logistic regression.

- Random Forest  
- Gradient Boosting (XGBoost)  

These models were selected to capture potential non-linear relationships and interactions between variables.

| Model                | AUC   |
|---------------------|-------|
| Logistic Regression | 0.647 |
| Random Forest       | 0.50  |
| XGBoost             | 0.639 |

Logistic regression performed best despite being the simplest model, while Random Forest performed no better than random classification and XGBoost showed only marginal performance.

<img width="695" height="602" alt="image" src="https://github.com/user-attachments/assets/b18834e2-fd8f-4f2b-ae35-d3a59ce7638e" />

This suggests that the relationships in the data are relatively simple and do not benefit from more flexible modelling approaches.

✅ The results indicate that predictive performance is limited by the available features rather than model complexity. 

---

### Key Takeaways

- Logistic regression provides the best balance of performance and interpretability  
- Threshold selection has a significant impact on model usefulness  
- More complex models do not necessarily improve results  
- Predictive performance is limited by the available features  

✅ Overall, simple and interpretable models are sufficient given the structure of the data.
