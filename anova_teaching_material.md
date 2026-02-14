# ANOVA (Analysis of Variance) - Complete Teaching Material
## From Foundations to Advanced Applications

---

## Table of Contents
1. Introduction & Motivation
2. Prerequisites & Foundational Concepts
3. One-Way ANOVA (Simple)
4. Mathematical Framework
5. Assumptions & Diagnostics
6. Two-Way ANOVA (Intermediate)
7. Advanced ANOVA Techniques
8. Practical Examples with Solutions
9. Common Pitfalls & Best Practices
10. Practice Problems

---

## 1. Introduction & Motivation

### What is ANOVA?

ANOVA (Analysis of Variance) is a statistical method used to test whether there are significant differences between the means of three or more groups. While it's called "analysis of variance," it actually compares means by analyzing variances.

### Why Do We Need ANOVA?

**The Problem:**
Imagine you're testing a new drug at three different dosages (low, medium, high) and want to know if any dosage affects blood pressure differently. You might think: "Why not just do multiple t-tests?"

**Why Not Multiple t-tests?**
- If you compare 3 groups, you need 3 t-tests (A vs B, B vs C, A vs C)
- If you compare 5 groups, you need 10 t-tests!
- Each test has a 5% chance of Type I error (false positive)
- Multiple tests inflate your overall error rate dramatically

**The Solution:**
ANOVA performs a single test to determine if ANY group means differ, controlling the overall error rate at 5% (or your chosen α level).

### Real-World Applications
- **Medicine:** Comparing effectiveness of different treatments
- **Agriculture:** Testing yields from different fertilizers
- **Education:** Comparing teaching methods across multiple classes
- **Manufacturing:** Quality control across different production lines
- **Psychology:** Comparing behavioral responses to different stimuli

---

## 2. Prerequisites & Foundational Concepts

### Statistical Concepts You Need

**1. Mean (Average)**
The sum of values divided by the count:
```
x̄ = (x₁ + x₂ + ... + xₙ) / n
```

**2. Variance**
How spread out data is from the mean:
```
s² = Σ(xᵢ - x̄)² / (n - 1)
```

**3. Hypothesis Testing Review**

- **Null Hypothesis (H₀):** The default assumption (usually "no effect" or "no difference")
- **Alternative Hypothesis (H₁):** What we're trying to prove
- **p-value:** Probability of observing data this extreme if H₀ is true
- **Significance level (α):** Threshold for rejecting H₀ (commonly 0.05)

**Decision Rule:**
- If p-value < α: Reject H₀ (significant result)
- If p-value ≥ α: Fail to reject H₀ (not significant)

**4. The F-Distribution**

ANOVA uses the F-statistic, which follows an F-distribution. The F-statistic is always positive and is the ratio of two variances.

---

## 3. One-Way ANOVA (Simple Introduction)

### The Basic Question

**One-Way ANOVA answers:** "Are there differences among the means of 3+ independent groups?"

### Simple Example: Coffee and Productivity

Suppose we test three types of coffee (Regular, Espresso, Decaf) on worker productivity (tasks completed per hour):

```
Regular:  [15, 17, 16, 18, 14]
Espresso: [22, 21, 23, 20, 24]
Decaf:    [12, 13, 11, 14, 10]
```

**Visual Intuition:**
```
Productivity (tasks/hour)
    25|              *
    20|         * *  *  *
    15|    *  * *  *
    10|          * * * *
     5|
       |____________________
        Regular Espresso Decaf
```

Just by looking, Espresso seems different. ANOVA tells us if this difference is statistically significant or could happen by chance.

### Hypotheses

**H₀:** μ₁ = μ₂ = μ₃ (all group means are equal)
**H₁:** At least one group mean is different

### The Core Logic

ANOVA partitions the total variation in the data into two sources:

1. **Between-Group Variation:** Differences between group means
2. **Within-Group Variation:** Natural variation within each group

```
Total Variation = Between-Group Variation + Within-Group Variation
```

**The F-Statistic:**
```
F = Between-Group Variance / Within-Group Variance
```

**Interpretation:**
- **Large F:** Between-group differences are large relative to within-group variation → Likely significant
- **Small F:** Between-group differences are small relative to within-group variation → Likely not significant

### Step-by-Step Calculation (Simple Example)

Let's work through the coffee example:

**Step 1: Calculate Group Means**
```
Regular:  (15+17+16+18+14)/5 = 16
Espresso: (22+21+23+20+24)/5 = 22
Decaf:    (12+13+11+14+10)/5 = 12
```

**Step 2: Calculate Grand Mean**
```
Grand Mean = (16+22+12)/3 = 16.67
(Or: sum of all observations / total n)
```

**Step 3: Calculate Sum of Squares**

*Between-Group Sum of Squares (SSB):*
```
SSB = n₁(x̄₁ - x̄)² + n₂(x̄₂ - x̄)² + n₃(x̄₃ - x̄)²
SSB = 5(16-16.67)² + 5(22-16.67)² + 5(12-16.67)²
SSB = 5(0.45) + 5(28.41) + 5(21.81)
SSB = 2.25 + 142.05 + 109.05 = 253.35
```

