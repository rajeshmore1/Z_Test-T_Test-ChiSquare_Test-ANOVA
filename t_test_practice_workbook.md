# t-Test Practice Workbook with Detailed Solutions

## How to Use This Workbook

Each problem includes:
1. The scenario and data
2. Step-by-step solution with all calculations shown
3. Interpretation in plain language
4. Common mistakes to avoid

Work through each problem yourself BEFORE looking at the solution!

---

## Problem Set 1: One-Sample t-Tests

### Problem 1.1: Quality Control (Two-Tailed)

**Scenario:**
A factory produces bolts that should be 5.0 cm long. The quality control manager suspects the machine may be off-calibration. She measures 12 randomly selected bolts:

**Data:** 5.1, 4.9, 5.2, 5.0, 4.8, 5.1, 5.0, 4.9, 5.2, 5.1, 5.0, 4.9

**Question:** Test if the machine is properly calibrated at α = 0.05 (two-tailed).

---

**SOLUTION:**

**Step 1: State Hypotheses**
- H₀: μ = 5.0 cm (machine is properly calibrated)
- H₁: μ ≠ 5.0 cm (machine is off-calibration)
- α = 0.05
- Test type: Two-tailed (we care about deviation in either direction)

**Step 2: Organize Data**
```
n = 12 bolts
Data: 5.1, 4.9, 5.2, 5.0, 4.8, 5.1, 5.0, 4.9, 5.2, 5.1, 5.0, 4.9
```

**Step 3: Calculate Sample Mean (x̄)**
```
Sum = 5.1 + 4.9 + 5.2 + 5.0 + 4.8 + 5.1 + 5.0 + 4.9 + 5.2 + 5.1 + 5.0 + 4.9
Sum = 60.2

x̄ = 60.2 / 12 = 5.017 cm
```

**Step 4: Calculate Sample Standard Deviation (s)**
```
Deviations from mean (x - x̄):
5.1 - 5.017 = 0.083
4.9 - 5.017 = -0.117
5.2 - 5.017 = 0.183
5.0 - 5.017 = -0.017
4.8 - 5.017 = -0.217
5.1 - 5.017 = 0.083
5.0 - 5.017 = -0.017
4.9 - 5.017 = -0.117
5.2 - 5.017 = 0.183
5.1 - 5.017 = 0.083
5.0 - 5.017 = -0.017
4.9 - 5.017 = -0.117

Squared deviations:
0.007, 0.014, 0.033, 0.000, 0.047, 0.007, 0.000, 0.014, 0.033, 0.007, 0.000, 0.014

Sum of squared deviations = 0.176

Variance: s² = 0.176 / (12-1) = 0.176 / 11 = 0.016

Standard deviation: s = √0.016 = 0.126 cm
```

**Step 5: Calculate t-Statistic**
```
Formula: t = (x̄ - μ₀) / (s / √n)

t = (5.017 - 5.0) / (0.126 / √12)
t = 0.017 / (0.126 / 3.464)
t = 0.017 / 0.036
t = 0.47
```

**Step 6: Determine Critical Value**
```
df = n - 1 = 12 - 1 = 11
α = 0.05 (two-tailed)

From t-table: t_critical = ±2.201
```

**Step 7: Make Decision**
```
Decision rule: Reject H₀ if |t| > t_critical

|t| = |0.47| = 0.47
t_critical = 2.201

Since 0.47 < 2.201, we FAIL TO REJECT H₀
```

**Step 8: Calculate p-value (approximate)**
```
With t = 0.47 and df = 11, p-value > 0.10 (not significant)
```

**Step 9: Interpretation**

"There is insufficient evidence to conclude that the machine is off-calibration (t(11) = 0.47, p > 0.05). The mean bolt length of 5.017 cm is not significantly different from the target of 5.0 cm. The machine appears to be working properly."

**Common Mistakes to Avoid:**
❌ Forgetting to use (n-1) in denominator when calculating s²
❌ Using wrong critical value (one-tailed instead of two-tailed)
❌ Confusing "fail to reject H₀" with "accepting H₀"

