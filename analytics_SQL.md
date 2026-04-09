## 📁 `SQL Queries`

This file contains the SQL queries used to generate the results in `analytics.md`.

---

### Admission Type Analysis

```
WITH props AS (
    SELECT
        t."Admission.Type",
        t.freq,
        a.abnorm_freq,
        ROUND(a.abnorm_freq * 1.0 / t.freq, 4) AS Proportion
    FROM (
        SELECT "Admission.Type", COUNT(*) AS freq
        FROM cleaned_health_data
        GROUP BY "Admission.Type"
    ) t
    JOIN (
        SELECT "Admission.Type", COUNT(*) AS abnorm_freq
        FROM cleaned_health_data
        WHERE "Test.Results" = 'Abnormal'
        GROUP BY "Admission.Type"
    ) a
    ON t."Admission.Type" = a."Admission.Type"
)

SELECT * FROM props ORDER BY Proportion DESC
```

### Age Group Analysis

```
WITH age_summary AS (
    SELECT
        CASE
            WHEN "Age" <= 20 THEN 'Under 20'
            WHEN "Age" <= 30 THEN '21 - 30'
            WHEN "Age" <= 40 THEN '31 - 40'
            WHEN "Age" <= 50 THEN '41 - 50'
            WHEN "Age" <= 60 THEN '51 - 60'
            ELSE 'Over 60'
        END AS agegroups,
        COUNT(*) AS total_count,
        SUM(CASE WHEN "Test.Results" = 'Abnormal' THEN 1 ELSE 0 END) AS abnormal_count,
        ROUND(
            SUM(CASE WHEN "Test.Results" = 'Abnormal' THEN 1 ELSE 0 END) * 1.0 / COUNT(*),
            5
        ) AS abnorm_rate
    FROM cleaned_health_data
    GROUP BY agegroups
)

SELECT
    agegroups, abnormal_count, total_count, abnorm_rate,
    ROUND(abnorm_rate - AVG(abnorm_rate) OVER (), 5) AS deviation_from_avg,
    RANK() OVER (ORDER BY abnorm_rate DESC) AS risk_rank
FROM age_summary
ORDER BY abnorm_rate DESC;
```

### Medical Condition Analysis

```
WITH condition_contrib AS (
	SELECT t."Medical.Condition", t.abnorm_cases, a.Total_number_of_cases, ROUND((t.abnorm_cases * 1.0)/(SELECT COUNT(*)
		FROM cleaned_health_data
		WHERE "Test.Results" = 'Abnormal'),5) AS contribution
	FROM
	(
		SELECT "Medical.Condition", COUNT(*) AS abnorm_cases 
		FROM cleaned_health_data
		WHERE "Test.Results" = 'Abnormal' 
		GROUP BY "Medical.Condition"
		ORDER BY abnorm_cases DESC) t
	JOIN (
		SELECT "Medical.Condition", COUNT(*) AS Total_number_of_cases 
		FROM cleaned_health_data 
		GROUP BY "Medical.Condition"
		ORDER BY Total_number_of_cases DESC
	)a
ON t."Medical.Condition" = a."Medical.Condition"
)

SELECT "Medical.Condition", abnorm_cases, Total_number_of_cases, contribution, 
	SUM(contribution) OVER (ORDER BY contribution DESC) AS cumulative_contribution
FROM condition_contrib
```