*Within-Group Sum of Squares (SSW):*
```
For each group, sum squared deviations from group mean:

Regular:  (15-16)² + (17-16)² + (16-16)² + (18-16)² + (14-16)²
        = 1 + 1 + 0 + 4 + 4 = 10

Espresso: (22-22)² + (21-22)² + (23-22)² + (20-22)² + (24-22)²
        = 0 + 1 + 1 + 4 + 4 = 10

Decaf:    (12-12)² + (13-12)² + (11-12)² + (14-12)² + (10-12)²
        = 0 + 1 + 1 + 4 + 4 = 10

SSW = 10 + 10 + 10 = 30
```

**Step 4: Calculate Degrees of Freedom**
```
df_between = k - 1 = 3 - 1 = 2  (k = number of groups)
df_within  = N - k = 15 - 3 = 12 (N = total observations)
df_total   = N - 1 = 15 - 1 = 14
```

**Step 5: Calculate Mean Squares**
```
MSB = SSB / df_between = 253.35 / 2 = 126.675
MSW = SSW / df_within  = 30 / 12 = 2.5
```

**Step 6: Calculate F-Statistic**
```
F = MSB / MSW = 126.675 / 2.5 = 50.67
```

**Step 7: Find Critical Value or p-value**

Using F-distribution tables or software with df₁=2, df₂=12, α=0.05:
- Critical F-value ≈ 3.89
- Our F = 50.67 >> 3.89
- p-value < 0.001

**Conclusion:** We reject H₀. There is strong evidence that at least one coffee type produces different productivity levels.

### ANOVA Table Format

Results are typically presented in a table:

| Source     | SS     | df | MS      | F     | p-value |
|------------|--------|----|---------|-------|---------|
| Between    | 253.35 | 2  | 126.675 | 50.67 | <0.001  |
| Within     | 30.00  | 12 | 2.50    |       |         |
| **Total**  | 283.35 | 14 |         |       |         |

---

## 4. Mathematical Framework

### The Statistical Model

For one-way ANOVA, each observation can be modeled as:

```
yᵢⱼ = μ + αᵢ + εᵢⱼ
```

Where:
- yᵢⱼ = j-th observation in i-th group
- μ = overall mean (grand mean)
- αᵢ = effect of i-th treatment (deviation from grand mean)
- εᵢⱼ = random error ~ N(0, σ²)

### Partitioning Total Variation

**Total Sum of Squares (SST):**
```
SST = Σᵢ Σⱼ (yᵢⱼ - ȳ)²
```

**Between-Group Sum of Squares (SSB):**
```
SSB = Σᵢ nᵢ(ȳᵢ - ȳ)²
```

**Within-Group Sum of Squares (SSW):**
```
SSW = Σᵢ Σⱼ (yᵢⱼ - ȳᵢ)²
```

**Fundamental Identity:**
```
SST = SSB + SSW
```

### The F-Test Statistic

```
F = MSB / MSW = [SSB/(k-1)] / [SSW/(N-k)]
```

Under H₀, F follows an F-distribution with:
- Numerator df = k - 1
- Denominator df = N - k

### Effect Size: Eta-Squared (η²)

Measures proportion of total variance explained by group differences:

```
η² = SSB / SST
```

**Interpretation:**
- 0.01 = small effect
- 0.06 = medium effect
- 0.14 = large effect

---

## 5. Assumptions & Diagnostics

### The Four Key Assumptions

**1. Independence**
- Observations within and between groups must be independent
- **Check:** Review study design; was randomization used?
- **Violation:** Can lead to inflated Type I error

**2. Normality**
- Data within each group should be approximately normally distributed
- **Check:** 
  - Visual: Q-Q plots, histograms for each group
  - Statistical: Shapiro-Wilk test
- **Robustness:** ANOVA is robust to moderate violations with equal sample sizes
- **Solution:** If violated, consider transformation or non-parametric alternative (Kruskal-Wallis)

**3. Homogeneity of Variance (Homoscedasticity)**
- Variances should be approximately equal across groups
- **Check:**
  - Visual: Boxplots, residual plots
  - Statistical: Levene's test, Bartlett's test
- **Rule of thumb:** Largest variance ≤ 4 × smallest variance
- **Solution:** If violated, use Welch's ANOVA or transform data

**4. Random Sampling**
- Observations should be randomly sampled from populations
- **Check:** Review sampling methodology
- **Implication:** Affects generalizability of results

### Diagnostic Procedures

**Residual Analysis:**

Residuals = Observed values - Group means

```
eᵢⱼ = yᵢⱼ - ȳᵢ
```

**What to Plot:**
1. Residuals vs. Fitted Values (check homoscedasticity)
2. Q-Q plot of residuals (check normality)
3. Residuals vs. Order (check independence)

**Example Interpretation:**

Good residual plot (random scatter):
```
Residuals
    |   ·  ·    ·
    |  ·    · ·  ·
  0 |—·—·——·—·——·—·
    | ·  ·   · ·
    |  ·   ·    ·
    |_____________
      Fitted Values
```