---

### Problem 1.2: Coffee Temperature (Right-Tailed)

**Scenario:**
A coffee shop advertises that their coffee is served at "at least 160°F." A customer suspects it's actually cooler. She measures the temperature of 8 coffees:

**Data:** 157, 159, 158, 160, 156, 159, 157, 158

**Question:** Test the customer's suspicion at α = 0.05.

---

**SOLUTION:**

**Step 1: State Hypotheses**
- H₀: μ ≥ 160°F (shop's claim is correct)
- H₁: μ < 160°F (coffee is cooler than claimed)
- α = 0.05
- Test type: Left-tailed (testing if temperature is LESS than claimed)

**Step 2: Calculate Sample Mean**
```
Sum = 157 + 159 + 158 + 160 + 156 + 159 + 157 + 158 = 1264

x̄ = 1264 / 8 = 158.0°F
```

**Step 3: Calculate Standard Deviation**
```
Deviations: -1, 1, 0, 2, -2, 1, -1, 0

Squared: 1, 1, 0, 4, 4, 1, 1, 0
Sum = 12

s² = 12 / 7 = 1.714
s = √1.714 = 1.31°F
```

**Step 4: Calculate t-Statistic**
```
t = (158.0 - 160) / (1.31 / √8)
t = -2.0 / (1.31 / 2.828)
t = -2.0 / 0.463
t = -4.32
```

**Step 5: Critical Value**
```
df = 7
α = 0.05 (one-tailed, left)
t_critical = -1.895
```

**Step 6: Decision**
```
Since t = -4.32 < -1.895, we REJECT H₀
```

**Step 7: Interpretation**

"The coffee is significantly cooler than advertised (t(7) = -4.32, p < 0.01). The average temperature of 158.0°F is statistically significantly less than the claimed 160°F. The customer's suspicion is correct."

---

## Problem Set 2: Independent Two-Sample t-Tests

### Problem 2.1: Study Methods Comparison

**Scenario:**
Does studying with music affect test scores? Two groups of students are compared:

**Group A (No Music):** 78, 82, 85, 80, 83, 79, 81
**Group B (With Music):** 75, 72, 77, 74, 76, 73, 75

**Question:** Is there a significant difference? (α = 0.05, two-tailed)

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: μ₁ = μ₂ (no difference between groups)
- H₁: μ₁ ≠ μ₂ (there is a difference)
- α = 0.05

**Step 2: Calculate Sample Statistics**

Group A (No Music):
```
n₁ = 7
Sum = 78 + 82 + 85 + 80 + 83 + 79 + 81 = 568
x̄₁ = 568 / 7 = 81.14

Deviations from 81.14: -3.14, 0.86, 3.86, -1.14, 1.86, -2.14, -0.14
Squared: 9.86, 0.74, 14.90, 1.30, 3.46, 4.58, 0.02
Sum = 34.86

s₁² = 34.86 / 6 = 5.81
s₁ = 2.41
```

Group B (With Music):
```
n₂ = 7
Sum = 75 + 72 + 77 + 74 + 76 + 73 + 75 = 522
x̄₂ = 522 / 7 = 74.57

Deviations from 74.57: 0.43, -2.57, 2.43, -0.57, 1.43, -1.57, 0.43
Squared: 0.18, 6.60, 5.90, 0.32, 2.04, 2.46, 0.18
Sum = 17.68

s₂² = 17.68 / 6 = 2.95
s₂ = 1.72
```

**Step 3: Calculate Pooled Variance**
```
s²ₚ = [(n₁-1)s₁² + (n₂-1)s₂²] / (n₁ + n₂ - 2)
s²ₚ = [(6)(5.81) + (6)(2.95)] / (7 + 7 - 2)
s²ₚ = [34.86 + 17.70] / 12
s²ₚ = 52.56 / 12
s²ₚ = 4.38
```

**Step 4: Calculate t-Statistic**
```
t = (x̄₁ - x̄₂) / √[s²ₚ(1/n₁ + 1/n₂)]
t = (81.14 - 74.57) / √[4.38(1/7 + 1/7)]
t = 6.57 / √[4.38(0.286)]
t = 6.57 / √1.253
t = 6.57 / 1.12
t = 5.87
```

**Step 5: Critical Value**
```
df = n₁ + n₂ - 2 = 7 + 7 - 2 = 12
α = 0.05 (two-tailed)
t_critical = ±2.179
```

**Step 6: Decision**
```
Since |5.87| > 2.179, we REJECT H₀
```

**Step 7: Calculate Effect Size**
```
Cohen's d = (x̄₁ - x̄₂) / √s²ₚ
d = 6.57 / √4.38
d = 6.57 / 2.09
d = 3.14  (Very large effect!)
```

**Step 8: Interpretation**

"Students who studied without music scored significantly higher (M = 81.14, SD = 2.41) than students who studied with music (M = 74.57, SD = 1.72), t(12) = 5.87, p < 0.001, d = 3.14. This represents a very large effect size, suggesting music substantially interferes with studying for this type of test."

---

### Problem 2.2: Drug Trial

**Scenario:**
Testing a new pain medication. Pain scores (0-10 scale) after treatment:

**Placebo Group:** 6, 7, 6, 8, 7, 6, 7, 8
**Drug Group:** 4, 3, 5, 4, 3, 4, 5, 3

**Question:** Does the drug reduce pain? (α = 0.01, one-tailed)

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: μ_drug ≥ μ_placebo (drug is no better)
- H₁: μ_drug < μ_placebo (drug reduces pain)
- α = 0.01
- Test: Left-tailed (expecting lower pain scores with drug)

**Step 2: Sample Statistics**

Placebo:
```
n₁ = 8
x̄₁ = (6+7+6+8+7+6+7+8)/8 = 55/8 = 6.875

Deviations: -0.875, 0.125, -0.875, 1.125, 0.125, -0.875, 0.125, 1.125
Squared: 0.766, 0.016, 0.766, 1.266, 0.016, 0.766, 0.016, 1.266
Sum = 4.878

s₁² = 4.878/7 = 0.697
s₁ = 0.835
```

Drug:
```
n₂ = 8
x̄₂ = (4+3+5+4+3+4+5+3)/8 = 31/8 = 3.875

Deviations: 0.125, -0.875, 1.125, 0.125, -0.875, 0.125, 1.125, -0.875
Squared: 0.016, 0.766, 1.266, 0.016, 0.766, 0.016, 1.266, 0.766
Sum = 4.878

s₂² = 4.878/7 = 0.697
s₂ = 0.835
```

**Step 3: Pooled Variance**
```
s²ₚ = [(7)(0.697) + (7)(0.697)] / 14
s²ₚ = 9.758 / 14
s²ₚ = 0.697
```

**Step 4: t-Statistic**
```
t = (3.875 - 6.875) / √[0.697(1/8 + 1/8)]
t = -3.0 / √[0.697(0.25)]
t = -3.0 / √0.174
t = -3.0 / 0.417
t = -7.19
```

**Step 5: Critical Value**
```
df = 14
α = 0.01 (one-tailed)
t_critical = -2.624
```

**Step 6: Decision**
```
Since -7.19 < -2.624, we REJECT H₀
```

**Step 7: Effect Size**
```
d = -3.0 / √0.697 = -3.0 / 0.835 = -3.59
(Negative indicates direction; magnitude = 3.59 is very large)
```

**Step 8: Interpretation**

"The drug significantly reduces pain compared to placebo (t(14) = -7.19, p < 0.001, d = 3.59). Patients receiving the drug reported much lower pain scores (M = 3.88) compared to placebo (M = 6.88), a difference of 3 points on the 0-10 scale. This represents a clinically meaningful and statistically significant improvement."

---

## Problem Set 3: Paired Sample t-Tests

### Problem 3.1: Tutoring Effectiveness

**Scenario:**
Does tutoring improve test scores? 10 students tested before and after tutoring:

| Student | Before | After |
|---------|--------|-------|
| 1       | 65     | 72    |
| 2       | 70     | 75    |
| 3       | 68     | 71    |
| 4       | 72     | 78    |
| 5       | 66     | 70    |
| 6       | 69     | 74    |
| 7       | 71     | 76    |
| 8       | 67     | 69    |
| 9       | 73     | 79    |
| 10      | 64     | 68    |

**Question:** Does tutoring significantly improve scores? (α = 0.05, one-tailed)

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: μ_d ≤ 0 (no improvement)
- H₁: μ_d > 0 (scores improve after tutoring)
- α = 0.05
- Test: Right-tailed (expecting positive differences)

**Step 2: Calculate Differences (After - Before)**

| Student | Before | After | Difference (d) |
|---------|--------|-------|----------------|
| 1       | 65     | 72    | 7              |
| 2       | 70     | 75    | 5              |
| 3       | 68     | 71    | 3              |
| 4       | 72     | 78    | 6              |
| 5       | 66     | 70    | 4              |
| 6       | 69     | 74    | 5              |
| 7       | 71     | 76    | 5              |
| 8       | 67     | 69    | 2              |
| 9       | 73     | 79    | 6              |
| 10      | 64     | 68    | 4              |

**Step 3: Calculate Mean Difference**
```
Sum of differences = 7 + 5 + 3 + 6 + 4 + 5 + 5 + 2 + 6 + 4 = 47

d̄ = 47 / 10 = 4.7 points
```

**Step 4: Calculate Standard Deviation of Differences**
```
Deviations from d̄ = 4.7:
7-4.7 = 2.3
5-4.7 = 0.3
3-4.7 = -1.7
6-4.7 = 1.3
4-4.7 = -0.7
5-4.7 = 0.3
5-4.7 = 0.3
2-4.7 = -2.7
6-4.7 = 1.3
4-4.7 = -0.7

Squared deviations:
5.29, 0.09, 2.89, 1.69, 0.49, 0.09, 0.09, 7.29, 1.69, 0.49

Sum = 20.1

sᵈ² = 20.1 / 9 = 2.233
sᵈ = √2.233 = 1.494
```

**Step 5: Calculate t-Statistic**
```
t = d̄ / (sᵈ / √n)
t = 4.7 / (1.494 / √10)
t = 4.7 / (1.494 / 3.162)
t = 4.7 / 0.472
t = 9.96
```

**Step 6: Critical Value**
```
df = n - 1 = 10 - 1 = 9
α = 0.05 (one-tailed, right)
t_critical = 1.833
```

**Step 7: Decision**
```
Since 9.96 > 1.833, we REJECT H₀
```

**Step 8: 95% Confidence Interval for Mean Difference**
```
CI = d̄ ± (t_critical × sᵈ/√n)
CI = 4.7 ± (2.262 × 0.472)    [using two-tailed t for CI]
CI = 4.7 ± 1.07
CI = [3.63, 5.77]
```

**Step 9: Effect Size**
```
Cohen's d = d̄ / sᵈ
d = 4.7 / 1.494 = 3.15 (Very large effect)
```

**Step 10: Interpretation**

"Tutoring significantly improved test scores (t(9) = 9.96, p < 0.001, d = 3.15). Students improved by an average of 4.7 points (95% CI: [3.63, 5.77]), with all 10 students showing improvement. This represents a very large and practically meaningful effect of tutoring."

---

### Problem 3.2: Blood Pressure Medication

**Scenario:**
Testing a blood pressure medication. Systolic BP measured before and after 4 weeks:

| Patient | Before | After |
|---------|--------|-------|
| 1       | 145    | 138   |
| 2       | 152    | 145   |
| 3       | 148    | 142   |
| 4       | 155    | 148   |
| 5       | 150    | 146   |
| 6       | 147    | 144   |

**Question:** Does medication reduce blood pressure? (α = 0.05)

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: μ_d ≤ 0 (no reduction in BP)
- H₁: μ_d > 0 (BP decreases)
- α = 0.05
- One-tailed test (expecting reduction)

**Step 2: Calculate Differences (Before - After)**
```
Patient 1: 145 - 138 = 7
Patient 2: 152 - 145 = 7
Patient 3: 148 - 142 = 6
Patient 4: 155 - 148 = 7
Patient 5: 150 - 146 = 4
Patient 6: 147 - 144 = 3

d̄ = (7+7+6+7+4+3) / 6 = 34 / 6 = 5.67 mmHg
```

**Step 3: Standard Deviation**
```
Deviations: 1.33, 1.33, 0.33, 1.33, -1.67, -2.67
Squared: 1.77, 1.77, 0.11, 1.77, 2.79, 7.13
Sum = 15.34

sᵈ² = 15.34 / 5 = 3.068
sᵈ = 1.752
```

**Step 4: t-Statistic**
```
t = 5.67 / (1.752 / √6)
t = 5.67 / 0.715
t = 7.93
```

**Step 5: Critical Value**
```
df = 5
α = 0.05 (one-tailed)
t_critical = 2.015
```

**Step 6: Decision**
```
Since 7.93 > 2.015, we REJECT H₀
```

**Step 7: Interpretation**

"The medication significantly reduces systolic blood pressure (t(5) = 7.93, p < 0.01). Patients experienced an average reduction of 5.67 mmHg, which is both statistically significant and clinically meaningful. All patients showed some reduction in blood pressure."

---

## Problem Set 4: Mixed Practice

### Problem 4.1: Choosing the Right Test

For each scenario, identify which t-test to use:

**A.** Comparing IQ scores of twins where one twin attended preschool and one didn't
**Answer:** Paired t-test (matched pairs - twins are related)

**B.** Testing if average customer satisfaction score differs from the industry standard of 7.5
**Answer:** One-sample t-test (comparing to known value)

**C.** Comparing reaction times between coffee drinkers and non-coffee drinkers
**Answer:** Independent two-sample t-test (different, unrelated groups)

**D.** Measuring anxiety levels before and after meditation training
**Answer:** Paired t-test (same people, two time points)

**E.** Testing if students from School A score differently than students from School B
**Answer:** Independent two-sample t-test (different schools, different students)

---

## Key Formulas Reference

### One-Sample t-Test
```
t = (x̄ - μ₀) / (s / √n)
df = n - 1
```

### Independent Two-Sample t-Test
```
s²ₚ = [(n₁-1)s₁² + (n₂-1)s₂²] / (n₁ + n₂ - 2)
t = (x̄₁ - x̄₂) / √[s²ₚ(1/n₁ + 1/n₂)]
df = n₁ + n₂ - 2
```

### Paired Sample t-Test
```
t = d̄ / (sᵈ / √n)
df = n - 1
```

### Effect Size
```
Cohen's d = (x̄₁ - x̄₂) / s_pooled
```

### Confidence Interval
```
CI = x̄ ± (t_critical × SE)
where SE = s / √n
```

---

## Tips for Success

1. **Always state hypotheses first** - before calculating anything
2. **Show all calculation steps** - even if using software
3. **Check your assumptions** - normality, independence, equal variances
4. **Use appropriate critical values** - one-tailed vs two-tailed
5. **Calculate effect sizes** - statistical significance ≠ practical importance
6. **Interpret in context** - don't just report numbers
7. **Double-check df** - most common source of errors
8. **Round consistently** - typically 2-3 decimal places

---

## Common Errors Checklist

Before finalizing your answer, check:

□ Used correct degrees of freedom?
□ Matched test type to hypothesis (one-tailed vs two-tailed)?
□ Used (n-1) when calculating standard deviation?
□ Compared to correct critical value?
□ Stated conclusion in context of problem?
□ Calculated and interpreted effect size?
□ Checked all assumptions?

