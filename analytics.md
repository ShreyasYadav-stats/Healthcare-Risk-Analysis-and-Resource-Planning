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

### Which admission types have above-average abnormal rates?

This analysis examines how abnormal test outcomes vary across different admission types, namely elective, urgent, and emergency.

Understanding this relationship helps identify whether certain admission pathways are associated with higher clinical risk and may require greater resource allocation.

| Admission Type | Total Cases | Abnormal Cases | Abnormal Rate |
|---------------|------------|----------------|---------------|
| Emergency     | 5465       | 861            | 0.1575        |
| Urgent        | 5585       | 702            | 0.1257        |
| Elective      | 44450      | 5573           | 0.1254        |

Emergency admissions exhibit the highest abnormal rate, noticeably above both urgent and elective cases.

While urgent and elective admissions have similar abnormal rates, emergency cases show a clear increase in the likelihood of abnormal outcomes.

✅ Emergency admissions are associated with higher clinical risk and may require increased attention and resource allocation.