Bad residual plot (funnel shape = heteroscedasticity):
```
Residuals
    |       ·  ·
    |     · ·  · ·
  0 |—·—·———·————·
    |  · ·  ·  ·
    |   ·  ·
    |_____________
      Fitted Values
```

### Dealing with Violations

**Transformations:**
- Log transformation: log(y) - for right-skewed data
- Square root: √y - for count data
- Reciprocal: 1/y - for strong right skew
- Box-Cox: finds optimal transformation

**Alternative Tests:**
- Welch's ANOVA: robust to unequal variances
- Kruskal-Wallis: non-parametric alternative
- Permutation tests: distribution-free approach

---

## 6. Two-Way ANOVA (Intermediate)

### Introduction

Two-Way ANOVA examines the effect of TWO categorical independent variables (factors) on a continuous dependent variable.

**Advantages:**
1. Tests two factors simultaneously
2. Tests for interaction between factors
3. More efficient than separate one-way ANOVAs

### Example: Plant Growth Study

**Factors:**
- Factor A: Fertilizer Type (Organic, Chemical)
- Factor B: Water Amount (Low, Medium, High)

**Dependent Variable:** Plant height (cm)

### The Model

```
yᵢⱼₖ = μ + αᵢ + βⱼ + (αβ)ᵢⱼ + εᵢⱼₖ
```

Where:
- μ = grand mean
- αᵢ = main effect of Factor A (i-th level)
- βⱼ = main effect of Factor B (j-th level)
- (αβ)ᵢⱼ = interaction effect
- εᵢⱼₖ = random error

### Three Hypotheses to Test

**1. Main Effect of Factor A (Fertilizer):**
- H₀: No difference between fertilizer types
- H₁: Fertilizer types differ in effect

**2. Main Effect of Factor B (Water):**
- H₀: No difference between water amounts
- H₁: Water amounts differ in effect

**3. Interaction Effect (A × B):**
- H₀: No interaction between fertilizer and water
- H₁: Effect of one factor depends on level of other factor

### Understanding Interactions

**No Interaction (parallel lines):**
```
Height
  30|        Chemical ————————
    |                      /
  20|        Organic  ————
    |              /
  10|          /
    |______________________
      Low  Medium  High
           Water
```
Effect of water is same for both fertilizers.

**Interaction Present (non-parallel lines):**
```
Height
  30|        Chemical ————
    |                  \
  20|                   \
    |        Organic ————————
  10|
    |______________________
      Low  Medium  High
           Water
```
Chemical works best with low water; Organic with high water.

### Partitioning Variance

```
SST = SSA + SSB + SSAB + SSE
```

Where:
- SST = Total sum of squares
- SSA = Sum of squares for Factor A
- SSB = Sum of squares for Factor B
- SSAB = Sum of squares for interaction
- SSE = Error sum of squares (within-groups)

### Degrees of Freedom

```
df_A = a - 1           (a = levels of Factor A)
df_B = b - 1           (b = levels of Factor B)
df_AB = (a-1)(b-1)
df_E = ab(n-1)         (n = observations per cell)
df_T = abn - 1
```

### ANOVA Table for Two-Way

| Source      | SS   | df           | MS        | F           | p-value |
|-------------|------|--------------|-----------|-------------|---------|
| Factor A    | SSA  | a-1          | MSA       | MSA/MSE     | p_A     |
| Factor B    | SSB  | b-1          | MSB       | MSB/MSE     | p_B     |
| A × B       | SSAB | (a-1)(b-1)   | MSAB      | MSAB/MSE    | p_AB    |
| Error       | SSE  | ab(n-1)      | MSE       |             |         |
| **Total**   | SST  | abn-1        |           |             |         |

### Interpreting Results

**Decision Tree:**

1. **Is interaction significant?**
   - YES → Focus on interaction; main effects may be misleading
   - NO → Interpret main effects

2. **If no interaction:**
   - Examine each main effect separately
   - Use post-hoc tests if factor has >2 levels

3. **If interaction exists:**
   - Describe the interaction pattern
   - Use simple effects analysis (effect of one factor at each level of other)

### Worked Example

**Data: Plant Heights (cm)**

|           | Low Water | Med Water | High Water |
|-----------|-----------|-----------|------------|
| Organic   | 12, 14    | 18, 20    | 22, 24     |
| Chemical  | 20, 22    | 19, 21    | 18, 20     |

**Step 1: Calculate Cell Means**
```
Organic-Low:  13
Organic-Med:  19
Organic-High: 23
Chemical-Low: 21
Chemical-Med: 20
Chemical-High:19
```

**Step 2: Calculate Marginal Means**
```
Organic:  (13+19+23)/3 = 18.33
Chemical: (21+20+19)/3 = 20.00

Low:  (13+21)/2 = 17
Med:  (19+20)/2 = 19.5
High: (23+19)/2 = 21
```

**Step 3: Grand Mean**
```
μ = 19.17
```

