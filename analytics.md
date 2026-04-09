## 📁 `analytics/`

This section focuses on using SQL to analyse the dataset from an operational perspective.

---

The emphasis here is on understanding how different patient segments contribute to outcomes such as abnormal test results and hospital demand.

The analysis answers questions including:

- which medical conditions contribute most to abnormal cases  
- how risk varies across age groups  
- which admission types are associated with higher abnormal rates  
- which segments drive overall hospital utilisation  

These queries show how data can be explored and broken down to answer practical questions.

---

### Admission Type Analysis: Abnormal Outcome Rates

This analysis examines how abnormal test outcomes vary across different admission types, namely elective, urgent and emergency.

Understanding this relationship helps identify whether certain admission pathways are associated with higher clinical risk and may require greater resource allocation.

| Admission Type | Abnormal Cases | Total Cases | Abnormal Rate |
|---------------|----------------|-------------|---------------|
| Emergency     | 861            | 5465        | 0.1575        |
| Urgent        | 702            | 5585        | 0.1257        |
| Elective      | 5573           | 44450       | 0.1254        |

Emergency admissions exhibit a higher abnormal rate compared to urgent and elective cases. A chi-square test indicates a statistically significant association between admission type and abnormal outcomes.

However, the difference in abnormal rates is relatively small in magnitude. As discussed in the `statistics/` section, statistical significance does not imply practical significance.

✅ While admission type shows some association with abnormal outcomes, its practical impact is limited and may not be sufficient as a standalone risk indicator.

---

### Age Group Analysis: Abnormal Outcome Rates

This analysis examines how abnormal test outcomes vary across different age groups and how each group compares to the overall average.

Understanding this distribution helps identify high-risk segments and quantify how far each group deviates from the average risk level.

| Age Group (in years) | Abnormal Cases | Total Cases | Abnormal Rate | Deviation from Average | Risk Rank |
|----------|----------------|-------------|---------------|----------------------|----------|
| Over 60  | 3998           | 20370       | 0.19627       | +0.09427             | 1        |
| 51 - 60    | 1028           | 8297        | 0.12390       | +0.02189             | 2        |
| 41 - 50    | 1010           | 8209        | 0.12304       | +0.02103             | 3        |
| 31 - 40    | 499            | 8125        | 0.06142       | −0.04058             | 4        |
| 21 - 30    | 486            | 8056        | 0.06033       | −0.04167             | 5        |
| Under 20 | 115            | 2443        | 0.04707       | −0.05493             | 6        |

The results show a clear and consistent increase in abnormal outcomes with age.

Patients aged over 60 exhibit the highest abnormal rate and deviate significantly above the average, making them the highest-risk group.  
Patients between 40 and 60 years of age form a moderate-risk segment, with similar abnormal rates slightly above average.  
In contrast, younger age groups (below 40) fall below the average and represent lower-risk segments.

✅ Age is a strong driver of abnormal outcomes and provides a clear basis for identifying risk and prioritisation of resources.

---

### Medical Condition Analysis: Contribution to Abnormal Cases

This analysis looks at which medical conditions contribute most to abnormal outcomes. It also compares abnormal rates across conditions and then checks where most cases come from.

#### Above Average Abnormal Rates

| Medical Condition | Total Cases | Abnormal Cases | Abnormal Rate |
|------------------|------------|----------------|---------------|
| Arthritis        | 10469      | 1764           | 0.1685        |
| Cancer           | 2788       | 364            | 0.1306        |
| Diabetes         | 7320       | 1073           | 0.1466        |
| Hypertension     | 15710      | 2107           | 0.1341        |

These conditions have abnormal rates above the overall average.  
Arthritis shows the highest rate, followed by Diabetes and Hypertension.


#### Contribution to Total Abnormal Cases

| Medical Condition | Abnormal Cases | Total Cases | Contribution | Cumulative Contribution |
|------------------|----------------|-------------|--------------|------------------------|
| Hypertension     | 2107           | 15710       | 0.29526      | 0.29526                |
| Arthritis        | 1764           | 10469       | 0.24720      | 0.54246                |
| Diabetes         | 1073           | 7320        | 0.15036      | 0.69282                |
| Obesity          | 926            | 9968        | 0.12976      | 0.82258                |
| Asthma           | 902            | 9245        | 0.12640      | 0.94898                |
| Cancer           | 364            | 2788        | 0.05101      | 0.99999                |

A small number of conditions account for most abnormal cases.  
The top four conditions contribute to about 80 percent of all abnormal outcomes.

---

Hypertension contributes the most in absolute terms because of large number patients, even though its rate is not the highest.  
Arthritis has a higher abnormal rate, but fewer total cases.

This shows the difference between:
- high risk conditions  
- high volume conditions  

Both matter in practice.

✅ A small group of conditions is responsible for most abnormal outcomes, which can help prioritise focus areas for monitoring and care.
