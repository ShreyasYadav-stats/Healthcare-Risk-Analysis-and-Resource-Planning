## 📁 `analytics/`

This section focuses on using SQL to analyse the dataset from an operational perspective.

---

The emphasis here is on understanding how different patient segments contribute to outcomes such as abnormal test results and hospital demand.

The analysis is driven by questions including:

- which medical conditions contribute most to abnormal cases  
- how risk varies across age groups  
- which admission types are associated with higher abnormal rates  
- which segments drive overall hospital utilisation  

These queries show how data can be explored and broken down to answer practical questions.

### Admission Type Analysis: Abnormal Outcome Rates

This analysis examines how abnormal test outcomes vary across different admission types, namely elective, urgent and emergency.

Understanding this relationship helps identify whether certain admission pathways are associated with higher clinical risk and may require greater resource allocation.

| Admission Type | Total Cases | Abnormal Cases | Abnormal Rate |
|---------------|------------|----------------|---------------|
| Emergency     | 5465       | 861            | 0.1575        |
| Urgent        | 5585       | 702            | 0.1257        |
| Elective      | 44450      | 5573           | 0.1254        |

Emergency admissions exhibit a higher abnormal rate compared to urgent and elective cases. A chi-square test indicates a statistically significant association between admission type and abnormal outcomes.

However, the difference in abnormal rates is relatively small in magnitude. As discussed in the `statistics/` section, statistical significance does not imply practical significance.

✅ While admission type shows some association with abnormal outcomes, its practical impact is limited and may not be sufficient as a standalone risk indicator.