**Step 4: Calculate SS**

I'll spare the detailed arithmetic, but the process:
- SSA: Based on fertilizer marginal means vs. grand mean
- SSB: Based on water marginal means vs. grand mean
- SSAB: Based on cell means minus what's explained by main effects
- SSE: Deviations within each cell

**Results:**

| Source      | SS    | df | MS    | F     | p-value |
|-------------|-------|----|-------|-------|---------|
| Fertilizer  | 16.67 | 1  | 16.67 | 3.47  | 0.115   |
| Water       | 80.00 | 2  | 40.00 | 8.33  | 0.019   |
| Fert×Water  | 130.67| 2  | 65.33 | 13.61 | 0.006   |
| Error       | 28.80 | 6  | 4.80  |       |         |
| **Total**   | 256.14| 11 |       |       |         |

**Interpretation:**
- Significant interaction (p = 0.006)
- The effect of water amount depends on fertilizer type
- Organic fertilizer performs better with high water
- Chemical fertilizer performs better with low water

---

## 7. Advanced ANOVA Techniques

### Repeated Measures ANOVA

**When to Use:**
Same subjects measured multiple times (e.g., before, during, after treatment)

**Key Difference:**
Observations are NOT independent; same subjects provide multiple measurements

**Advantages:**
- Controls for individual differences
- More powerful (less error variance)
- Requires fewer subjects

**Additional Assumption:**
- Sphericity: variances of differences between all pairs of conditions are equal
- **Test:** Mauchly's test
- **Correction:** Greenhouse-Geisser or Huynh-Feldt if violated

**Model:**
```
yᵢⱼ = μ + πᵢ + τⱼ + εᵢⱼ
```
Where πᵢ = subject effect

### Mixed ANOVA

Combines between-subjects and within-subjects factors

**Example:**
- Between: Treatment group (Control vs. Experimental)
- Within: Time (Week 1, 2, 3, 4)

**Tests:**
1. Between-subjects main effect
2. Within-subjects main effect
3. Interaction (does treatment affect time course?)

### MANOVA (Multivariate ANOVA)

**When to Use:**
Multiple dependent variables measured simultaneously

**Example:**
Effect of teaching method on math scores, reading scores, and science scores

**Advantages:**
- Controls Type I error across multiple DVs
- Can detect effects that univariate tests miss

**Test Statistics:**
- Wilks' Lambda
- Pillai's Trace
- Hotelling's Trace
- Roy's Largest Root

### ANCOVA (Analysis of Covariance)

**Purpose:**
Control for a continuous covariate while testing group differences

**Example:**
Comparing teaching methods on test scores, controlling for IQ

**Model:**
```
yᵢⱼ = μ + αᵢ + β(xᵢⱼ - x̄) + εᵢⱼ
```
Where xᵢⱼ = covariate value

**Assumptions (additional):**
- Linearity: DV and covariate are linearly related
- Homogeneity of regression slopes: relationship between DV and covariate is same across groups

**Benefits:**
- Reduces error variance
- Increases statistical power
- Controls for confounding variables

### Factorial ANOVA (3+ Factors)

**Example: 2×3×2 Design**
- Factor A: 2 levels
- Factor B: 3 levels
- Factor C: 2 levels

**Number of Effects:**
- 3 main effects
- 3 two-way interactions (A×B, A×C, B×C)
- 1 three-way interaction (A×B×C)

**Complexity:**
Interpreting three-way interactions requires careful attention to simple-simple effects

---

## 8. Post-Hoc Tests

### Why Post-Hoc Tests?

ANOVA only tells us that "at least one group differs." It doesn't tell us WHICH groups differ.

**The Multiple Comparison Problem:**
If you have 5 groups and use t-tests for all pairwise comparisons:
- Number of comparisons = C(5,2) = 10
- Overall error rate ≈ 1 - (0.95)¹⁰ ≈ 40%!

Post-hoc tests control this inflation of Type I error.

### Common Post-Hoc Tests

**1. Tukey's HSD (Honestly Significant Difference)**
- **Use:** All pairwise comparisons
- **Best for:** Equal sample sizes
- **Control:** Familywise error rate
- **Power:** Moderate

```
HSD = q × √(MSE/n)
```

**2. Bonferroni Correction**
- **Use:** Limited planned comparisons
- **Method:** Divide α by number of comparisons
- **Conservative:** Very strict, reduces power
- **Best for:** Few comparisons (≤5)

**3. Scheffé's Test**
- **Use:** Any/all possible comparisons (even complex contrasts)
- **Most conservative:** Hardest to find significance
- **Best for:** Post-hoc exploration of complex comparisons

**4. Dunnett's Test**
- **Use:** Comparing all groups to a control
- **More powerful:** Than Tukey when you have a control
- **Common in:** Clinical trials, biology experiments

**5. Fisher's LSD (Least Significant Difference)**
- **Use:** Protected only if overall F is significant
- **Least conservative:** Most powerful
- **Risk:** Higher Type I error

### Choosing the Right Test

