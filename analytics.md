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

### Age Group Analysis: Abnormal Outcome Rates

This analysis examines how abnormal test outcomes vary across different age groups and how each group compares to the overall average.

Understanding this distribution helps identify high-risk segments and quantify how far each group deviates from the average risk level.

| Age Group | Abnormal Cases | Total Cases | Abnormal Rate | Deviation from Average | Risk Rank |
|----------|----------------|-------------|---------------|----------------------|----------|
| Over 60  | 3998           | 20370       | 0.19627       | +0.09427             | 1        |
| 51–60    | 1028           | 8297        | 0.12390       | +0.02189             | 2        |
| 41–50    | 1010           | 8209        | 0.12304       | +0.02103             | 3        |
| 31–40    | 499            | 8125        | 0.06142       | −0.04058             | 4        |
| 21–30    | 486            | 8056        | 0.06033       | −0.04167             | 5        |
| Under 20 | 115            | 2443        | 0.04707       | −0.05493             | 6        |

The results show a clear and consistent increase in abnormal outcomes with age.

Patients aged over 60 exhibit the highest abnormal rate and deviate significantly above the average, making them the highest-risk group.  
Patients between 40 and 60 years of age form a moderate-risk segment, with similar abnormal rates slightly above average.  
In contrast, younger age groups (below 40) fall below the average and represent lower-risk segments.

✅ Age is a strong driver of abnormal outcomes and provides a clear basis for risk stratification and prioritisation of healthcare resources.

