# Complete Guide to t-Tests in Hypothesis Testing
## From Basic to Advanced

---

## Table of Contents
1. Introduction to Hypothesis Testing
2. Understanding the t-Distribution
3. Degrees of Freedom
4. Types of t-Tests
5. One-Sample t-Test
6. Two-Sample t-Test (Independent)
7. Paired Sample t-Test
8. One-Tailed vs Two-Tailed Tests
9. Step-by-Step Calculation Examples
10. Interpreting Results
11. Common Pitfalls and Best Practices

---

## 1. Introduction to Hypothesis Testing

### What is Hypothesis Testing?

Hypothesis testing is a statistical method used to make decisions about a population based on sample data. Think of it as a formal way to test whether what you observe in your data is likely due to chance or represents a real effect.

### Key Components:

**Null Hypothesis (H₀)**: The default assumption that there is no effect or no difference
- Example: "The new drug has no effect on blood pressure"
- We assume this is true unless evidence proves otherwise

**Alternative Hypothesis (H₁ or Hₐ)**: What we're trying to prove
- Example: "The new drug changes blood pressure"
- This is what we suspect is actually true

**Significance Level (α)**: The threshold for deciding if results are significant
- Common value: α = 0.05 (5%)
- This means we're willing to accept a 5% chance of incorrectly rejecting the null hypothesis

**Test Statistic**: A number calculated from your data that helps you make a decision
- For t-tests, this is the t-statistic

**p-value**: The probability of getting your results (or more extreme) if the null hypothesis is true
- If p-value < α, we reject the null hypothesis
- If p-value ≥ α, we fail to reject the null hypothesis

---

## 2. Understanding the t-Distribution

### What is the t-Distribution?

The t-distribution is a probability distribution that looks similar to the normal distribution but has heavier tails. It was discovered by William Sealy Gosset, who published under the pseudonym "Student," which is why it's also called Student's t-distribution.

### Key Characteristics:

1. **Bell-shaped and symmetric** around zero (like the normal distribution)
2. **Heavier tails** than the normal distribution (more probability in the extremes)
3. **Shape changes** based on degrees of freedom
4. **Approaches normal distribution** as sample size increases

### Why Use t-Distribution Instead of Normal Distribution?

```
When to Use t-Distribution:
├── Small sample sizes (typically n < 30)
├── Population standard deviation is UNKNOWN
└── Sample standard deviation is used to estimate it

When to Use Normal Distribution:
├── Large sample sizes (typically n ≥ 30)
└── Population standard deviation is KNOWN
```

### Visual Concept:

```
        t-distribution vs Normal Distribution
        
              │
              │     ┌─────┐
              │   ┌─┘     └─┐
              │  ┌┘         └┐
              │ ┌┘           └┐
    Frequency │┌┘   Normal   └┐
              │┘   (thin tails)└┐
              │   t-distribution └┐
              │   (heavy tails)   └─
              └─────────────────────────
                      Values
                      
    Note: As df increases, t approaches normal
```

---

## 3. Degrees of Freedom (df)

### What Are Degrees of Freedom?

Degrees of freedom represent the number of independent pieces of information available to estimate a parameter. Think of it as "how many values are free to vary."

### Intuitive Example:

Imagine you have 5 numbers that must sum to 20:
- You can freely choose the first 4 numbers: 3, 5, 7, 2
- The 5th number is NOT free - it must be 3 (to make the sum = 20)
- Degrees of freedom = 5 - 1 = 4

### Formulas for Different t-Tests:

**One-Sample t-Test:**
```
df = n - 1

where n = sample size
```

**Independent Two-Sample t-Test:**
```
df = n₁ + n₂ - 2

where n₁ = size of sample 1
      n₂ = size of sample 2
```

**Paired Sample t-Test:**
```
df = n - 1

where n = number of pairs
```

### Why Does df Matter?

- **Smaller df** → heavier tails → harder to reject null hypothesis → need stronger evidence
- **Larger df** → closer to normal distribution → easier to detect real effects
- **Critical values** from t-table depend on df

---

## 4. Types of t-Tests

### Overview Diagram:

```
                    t-Tests
                       │
        ┌──────────────┼──────────────┐
        │              │              │
   One-Sample     Two-Sample      Paired
      t-Test        t-Test         t-Test
        │              │              │
        │              │              │
    Compare        Compare        Compare
    sample         two            related
    mean to     independent       samples
    known          groups        (before/after)
    value
        │              │              │
        │              │              │
    Example:       Example:        Example:
    "Is average   "Do men and    "Does weight
    height = 170   women differ   change after
    cm?"          in height?"     diet?"
```

### Quick Decision Guide:

```
Which t-Test Should I Use?

START
  │
  ├─ Do you have ONE group?
  │   └─ YES → One-Sample t-Test
  │
  └─ Do you have TWO groups?
      │
      ├─ Are the groups INDEPENDENT?
      │   └─ YES → Independent Two-Sample t-Test
      │
      └─ Are the groups RELATED (same subjects measured twice)?
          └─ YES → Paired Sample t-Test
```

---

## 5. One-Sample t-Test

### Purpose:
Compare a sample mean to a known or hypothesized population mean.

### When to Use:
- You have one group of data
- You want to compare it to a specific value
- Population standard deviation is unknown

### Hypotheses:

**Two-Tailed Test:**
- H₀: μ = μ₀ (population mean equals hypothesized value)
- H₁: μ ≠ μ₀ (population mean differs from hypothesized value)

**Right-Tailed Test:**
- H₀: μ ≤ μ₀
- H₁: μ > μ₀ (population mean is greater)

**Left-Tailed Test:**
- H₀: μ ≥ μ₀
- H₁: μ < μ₀ (population mean is less)

### Formula:

```
t = (x̄ - μ₀) / (s / √n)

where:
x̄ = sample mean
μ₀ = hypothesized population mean
s = sample standard deviation
n = sample size
df = n - 1
```

### Detailed Calculation Example:

**Scenario:** A coffee shop claims their large coffee contains 16 oz. You suspect it's less. You measure 10 cups:

Data: 15.8, 15.5, 15.9, 15.7, 15.6, 15.8, 15.4, 15.7, 15.5, 15.6