| Situation | Recommended Test |
|-----------|------------------|
| All pairwise, equal n | Tukey HSD |
| All pairwise, unequal n | Games-Howell |
| Few planned comparisons | Bonferroni |
| Compare to control | Dunnett |
| Complex contrasts | Scheffé |
| Exploratory, maximum power | Fisher LSD |

### Example: Tukey's HSD

Back to our coffee example (Regular=16, Espresso=22, Decaf=12):

```
MSE = 2.5, n = 5, k = 3
q₀.₀₅,₃,₁₂ ≈ 3.77 (from q-table)

HSD = 3.77 × √(2.5/5) = 2.67
```

**Pairwise Differences:**
- |Espresso - Regular| = |22-16| = 6 > 2.67 ✓ Significant
- |Espresso - Decaf| = |22-12| = 10 > 2.67 ✓ Significant
- |Regular - Decaf| = |16-12| = 4 > 2.67 ✓ Significant

**Conclusion:** All three coffees produce significantly different productivity levels.

### Planned Contrasts (Alternative Approach)

If you have specific hypotheses BEFORE seeing data:

**Example Hypotheses:**
1. Caffeine (Regular + Espresso) vs. No Caffeine (Decaf)
2. Regular vs. Espresso

**Contrast 1:** 
```
L₁ = (1)μ_regular + (1)μ_espresso + (-2)μ_decaf
   = 16 + 22 - 2(12) = 14
```

Test using: t = L / SE(L)

**Advantages:**
- More powerful than post-hoc tests
- Can test specific scientific questions
- Fewer comparisons needed

---

## 9. Practical Examples with Solutions

### Example 1: One-Way ANOVA - Diet Study

**Research Question:** Do three diets lead to different weight loss?

**Data (weight loss in kg):**
- Diet A: [5, 6, 7, 5, 6]
- Diet B: [3, 4, 3, 5, 4]
- Diet C: [8, 9, 7, 8, 9]

**Solution:**

Step 1: State hypotheses
- H₀: μ_A = μ_B = μ_C
- H₁: At least one mean differs

Step 2: Calculate means
- x̄_A = 5.8, x̄_B = 3.8, x̄_C = 8.2
- Grand mean = 5.93

Step 3: Calculate SS
- SSB = 5(5.8-5.93)² + 5(3.8-5.93)² + 5(8.2-5.93)² = 48.13
- SSW = 4 + 2 + 4 = 10
- SST = 58.13

Step 4: Create ANOVA table

| Source  | SS    | df | MS    | F     |
|---------|-------|----|-------|-------|
| Between | 48.13 | 2  | 24.07 | 28.88 |
| Within  | 10.00 | 12 | 0.83  |       |
| Total   | 58.13 | 14 |       |       |

Step 5: Find p-value
- F(2,12) = 28.88, p < 0.001

Step 6: Conclusion
Reject H₀. There are significant differences in weight loss among the three diets.

