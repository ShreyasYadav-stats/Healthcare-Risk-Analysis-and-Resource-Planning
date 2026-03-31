## 📁 `statistics/`

This section focuses on statistical analysis used to understand relationships within the dataset beyond predictive modelling.

---

### Length of Stay Analysis

Differences in length of stay across medical conditions were analysed using the Kruskal-Wallis test, a non-parametric alternative to ANOVA.

This approach was chosen as length of stay is not normally distributed and exhibits a right-skewed pattern.

The results indicate statistically significant differences between groups.

Average length of stay by condition is shown below:

| Medical Condition | Average Length of Stay |
|------------------|----------------------|
| Arthritis        | 5.42                 |
| Asthma           | 4.99                 |
| Cancer           | 5.15                 |
| Diabetes         | 5.29                 |
| Hypertension     | 5.22                 |
| Obesity          | 4.96                 |

<img width="895" height="602" alt="image" src="https://github.com/user-attachments/assets/69466b51-c98a-4084-a93c-3b2cc0d1264c" />

Although differences exist in average values, the distributions largely overlap across conditions.

In this setting, it is also important to consider the effect of sample size. With a large number of observations, statistical tests have high 
power and can detect even very small differences as significant.

✅ While differences are statistically significant, they are small in magnitude and not practically meaningful for decision-making.

---

### Chi-square Tests of Association

Chi-square tests were used to examine relationships between categorical variables.

Key findings include:

- A significant association between **medical condition and test results**  
- A significant association between **admission type and test results**  
- A significant association between **admission type and medical condition**  
- No significant association between **gender and medical condition**

These results indicate that clinical and operational factors play a larger role in patient outcomes than demographic variables such as gender.

---

### Statistical vs Practical Significance

Several tests returned highly significant p-values, which is expected given the large sample size.

However, statistical significance does not necessarily imply meaningful real-world differences.

In this case:

- Differences in length of stay are statistically detectable  
- But distributions largely overlap across groups  

✅ This highlights the importance of interpreting results in context, rather than relying solely on p-values.

---

### Key Takeaways
 
- Not all statistically significant results are practically important  
- Clinical and operational variables are more informative than demographic variables  
- Interpretation should focus on effect size and real-world relevance  

✅ Statistical analysis complements modelling by providing deeper insight into the structure and limitations of the data.