**Step 1: State Hypotheses**
- H₀: μ ≥ 16 oz (coffee shop's claim is correct)
- H₁: μ < 16 oz (coffee is less than claimed) [LEFT-TAILED]
- α = 0.05

**Step 2: Calculate Sample Statistics**

Calculate mean (x̄):
```
x̄ = (15.8 + 15.5 + 15.9 + 15.7 + 15.6 + 15.8 + 15.4 + 15.7 + 15.5 + 15.6) / 10
x̄ = 156.5 / 10
x̄ = 15.65 oz
```

Calculate sample standard deviation (s):
```
Step 1: Find deviations from mean
(15.8 - 15.65) = 0.15
(15.5 - 15.65) = -0.15
(15.9 - 15.65) = 0.25
(15.7 - 15.65) = 0.05
(15.6 - 15.65) = -0.05
(15.8 - 15.65) = 0.15
(15.4 - 15.65) = -0.25
(15.7 - 15.65) = 0.05
(15.5 - 15.65) = -0.15
(15.6 - 15.65) = -0.05

Step 2: Square each deviation
0.0225, 0.0225, 0.0625, 0.0025, 0.0025, 0.0225, 0.0625, 0.0025, 0.0225, 0.0025

Step 3: Sum of squared deviations
Σ(x - x̄)² = 0.225

Step 4: Calculate variance
s² = Σ(x - x̄)² / (n - 1) = 0.225 / 9 = 0.025

Step 5: Calculate standard deviation
s = √0.025 = 0.158 oz
```

**Step 3: Calculate t-Statistic**
```
t = (x̄ - μ₀) / (s / √n)
t = (15.65 - 16) / (0.158 / √10)
t = -0.35 / (0.158 / 3.162)
t = -0.35 / 0.050
t = -7.00
```

**Step 4: Determine Critical Value**
- df = n - 1 = 10 - 1 = 9
- α = 0.05 (one-tailed, left)
- From t-table: t_critical = -1.833

**Step 5: Make Decision**
```
Decision Rule for Left-Tailed Test:
Reject H₀ if t < -t_critical

Our result: t = -7.00
Critical value: -1.833

Since -7.00 < -1.833, we REJECT H₀
```

**Step 6: Interpret**

We have strong evidence (p < 0.001) that the coffee shop is serving less than 16 oz on average. The actual average appears to be around 15.65 oz.

---

## 6. Two-Sample Independent t-Test

### Purpose:
Compare means of two independent groups.

### When to Use:
- Two separate, unrelated groups
- Different subjects in each group
- Want to compare their means

### Assumptions:
1. Independence of observations
2. Approximate normality (or large samples)
3. Homogeneity of variance (equal variances)

### Formula (Equal Variances):

```
t = (x̄₁ - x̄₂) / √[s²ₚ(1/n₁ + 1/n₂)]

where:
x̄₁, x̄₂ = means of samples 1 and 2
n₁, n₂ = sizes of samples 1 and 2
s²ₚ = pooled variance
df = n₁ + n₂ - 2

Pooled variance:
s²ₚ = [(n₁-1)s₁² + (n₂-1)s₂²] / (n₁ + n₂ - 2)
```

### Detailed Calculation Example:

**Scenario:** Does a new teaching method improve test scores?

**Control Group (traditional method):** 85, 88, 82, 90, 87, 84, 86
**Treatment Group (new method):** 92, 95, 89, 93, 94, 91, 90

**Step 1: State Hypotheses**
- H₀: μ₁ = μ₂ (no difference in means)
- H₁: μ₁ ≠ μ₂ (means are different) [TWO-TAILED]
- α = 0.05

**Step 2: Calculate Sample Statistics**

Control Group:
```
n₁ = 7
x̄₁ = (85 + 88 + 82 + 90 + 87 + 84 + 86) / 7 = 602 / 7 = 86.0

Deviations: -1, 2, -4, 4, 1, -2, 0
Squared: 1, 4, 16, 16, 1, 4, 0
Sum: 42

s₁² = 42 / (7-1) = 42 / 6 = 7.0
s₁ = √7.0 = 2.65
```

Treatment Group:
```
n₂ = 7
x̄₂ = (92 + 95 + 89 + 93 + 94 + 91 + 90) / 7 = 644 / 7 = 92.0

Deviations: 0, 3, -3, 1, 2, -1, -2
Squared: 0, 9, 9, 1, 4, 1, 4
Sum: 28

s₂² = 28 / (7-1) = 28 / 6 = 4.67
s₂ = √4.67 = 2.16
```

**Step 3: Calculate Pooled Variance**
```
s²ₚ = [(n₁-1)s₁² + (n₂-1)s₂²] / (n₁ + n₂ - 2)
s²ₚ = [(7-1)(7.0) + (7-1)(4.67)] / (7 + 7 - 2)
s²ₚ = [6(7.0) + 6(4.67)] / 12
s²ₚ = [42.0 + 28.0] / 12
s²ₚ = 70.0 / 12
s²ₚ = 5.83
```

**Step 4: Calculate t-Statistic**
```
t = (x̄₁ - x̄₂) / √[s²ₚ(1/n₁ + 1/n₂)]
t = (86.0 - 92.0) / √[5.83(1/7 + 1/7)]
t = -6.0 / √[5.83(0.286)]
t = -6.0 / √1.667
t = -6.0 / 1.291
t = -4.65
```

**Step 5: Determine Critical Value**
```
df = n₁ + n₂ - 2 = 7 + 7 - 2 = 12
α = 0.05 (two-tailed)
From t-table: t_critical = ±2.179
```

**Step 6: Make Decision**
```
Decision Rule for Two-Tailed Test:
Reject H₀ if |t| > t_critical

Our result: |t| = |-4.65| = 4.65
Critical value: 2.179

Since 4.65 > 2.179, we REJECT H₀
```

**Step 7: Interpret**

The new teaching method produces significantly higher test scores (mean difference = 6.0 points, p < 0.001). The treatment group scored an average of 92.0 compared to 86.0 in the control group.

---

## 7. Paired Sample t-Test

### Purpose:
Compare two related samples (same subjects measured twice, or matched pairs).

### When to Use:
- Before and after measurements
- Matched pairs design
- Same subjects, two conditions

### Advantages:
- Controls for individual differences
- More powerful than independent t-test
- Requires fewer subjects

### Formula:

```
t = d̄ / (sᵈ / √n)

where:
d̄ = mean of differences
sᵈ = standard deviation of differences
n = number of pairs
df = n - 1

Steps:
1. Calculate difference for each pair: d = x₁ - x₂
2. Find mean of differences: d̄
3. Find standard deviation of differences: sᵈ
4. Calculate t-statistic
```

### Detailed Calculation Example:

**Scenario:** Does a weight loss program work? Measure 8 people before and after:

| Person | Before | After | Difference (d) |
|--------|--------|-------|----------------|
| 1      | 180    | 175   | 5              |
| 2      | 195    | 188   | 7              |
| 3      | 170    | 168   | 2              |
| 4      | 185    | 179   | 6              |
| 5      | 200    | 192   | 8              |
| 6      | 175    | 172   | 3              |
| 7      | 190    | 185   | 5              |
| 8      | 165    | 163   | 2              |

**Step 1: State Hypotheses**
- H₀: μᵈ = 0 (no weight change)
- H₁: μᵈ > 0 (weight decreased) [RIGHT-TAILED]
- α = 0.05

**Step 2: Calculate Mean Difference**
```
d̄ = (5 + 7 + 2 + 6 + 8 + 3 + 5 + 2) / 8
d̄ = 38 / 8
d̄ = 4.75 lbs
```

**Step 3: Calculate Standard Deviation of Differences**
```
Deviations from d̄ = 4.75:
(5 - 4.75) = 0.25
(7 - 4.75) = 2.25
(2 - 4.75) = -2.75
(6 - 4.75) = 1.25
(8 - 4.75) = 3.25
(3 - 4.75) = -1.75
(5 - 4.75) = 0.25
(2 - 4.75) = -2.75

Squared deviations:
0.0625, 5.0625, 7.5625, 1.5625, 10.5625, 3.0625, 0.0625, 7.5625

Sum = 35.5

sᵈ² = 35.5 / (8-1) = 35.5 / 7 = 5.071
sᵈ = √5.071 = 2.252
```

**Step 4: Calculate t-Statistic**
```
t = d̄ / (sᵈ / √n)
t = 4.75 / (2.252 / √8)
t = 4.75 / (2.252 / 2.828)
t = 4.75 / 0.796
t = 5.97
```

**Step 5: Determine Critical Value**
```
df = n - 1 = 8 - 1 = 7
α = 0.05 (one-tailed, right)
From t-table: t_critical = 1.895
```

**Step 6: Make Decision**
```
Decision Rule for Right-Tailed Test:
Reject H₀ if t > t_critical

Our result: t = 5.97
Critical value: 1.895

Since 5.97 > 1.895, we REJECT H₀
```

**Step 7: Interpret**

The weight loss program is effective (p < 0.001). Participants lost an average of 4.75 lbs, with individual losses ranging from 2 to 8 lbs.

---

## 8. One-Tailed vs Two-Tailed Tests

### Visual Representation:

```
TWO-TAILED TEST (H₁: μ ≠ μ₀)
"Is there ANY difference?"

        Rejection   │   Rejection
        Region      │   Region
          2.5%      │     2.5%
            ▼       │       ▼
        ────┐       │       ┌────
            │   ┌───┴───┐   │
            │  ┌┘       └┐  │
            │ ┌┘         └┐ │
            │┌┘           └┐│
        ────┘               └────
    -t_critical    0    +t_critical
    
    Reject H₀ if: |t| > t_critical


RIGHT-TAILED TEST (H₁: μ > μ₀)
"Is it GREATER?"

                    │   Rejection
                    │   Region
                    │     5%
                    │      ▼
        ────────────┴───────┌────
               ┌────────┐   │
              ┌┘        └┐  │
             ┌┘          └┐ │
            ┌┘            └┐│
        ────┘               └────
           0           +t_critical
    
    Reject H₀ if: t > t_critical


LEFT-TAILED TEST (H₁: μ < μ₀)
"Is it LESS?"

        Rejection   │
        Region      │
          5%        │
           ▼        │
        ───┐        │
           │   ┌────┴────────
           │  ┌┘        └┐
           │ ┌┘          └┐
           │┌┘            └┐
        ───┘               └────
    -t_critical        0
    
    Reject H₀ if: t < -t_critical
```

### Decision Framework:

```
How to Choose:

TWO-TAILED TEST:
├─ When: You care about differences in EITHER direction
├─ Example: "Does this drug CHANGE blood pressure?"
├─ H₁: μ ≠ μ₀
└─ Use when: No prior expectation of direction

RIGHT-TAILED TEST:
├─ When: You only care if it's GREATER
├─ Example: "Does this training IMPROVE performance?"
├─ H₁: μ > μ₀
└─ Use when: Only positive change matters

LEFT-TAILED TEST:
├─ When: You only care if it's LESS
├─ Example: "Does this process REDUCE costs?"
├─ H₁: μ < μ₀
└─ Use when: Only negative change matters
```

### Critical Values Comparison:

For df = 20, α = 0.05:

| Test Type    | Critical Value(s) | Rejection Region   |
|--------------|-------------------|--------------------|
| Two-tailed   | ±2.086            | t < -2.086 OR t > 2.086 |
| Right-tailed | +1.725            | t > 1.725          |
| Left-tailed  | -1.725            | t < -1.725         |

**Important:** One-tailed tests have less extreme critical values because all 5% is in one tail, making it "easier" to reject H₀. However, you can ONLY detect effects in the predicted direction.

---

## 9. Complete Workflow Diagram

```
                HYPOTHESIS TESTING WITH t-TESTS
                          
    ┌────────────────────────────────────────────────┐
    │ STEP 1: Define Your Research Question          │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 2: Choose Appropriate t-Test              │
    │  • One sample? → One-sample t-test             │
    │  • Two independent groups? → Independent t-test│
    │  • Paired data? → Paired t-test                │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 3: State Hypotheses                       │
    │  • Null Hypothesis (H₀)                        │
    │  • Alternative Hypothesis (H₁)                 │
    │  • Choose one-tailed or two-tailed             │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 4: Set Significance Level (α)             │
    │  • Usually α = 0.05 or 0.01                    │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 5: Calculate Sample Statistics            │
    │  • Sample mean(s): x̄                          │
    │  • Sample standard deviation(s): s             │
    │  • Sample size(s): n                           │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 6: Calculate t-Statistic                  │
    │  • Use appropriate formula for your test type  │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 7: Determine Degrees of Freedom (df)      │
    │  • Calculate based on test type                │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 8: Find Critical Value                    │
    │  • Look up in t-table using df and α           │
    └──────────────────┬─────────────────────────────┘
                       │
    ┌──────────────────▼─────────────────────────────┐
    │ STEP 9: Make Decision                          │
    │  • Compare t-statistic to critical value       │
    │  • Or compare p-value to α                     │
    └──────────────────┬─────────────────────────────┘
                       │
              ┌────────┴────────┐
              │                 │
    ┌─────────▼──────┐  ┌───────▼────────┐
    │ Reject H₀      │  │ Fail to Reject │
    │                │  │ H₀             │
    └────────┬───────┘  └───────┬────────┘
             │                  │
    ┌────────▼──────────────────▼────────┐
    │ STEP 10: Interpret Results         │
    │  • State conclusion in context     │
    │  • Report effect size              │
    │  • Consider practical significance │
    └────────────────────────────────────┘
```

---

## 10. Reading t-Tables

### Understanding the t-Table:

```
Sample t-Table Structure:

df  │  α = 0.10   α = 0.05   α = 0.01  (Two-tailed)
    │  α = 0.05   α = 0.025  α = 0.005 (One-tailed)
────┼─────────────────────────────────
 1  │   6.314     12.706     63.657
 2  │   2.920      4.303      9.925
 3  │   2.353      3.182      5.841
 5  │   2.015      2.571      4.032
10  │   1.812      2.228      3.169
20  │   1.725      2.086      2.845
30  │   1.697      2.042      2.750
∞   │   1.645      1.960      2.576
```

### How to Use:

1. **Find your df** (degrees of freedom) in the left column
2. **Find your α** (significance level) in the top row
   - For two-tailed tests, use the larger α values
   - For one-tailed tests, use the smaller α values
3. **Intersection gives your critical value**

### Example:
- df = 10
- Two-tailed test
- α = 0.05
- Critical value = ±2.228

---

## 11. Effect Size and Power

### Effect Size (Cohen's d)

Effect size tells you HOW LARGE the difference is, not just whether it's statistically significant.

```
Cohen's d = (x̄₁ - x̄₂) / s_pooled

Interpretation:
│ d │ < 0.2   : Negligible effect
│ d │ ≈ 0.2   : Small effect
│ d │ ≈ 0.5   : Medium effect
│ d │ ≈ 0.8   : Large effect
│ d │ > 1.3   : Very large effect
```

### Statistical Power

Power is the probability of detecting an effect when it truly exists.

```
Power = 1 - β (where β = Type II error rate)

Desired power: Usually 0.80 or higher (80%)

Factors affecting power:
├── Sample size ↑ → Power ↑
├── Effect size ↑ → Power ↑
├── Significance level (α) ↑ → Power ↑
└── Variability ↓ → Power ↑
```

---

## 12. Common Mistakes and How to Avoid Them

### Mistake 1: Choosing Wrong Test Type

❌ **Wrong:** Using independent t-test for before/after measurements
✅ **Right:** Use paired t-test when same subjects measured twice

### Mistake 2: Multiple Testing Without Correction

❌ **Wrong:** Conducting many t-tests and using α = 0.05 for each
✅ **Right:** Apply Bonferroni correction: α_adjusted = α / number_of_tests

Example: 10 tests with α = 0.05
- Adjusted α = 0.05 / 10 = 0.005

### Mistake 3: Ignoring Assumptions

**Check These Before Using t-Tests:**

1. **Independence:** Observations are independent
2. **Normality:** Data approximately normally distributed (or n > 30)
3. **Equal Variances:** For independent t-test (can use Welch's t-test if violated)

### Mistake 4: Confusing Statistical and Practical Significance

❌ **Wrong:** "p < 0.05, so the result is important"
✅ **Right:** Consider both:
- Statistical significance (p-value)
- Practical significance (effect size, context)

Example: A drug reduces blood pressure by 0.5 mmHg (p < 0.001)
- Statistically significant ✓
- Clinically meaningful? Probably not

### Mistake 5: One-Tailed Test After Seeing Data

❌ **Wrong:** Looking at data, then choosing one-tailed test
✅ **Right:** Decide on one-tailed vs two-tailed BEFORE seeing results

### Mistake 6: Misinterpreting p-values

❌ **Wrong:** "p = 0.04 means there's a 4% chance the null hypothesis is true"
✅ **Right:** "p = 0.04 means there's a 4% chance of getting these results (or more extreme) IF the null hypothesis is true"

---

## 13. Assumptions and Diagnostics

### Checking Normality

**For Small Samples (n < 30):**
1. Visual inspection (histogram, Q-Q plot)
2. Shapiro-Wilk test

**For Large Samples (n ≥ 30):**
- Central Limit Theorem applies
- t-test is robust to non-normality

### Checking Equal Variances (Homogeneity)

**Levene's Test:**
- H₀: Variances are equal
- H₁: Variances are not equal

**Rule of Thumb:**
- If ratio of larger variance to smaller variance < 2, equal variance assumption is reasonable

**If Variances Unequal:**
- Use Welch's t-test (doesn't assume equal variances)

---

## 14. Advanced Topics

### Welch's t-Test (Unequal Variances)

When variances are not equal between groups:

```
t = (x̄₁ - x̄₂) / √(s₁²/n₁ + s₂²/n₂)

df = [(s₁²/n₁ + s₂²/n₂)²] / [(s₁²/n₁)²/(n₁-1) + (s₂²/n₂)²/(n₂-1)]
```

### Confidence Intervals

A 95% confidence interval for the mean:

```
CI = x̄ ± (t_critical × SE)

where SE = s / √n

Interpretation:
"We are 95% confident that the true population mean 
lies between [lower bound] and [upper bound]"
```

**Example:**
- x̄ = 100
- s = 15
- n = 25
- df = 24
- t_critical (95%, two-tailed) = 2.064

```
SE = 15 / √25 = 15 / 5 = 3
CI = 100 ± (2.064 × 3)
CI = 100 ± 6.19
CI = [93.81, 106.19]
```

---

## 15. Reporting Results (APA Style)

### Template:

"A [test type] t-test was conducted to compare [variable] between [groups/conditions]. There was a [significant/non-significant] difference in [variable] for [Group 1] (M = [mean], SD = [SD]) and [Group 2] (M = [mean], SD = [SD]); t([df]) = [t-value], p = [p-value], Cohen's d = [effect size]."

### Example:

"An independent samples t-test was conducted to compare test scores between the traditional teaching method and the new teaching method. There was a significant difference in scores for the traditional method (M = 86.0, SD = 2.65) and the new method (M = 92.0, SD = 2.16); t(12) = -4.65, p < 0.001, Cohen's d = 2.48."

---

## 16. Practice Problems

### Problem 1: One-Sample t-Test

A manufacturer claims their light bulbs last 1000 hours on average. You test 8 bulbs:
950, 1020, 980, 1050, 990, 1010, 970, 1030

Test if the claim is accurate (α = 0.05, two-tailed).

**Solution Steps:**
1. H₀: μ = 1000; H₁: μ ≠ 1000
2. Calculate x̄ = 1000
3. Calculate s = 33.17
4. Calculate t = (1000 - 1000) / (33.17/√8) = 0
5. df = 7, t_critical = ±2.365
6. Since |0| < 2.365, fail to reject H₀
7. Conclusion: No evidence that bulbs differ from claimed 1000 hours

### Problem 2: Independent t-Test

Compare sleep quality (scale 1-10) between caffeine and placebo groups:
- Caffeine: 5, 6, 4, 5, 6, 5
- Placebo: 7, 8, 7, 9, 8, 7

Test if caffeine affects sleep quality (α = 0.05, two-tailed).

**Your Turn:** Work through the solution!

### Problem 3: Paired t-Test

Measure anxiety levels before and after therapy:
- Before: 65, 70, 68, 72, 66, 69, 71, 67
- After: 60, 62, 64, 65, 58, 63, 66, 61

Test if therapy reduces anxiety (α = 0.05, one-tailed).

**Your Turn:** Work through the solution!

---

## 17. Quick Reference Formulas

### One-Sample t-Test
```
t = (x̄ - μ₀) / (s / √n)
df = n - 1
```

### Independent Two-Sample t-Test
```
t = (x̄₁ - x̄₂) / √[s²ₚ(1/n₁ + 1/n₂)]
s²ₚ = [(n₁-1)s₁² + (n₂-1)s₂²] / (n₁ + n₂ - 2)
df = n₁ + n₂ - 2
```

### Paired Sample t-Test
```
t = d̄ / (sᵈ / √n)
df = n - 1
```

### Standard Error (SE)
```
SE = s / √n
```

### Confidence Interval
```
CI = x̄ ± (t_critical × SE)
```

### Cohen's d
```
d = (x̄₁ - x̄₂) / s_pooled
```

---

## 18. Decision Rules Summary

| Test Type    | Reject H₀ When...           |
|--------------|----------------------------|
| Two-tailed   | │t│ > t_critical          |
| Right-tailed | t > t_critical             |
| Left-tailed  | t < -t_critical            |

Alternative using p-value:
- Reject H₀ when p-value < α

---

## Conclusion

The t-test is one of the most powerful tools in statistical hypothesis testing. Remember:

1. **Choose the right test** for your data structure
2. **Check assumptions** before running the test
3. **State hypotheses clearly** before collecting data
4. **Calculate carefully** and double-check your work
5. **Interpret in context** - statistics serve your research question
6. **Report completely** - include effect sizes and confidence intervals
7. **Think critically** - statistical significance ≠ practical importance

### Next Steps for Learning:

1. Practice with real datasets
2. Learn statistical software (R, Python, SPSS)
3. Explore ANOVA (extension of t-test to 3+ groups)
4. Study non-parametric alternatives (when assumptions violated)
5. Learn about experimental design

---

## Additional Resources

### Recommended Reading:
- Understanding the t-distribution and its properties
- Effect sizes and power analysis
- Multiple comparison corrections
- Non-parametric alternatives (Mann-Whitney U, Wilcoxon)

### Online Calculators:
- t-critical value calculators
- p-value calculators
- Effect size calculators
- Sample size calculators

---

**Remember:** Statistics is a tool for understanding the world. The mathematics is important, but never lose sight of what your numbers mean in the real world!