Step 7: Post-hoc (Tukey's HSD)
```
HSD = 3.77 × √(0.83/5) = 1.54
```
- |A-B| = 2.0 > 1.54 ✓
- |A-C| = 2.4 > 1.54 ✓
- |B-C| = 4.4 > 1.54 ✓

All diets differ significantly. Diet C most effective, Diet B least effective.

---

### Example 2: Two-Way ANOVA - Memory Study

**Research Question:** Does age and sleep affect memory scores?

**Factors:**
- Age: Young (20-30), Old (60-70)
- Sleep: Deprived, Normal

**Data (memory test scores out of 20):**

|           | Deprived  | Normal    |
|-----------|-----------|-----------|
| Young     | 12, 13, 14| 16, 17, 18|
| Old       | 8, 9, 10  | 10, 11, 12|

**Solution:**

Cell means:
- Young-Deprived: 13
- Young-Normal: 17
- Old-Deprived: 9
- Old-Normal: 11

Marginal means:
- Young: 15
- Old: 10
- Deprived: 11
- Normal: 14
- Grand: 12.5

ANOVA Table:

| Source      | SS    | df | MS   | F     | p-value |
|-------------|-------|----|------|-------|---------|
| Age         | 75.00 | 1  | 75.00| 90.00 | <0.001  |
| Sleep       | 27.00 | 1  | 27.00| 32.40 | <0.001  |
| Age×Sleep   | 3.00  | 1  | 3.00 | 3.60  | 0.092   |
| Error       | 6.67  | 8  | 0.83 |       |         |
| Total       | 111.67| 11 |      |       |         |

**Interpretation:**
- Significant main effect of Age: Young perform better (p < 0.001)
- Significant main effect of Sleep: Normal sleep leads to better performance (p < 0.001)
- No significant interaction (p = 0.092): The benefit of normal sleep is similar for both age groups

---

### Example 3: Repeated Measures - Drug Trial

**Research Question:** Does blood pressure change over time with medication?

**Data: Blood pressure measurements (mmHg)**

| Patient | Baseline | Week 2 | Week 4 | Week 6 |
|---------|----------|--------|--------|--------|
| 1       | 150      | 145    | 138    | 130    |
| 2       | 155      | 148    | 142    | 135    |
| 3       | 148      | 143    | 140    | 132    |
| 4       | 160      | 152    | 145    | 138    |
| 5       | 152      | 147    | 141    | 134    |

**Analysis:**

This requires repeated measures ANOVA because same patients measured at 4 time points.

**Results (simplified):**

| Source           | SS      | df | MS     | F     | p-value |
|------------------|---------|-------|--------|-------|---------|
| Time             | 1020.00 | 3  | 340.00 | 51.00 | <0.001  |
| Subject          | 366.67  | 4  | 91.67  |       |         |
| Error            | 80.00   | 12 | 6.67   |       |         |

**Interpretation:**
- Highly significant time effect (p < 0.001)
- Blood pressure decreases significantly over 6 weeks
- Post-hoc tests show each time point differs from baseline

**Effect size:**
η² = 1020/(1020+366.67+80) = 0.70 (large effect)

---

## 10. Common Pitfalls & Best Practices

### Common Mistakes

**1. Using ANOVA when you should use t-test**
- If only 2 groups, use t-test (though ANOVA gives same result)
- ANOVA is for 3+ groups

**2. Ignoring assumptions**
- Always check normality, homogeneity of variance, independence
- Don't just run the test blindly

**3. Not checking for outliers**
- One extreme value can drastically affect results
- Use boxplots, check residuals

**4. Treating ordinal data as continuous**
- Likert scales (1-5 ratings) are technically ordinal
- Consider non-parametric alternatives for ordinal data

**5. Over-interpreting non-significant results**
- Failing to reject H₀ doesn't prove groups are equal
- Could be due to low power (small sample size)

**6. Running post-hoc tests when F is not significant**
- Some tests (Fisher LSD) require significant F first
- Others don't, but interpretation is questionable

**7. Confusing interaction with main effects**
- When interaction is significant, main effects can be misleading
- Always interpret interaction first

**8. Not reporting effect sizes**
- p-value only tells if effect is significant
- Effect size tells if effect is meaningful
- Always report η², ω², or Cohen's f

**9. Fishing for significance**
- Running many post-hoc tests without adjustment
- Trying different transformations until p < 0.05

**10. Assuming equal importance of all factors**
- In two-way ANOVA, one factor may be much more important
- Report and discuss effect sizes

### Best Practices

**1. Plan your analysis before collecting data**
- Determine sample size needed (power analysis)
- Decide on planned comparisons
- Set significance level in advance

**2. Always visualize your data first**
- Boxplots for each group
- Interaction plots for two-way ANOVA
- Check for obvious patterns, outliers

**3. Check assumptions systematically**
- Test normality (Shapiro-Wilk)
- Test homogeneity (Levene's test)
- Plot residuals
- Document what you find

**4. Report comprehensively**
- Descriptive statistics (means, SDs)
- ANOVA table
- Effect sizes
- Post-hoc test results
- Confidence intervals

**5. Use appropriate post-hoc tests**
- Match test to research question
- Don't just default to Tukey
- Consider power vs. Type I error trade-off

**6. Interpret in context**
- Statistical significance ≠ practical significance
- Consider the research domain
- Discuss limitations

**7. Use software but understand it**
- Learn to verify calculations by hand (at least once)
- Don't blindly trust output
- Understand what each value means

**8. Consider alternatives when assumptions fail**
- Transformation (log, sqrt)
- Welch's ANOVA
- Non-parametric tests (Kruskal-Wallis)
- Bootstrap methods

---

## 11. Practice Problems

### Problem 1: Basic One-Way ANOVA

Four brands of batteries are tested for lifetime (hours):
- Brand A: [100, 105, 98, 102]
- Brand B: [88, 92, 90, 85]
- Brand C: [110, 115, 112, 118]
- Brand D: [95, 98, 100, 97]

**Tasks:**
a) Conduct one-way ANOVA (α = 0.05)
b) If significant, perform Tukey's HSD
c) Calculate η²
d) Interpret results

**Hints:**
- Start by calculating group means
- Check if variances are similar across groups
- Remember: SST = SSB + SSW

---

### Problem 2: Two-Way ANOVA

A study examines teaching method (Lecture, Discussion) and class size (Small, Large) on test scores:

|            | Small Class | Large Class |
|------------|-------------|-------------|
| Lecture    | 75, 78, 80  | 70, 72, 68  |
| Discussion | 85, 88, 86  | 82, 80, 84  |

**Tasks:**
a) Set up the two-way ANOVA
b) Test for main effects and interaction
c) Create an interaction plot
d) Interpret the results

**Hints:**
- Calculate cell means first
- Check if lines in interaction plot are parallel
- If interaction exists, focus on simple effects

---

### Problem 3: Assumption Checking

Given the following residuals from an ANOVA:
Group A: [-5, 2, 3, -2, 1]
Group B: [-1, 0, 2, -1, 0]
Group C: [-10, -15, 12, 8, 5]

**Tasks:**
a) Which assumption might be violated?
b) What diagnostic would you use?
c) What remedial action would you take?

**Hints:**
- Look at the spread of residuals
- Calculate variance for each group
- Consider Levene's test

---

### Problem 4: Post-Hoc Analysis

An ANOVA comparing 5 fertilizers yielded F(4, 25) = 8.45, p = 0.001, MSE = 4.5.
Group means: A=20, B=22, C=28, D=21, E=30 (n=6 each)

**Tasks:**
a) Calculate Tukey's HSD
b) Which pairs differ significantly?
c) Calculate Bonferroni-adjusted p-value for 10 comparisons
d) Which approach would you recommend and why?

**Hints:**
- Look up q-value for Tukey (k=5, df=25)
- Bonferroni: α_new = α / number of comparisons
- Consider Type I vs Type II error trade-off

---

### Problem 5: Design Choice

For each scenario, choose the appropriate ANOVA design:

a) Comparing productivity of employees in 3 different offices
b) Testing effects of temperature (20°C, 25°C, 30°C) and humidity (40%, 60%) on plant growth
c) Measuring depression scores before, during, and after therapy in same patients
d) Comparing reaction times across 4 age groups while controlling for IQ
e) Testing whether diet and exercise program affect weight, cholesterol, and blood pressure

**Options:**
1. One-way ANOVA
2. Two-way ANOVA
3. Repeated measures ANOVA
4. ANCOVA
5. MANOVA

---

## 12. Solutions to Practice Problems

### Solution to Problem 1

**a) One-Way ANOVA:**

Group means:
- A: 101.25, B: 88.75, C: 113.75, D: 97.5
- Grand mean: 100.31

Calculations:
- SSB = 4[(101.25-100.31)² + (88.75-100.31)² + (113.75-100.31)² + (97.5-100.31)²]
- SSB = 4[0.88 + 133.56 + 180.56 + 7.90] = 1291.60

- SSW = Σ(deviations within each group)²
- SSW = 28 + 26 + 58 + 16 = 128

ANOVA Table:
| Source  | SS      | df | MS     | F     | p-value |
|---------|---------|---|--------|-------|---------|
| Between | 1291.60 | 3  | 430.53 | 40.36 | <0.001  |
| Within  | 128.00  | 12 | 10.67  |       |         |
| Total   | 1419.60 | 15 |        |       |         |

F(3,12) = 40.36, p < 0.001 → Reject H₀

**b) Tukey's HSD:**
```
q₀.₀₅,₄,₁₂ ≈ 4.20
HSD = 4.20 × √(10.67/4) = 6.86
```

Pairwise comparisons:
- |A-B| = 12.5 > 6.86 ✓
- |A-C| = 12.5 > 6.86 ✓
- |A-D| = 3.75 < 6.86 ✗
- |B-C| = 25.0 > 6.86 ✓
- |B-D| = 8.75 > 6.86 ✓
- |C-D| = 16.25 > 6.86 ✓

**c) Effect size:**
η² = 1291.60 / 1419.60 = 0.91 (very large effect)

**d) Interpretation:**
Brand C has significantly longest lifetime, Brand B shortest. Brands A and D don't differ significantly from each other. The battery brand explains 91% of variance in lifetime.

---

### Solution to Problem 2

**a) Cell and Marginal Means:**

Cell means:
- Lecture-Small: 77.67
- Lecture-Large: 70.00
- Discussion-Small: 86.33
- Discussion-Large: 82.00

Marginal means:
- Lecture: 73.83
- Discussion: 84.17
- Small: 82.00
- Large: 76.00
- Grand: 79.00

**b) ANOVA Table (abbreviated):**

| Source      | SS     | df | MS    | F     | p-value |
|-------------|--------|---|-------|-------|---------|
| Method      | 320.67 | 1  | 320.67| 44.84 | <0.001  |
| Size        | 108.00 | 1  | 108.00| 15.10 | 0.004   |
| Method×Size | 2.67   | 1  | 2.67  | 0.37  | 0.556   |
| Error       | 57.33  | 8  | 7.17  |       |         |

**c) Interaction Plot:**
```
Score
  90|        Discussion ————————
    |                        
  80|                         ————
    |
  75|        Lecture   ————
    |                     ————
  70|
    |________________________
      Small          Large
         Class Size
```
Lines are roughly parallel → minimal interaction

**d) Interpretation:**
- Significant main effect of teaching method: Discussion superior to Lecture (p < 0.001)
- Significant main effect of class size: Small classes perform better (p = 0.004)
- No significant interaction (p = 0.556): Both methods benefit similarly from small classes
- Recommendation: Use discussion method in small classes for best results

---

### Solution to Problem 3

**a) Violated Assumption:**
Homogeneity of variance appears violated. Group C has much larger spread than A and B.

**b) Diagnostics:**

Variances:
- Group A: s² = 10.7
- Group B: s² = 1.3
- Group C: s² = 132.0

Ratio: 132.0 / 1.3 = 101.5 >> 4 (rule of thumb)

**Levene's Test:**
Would likely show p < 0.05, confirming heterogeneity

**c) Remedial Actions:**

1. **Transform data:** Try log transformation to stabilize variance
2. **Use Welch's ANOVA:** Doesn't assume equal variances
3. **Use non-parametric test:** Kruskal-Wallis test
4. **Investigate Group C:** Check for outliers or data entry errors

**Recommended:** Start by checking Group C for errors, then use Welch's ANOVA if heterogeneity confirmed.

---

### Solution to Problem 4

**a) Tukey's HSD:**
```
q₀.₀₅,₅,₂₅ ≈ 4.15
HSD = 4.15 × √(4.5/6) = 3.60
```

**b) Significant Pairs:**

All differences:
- |A-B| = 2 < 3.60 ✗
- |A-C| = 8 > 3.60 ✓
- |A-D| = 1 < 3.60 ✗
- |A-E| = 10 > 3.60 ✓
- |B-C| = 6 > 3.60 ✓
- |B-D| = 1 < 3.60 ✗
- |B-E| = 8 > 3.60 ✓
- |C-D| = 7 > 3.60 ✓
- |C-E| = 2 < 3.60 ✗
- |D-E| = 9 > 3.60 ✓

7 out of 10 comparisons significant

**c) Bonferroni:**
α_adjusted = 0.05 / 10 = 0.005

This is much more stringent; fewer comparisons would be significant.

**d) Recommendation:**

Use **Tukey's HSD** because:
- All pairwise comparisons are of interest
- Tukey controls familywise error rate appropriately
- More powerful than Bonferroni for this many comparisons
- Standard approach for this scenario

Bonferroni would be too conservative here (10 comparisons), risking Type II errors.

---

### Solution to Problem 5

**a) 1 - One-way ANOVA**
Single factor (office location), 3 levels

**b) 2 - Two-way ANOVA**
Two factors (temperature and humidity), testing main effects and interaction

**c) 3 - Repeated measures ANOVA**
Same subjects measured at 3 time points (before, during, after)

**d) 4 - ANCOVA**
One factor (age group), controlling for continuous covariate (IQ)

**e) 5 - MANOVA**
One factor (program), multiple dependent variables (weight, cholesterol, BP)

---

## 13. Quick Reference Guide

### When to Use Each Type

| ANOVA Type | Independent Variables | Dependent Variables | Use When |
|------------|----------------------|---------------------|----------|
| One-Way | 1 categorical (3+ levels) | 1 continuous | Comparing means across 3+ independent groups |
| Two-Way | 2 categorical | 1 continuous | Testing two factors and their interaction |
| Repeated Measures | 1 categorical (within-subjects) | 1 continuous | Same subjects measured multiple times |
| Mixed | 1 between + 1 within | 1 continuous | Combining independent groups and repeated measures |
| MANOVA | 1+ categorical | 2+ continuous | Multiple outcomes measured simultaneously |
| ANCOVA | 1 categorical + 1 continuous | 1 continuous | Controlling for a covariate |

### Critical Values Quick Reference

**F-distribution (α = 0.05):**

| df₁ | df₂=10 | df₂=20 | df₂=30 | df₂=∞ |
|-----|--------|--------|--------|-------|
| 1   | 4.96   | 4.35   | 4.17   | 3.84  |
| 2   | 4.10   | 3.49   | 3.32   | 3.00  |
| 3   | 3.71   | 3.10   | 2.92   | 2.60  |
| 4   | 3.48   | 2.87   | 2.69   | 2.37  |
| 5   | 3.33   | 2.71   | 2.53   | 2.21  |

### Effect Size Interpretation

**η² (Eta-squared):**
- 0.01 = Small effect
- 0.06 = Medium effect
- 0.14 = Large effect

**Cohen's f:**
- 0.10 = Small effect
- 0.25 = Medium effect
- 0.40 = Large effect

### Formulas Cheat Sheet

**One-Way ANOVA:**
```
SST = Σᵢ Σⱼ (yᵢⱼ - ȳ)²
SSB = Σᵢ nᵢ(ȳᵢ - ȳ)²
SSW = SST - SSB
F = MSB / MSW = [SSB/(k-1)] / [SSW/(N-k)]
```

**Effect Size:**
```
η² = SSB / SST
ω² = (SSB - (k-1)MSW) / (SST + MSW)
```

**Tukey HSD:**
```
HSD = q_α × √(MSW/n)
```

---

## Conclusion

ANOVA is a powerful tool for comparing means across multiple groups while controlling Type I error. Understanding when to use each type, checking assumptions, and properly interpreting results are crucial for valid statistical inference.

**Key Takeaways:**
1. Always check assumptions before running ANOVA
2. Visualize data first
3. Report effect sizes, not just p-values
4. Use appropriate post-hoc tests
5. Interpret interactions before main effects
6. Consider the research context in interpretation

**Further Learning:**
- Advanced topics: Mixed models, hierarchical ANOVA
- Software tutorials: R, Python, SPSS, SAS
- Real datasets for practice
- Bayesian alternatives to classical ANOVA

---

*End of Teaching Material*
