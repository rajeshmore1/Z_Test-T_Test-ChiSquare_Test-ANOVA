# Complete Guide to Chi-Square Test
## From Basic to Advanced

---

## Table of Contents
1. Introduction and Intuition
2. Mathematical Foundation
3. Types of Chi-Square Tests
4. Step-by-Step Methodology
5. Detailed Examples with Solutions
6. Assumptions and Conditions
7. Advanced Applications
8. Common Mistakes and How to Avoid Them
9. Practice Problems

---

## 1. Introduction and Intuition

### What is the Chi-Square Test?

The Chi-Square test is like a detective that investigates whether what we observe in reality matches what we expect to happen by chance.

**Real-Life Analogy:**
Imagine you flip a coin 100 times. You expect roughly 50 heads and 50 tails. But you get 60 heads and 40 tails. The Chi-Square test answers: "Is this difference just random luck, or is the coin actually biased?"

### When Do We Use Chi-Square Tests?

**Use Chi-Square when:**
- Your data is **categorical** (categories, not measurements)
- You want to see if observed frequencies match expected frequencies
- You want to check if two categorical variables are related

**Examples:**
- Are customer preferences evenly distributed across product categories?
- Is there a relationship between gender and voting preference?
- Do dice rolls follow a fair distribution?

---

## 2. Mathematical Foundation

### The Chi-Square Statistic Formula

```
χ² = Σ [(Observed - Expected)²] / Expected
```

**Breaking it down:**
- **Observed (O):** What you actually counted in your data
- **Expected (E):** What you would expect if there was no effect/relationship
- **Σ (Sigma):** Sum across all categories

### Why This Formula Makes Sense

1. **(O - E):** Measures the difference between reality and expectation
2. **(O - E)²:** Squaring makes all differences positive and emphasizes larger differences
3. **÷ E:** Divides by expected to make differences relative (10 off from 100 is different than 10 off from 20)
4. **Σ:** Adds up all these standardized differences

### The Chi-Square Distribution

The test statistic follows a **Chi-Square distribution** with specific degrees of freedom (df).

**Degrees of Freedom:**
- For Goodness of Fit: df = (number of categories - 1)
- For Test of Independence: df = (rows - 1) × (columns - 1)

---

## 3. Types of Chi-Square Tests

### Type 1: Chi-Square Goodness of Fit Test

**Purpose:** Tests if observed frequencies match an expected distribution

**Example Question:** Does a dice show each face with equal probability?

### Type 2: Chi-Square Test of Independence

**Purpose:** Tests if two categorical variables are related/associated

**Example Question:** Is there a relationship between smoking status and lung disease?

### Type 3: Chi-Square Test of Homogeneity

**Purpose:** Tests if different populations have the same distribution

**Example Question:** Do different age groups prefer the same political parties?

---

## 4. Step-by-Step Methodology

### Universal Steps for All Chi-Square Tests

**Step 1: State the Hypotheses**
- H₀ (Null Hypothesis): No difference/No relationship
- H₁ (Alternative Hypothesis): There is a difference/relationship

**Step 2: Choose Significance Level**
- Typically α = 0.05 (5% significance level)

**Step 3: Calculate Expected Frequencies**
- Method varies by test type (see examples below)

**Step 4: Compute Chi-Square Statistic**
- Use formula: χ² = Σ[(O - E)²/E]

**Step 5: Find Degrees of Freedom**
- Depends on test type

**Step 6: Determine Critical Value or p-value**
- Compare with chi-square distribution table

**Step 7: Make Decision**
- Reject H₀ if χ² > critical value (or p-value < α)
- Fail to reject H₀ otherwise

**Step 8: Interpret Results**
- What does this mean in context?

---

## 5. Detailed Examples with Solutions

---

### EXAMPLE 1: Chi-Square Goodness of Fit Test (Basic)

**Scenario:** A candy factory claims their candy bags contain equal proportions of 5 colors: Red, Blue, Green, Yellow, Orange. You open a bag of 200 candies and count:

| Color  | Observed |
|--------|----------|
| Red    | 45       |
| Blue   | 38       |
| Green  | 42       |
| Yellow | 35       |
| Orange | 40       |

**Question:** Does the data support the factory's claim?

---

**SOLUTION:**

**Step 1: State Hypotheses**
- H₀: All colors are equally distributed (20% each)
- H₁: Colors are not equally distributed

**Step 2: Significance Level**
- α = 0.05

**Step 3: Calculate Expected Frequencies**

If colors are equal, each should be 200/5 = 40 candies

| Color  | Observed (O) | Expected (E) |
|--------|--------------|--------------|
| Red    | 45           | 40           |
| Blue   | 38           | 40           |
| Green  | 42           | 40           |
| Yellow | 35           | 40           |
| Orange | 40           | 40           |

**Step 4: Calculate Chi-Square Statistic**

```
χ² = Σ[(O - E)²/E]

Red:    (45 - 40)² / 40 = 25/40 = 0.625
Blue:   (38 - 40)² / 40 = 4/40  = 0.100
Green:  (42 - 40)² / 40 = 4/40  = 0.100
Yellow: (35 - 40)² / 40 = 25/40 = 0.625
Orange: (40 - 40)² / 40 = 0/40  = 0.000

χ² = 0.625 + 0.100 + 0.100 + 0.625 + 0.000 = 1.45
```

**Step 5: Degrees of Freedom**
```
df = number of categories - 1 = 5 - 1 = 4
```

**Step 6: Critical Value**

From Chi-Square table at α = 0.05 and df = 4:
Critical value = 9.488

**Step 7: Decision**

χ² = 1.45 < 9.488

**Fail to reject H₀**

**Step 8: Interpretation**

There is **insufficient evidence** to conclude that the color distribution differs from equal proportions. The observed differences appear to be due to random variation. The factory's claim is supported by the data.

---

### EXAMPLE 2: Chi-Square Goodness of Fit Test (Intermediate)

**Scenario:** A genetics study predicts that flower colors should appear in the ratio 9:3:3:1 (Red:Pink:White:Yellow) based on Mendelian inheritance. You observe 300 flowers:

| Color  | Observed |
|--------|----------|
| Red    | 180      |
| Pink   | 55       |
| White  | 50       |
| Yellow | 15       |

**Question:** Do the results fit the genetic model?

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: Flowers follow 9:3:3:1 ratio
- H₁: Flowers do not follow 9:3:3:1 ratio

**Step 2: Significance Level**
- α = 0.05

**Step 3: Calculate Expected Frequencies**

Total ratio parts = 9 + 3 + 3 + 1 = 16
Total flowers = 300

| Color  | Ratio | Expected (E) | Observed (O) |
|--------|-------|--------------|--------------|
| Red    | 9/16  | 300×(9/16) = 168.75 | 180 |
| Pink   | 3/16  | 300×(3/16) = 56.25  | 55  |
| White  | 3/16  | 300×(3/16) = 56.25  | 50  |
| Yellow | 1/16  | 300×(1/16) = 18.75  | 15  |

**Step 4: Calculate Chi-Square**

```
Red:    (180 - 168.75)² / 168.75 = 126.5625/168.75 = 0.750
Pink:   (55 - 56.25)² / 56.25 = 1.5625/56.25 = 0.028
White:  (50 - 56.25)² / 56.25 = 39.0625/56.25 = 0.694
Yellow: (15 - 18.75)² / 18.75 = 14.0625/18.75 = 0.750

χ² = 0.750 + 0.028 + 0.694 + 0.750 = 2.222
```

**Step 5: Degrees of Freedom**
```
df = 4 - 1 = 3
```

**Step 6: Critical Value**
At α = 0.05, df = 3: Critical value = 7.815

**Step 7: Decision**
χ² = 2.222 < 7.815
**Fail to reject H₀**

**Step 8: Interpretation**
The observed flower colors are **consistent** with the predicted 9:3:3:1 genetic ratio. The genetic model is supported.

---

### EXAMPLE 3: Chi-Square Test of Independence (Basic)

**Scenario:** A researcher wants to know if there's a relationship between exercise habits and stress levels. Survey results from 200 people:

|              | Low Stress | High Stress | Total |
|--------------|------------|-------------|-------|
| Regular Exercise | 70     | 30          | 100   |
| No Exercise  | 40         | 60          | 100   |
| **Total**    | **110**    | **90**      | **200** |

**Question:** Is there a relationship between exercise and stress?

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: Exercise and stress level are independent (no relationship)
- H₁: Exercise and stress level are dependent (relationship exists)

**Step 2: Significance Level**
- α = 0.05

**Step 3: Calculate Expected Frequencies**

**Formula:** Expected = (Row Total × Column Total) / Grand Total

```
Expected for Regular Exercise & Low Stress:
E = (100 × 110) / 200 = 55

Expected for Regular Exercise & High Stress:
E = (100 × 90) / 200 = 45

Expected for No Exercise & Low Stress:
E = (100 × 110) / 200 = 55

Expected for No Exercise & High Stress:
E = (100 × 90) / 200 = 45
```

**Expected Frequencies Table:**

|              | Low Stress | High Stress |
|--------------|------------|-------------|
| Regular Exercise | 55     | 45          |
| No Exercise  | 55         | 45          |

**Step 4: Calculate Chi-Square**

```
χ² = Σ[(O - E)²/E]

Regular Exercise, Low Stress:  (70 - 55)²/55 = 225/55 = 4.091
Regular Exercise, High Stress: (30 - 45)²/45 = 225/45 = 5.000
No Exercise, Low Stress:       (40 - 55)²/55 = 225/55 = 4.091
No Exercise, High Stress:      (60 - 45)²/45 = 225/45 = 5.000

χ² = 4.091 + 5.000 + 4.091 + 5.000 = 18.182
```

**Step 5: Degrees of Freedom**
```
df = (rows - 1) × (columns - 1) = (2 - 1) × (2 - 1) = 1
```

**Step 6: Critical Value**
At α = 0.05, df = 1: Critical value = 3.841

**Step 7: Decision**
χ² = 18.182 > 3.841
**Reject H₀**

**Step 8: Interpretation**
There is **strong evidence** of a relationship between exercise habits and stress levels. People who exercise regularly tend to have lower stress levels compared to those who don't exercise.

---

### EXAMPLE 4: Chi-Square Test of Independence (Advanced)

**Scenario:** A marketing team analyzes customer purchase patterns across age groups and product categories:

|           | Electronics | Clothing | Home Goods | Total |
|-----------|-------------|----------|------------|-------|
| 18-30     | 45          | 60       | 25         | 130   |
| 31-50     | 55          | 40       | 45         | 140   |
| 51+       | 30          | 50       | 50         | 130   |
| **Total** | **130**     | **150**  | **120**    | **400** |

**Question:** Is product preference independent of age group?

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: Product preference is independent of age group
- H₁: Product preference depends on age group

**Step 2: Significance Level**
- α = 0.05

**Step 3: Calculate Expected Frequencies**

**Formula:** E = (Row Total × Column Total) / Grand Total

```
18-30, Electronics:  (130 × 130) / 400 = 42.25
18-30, Clothing:     (130 × 150) / 400 = 48.75
18-30, Home Goods:   (130 × 120) / 400 = 39.00

31-50, Electronics:  (140 × 130) / 400 = 45.50
31-50, Clothing:     (140 × 150) / 400 = 52.50
31-50, Home Goods:   (140 × 120) / 400 = 42.00

51+, Electronics:    (130 × 130) / 400 = 42.25
51+, Clothing:       (130 × 150) / 400 = 48.75
51+, Home Goods:     (130 × 120) / 400 = 39.00
```

**Expected Frequencies Table:**

|       | Electronics | Clothing | Home Goods |
|-------|-------------|----------|------------|
| 18-30 | 42.25       | 48.75    | 39.00      |
| 31-50 | 45.50       | 52.50    | 42.00      |
| 51+   | 42.25       | 48.75    | 39.00      |

**Step 4: Calculate Chi-Square**

```
χ² = Σ[(O - E)²/E]

18-30, Electronics:  (45 - 42.25)²/42.25 = 7.5625/42.25 = 0.179
18-30, Clothing:     (60 - 48.75)²/48.75 = 126.5625/48.75 = 2.596
18-30, Home Goods:   (25 - 39.00)²/39.00 = 196.00/39.00 = 5.026

31-50, Electronics:  (55 - 45.50)²/45.50 = 90.25/45.50 = 1.984
31-50, Clothing:     (40 - 52.50)²/52.50 = 156.25/52.50 = 2.976
31-50, Home Goods:   (45 - 42.00)²/42.00 = 9.00/42.00 = 0.214

51+, Electronics:    (30 - 42.25)²/42.25 = 150.0625/42.25 = 3.552
51+, Clothing:       (50 - 48.75)²/48.75 = 1.5625/48.75 = 0.032
51+, Home Goods:     (50 - 39.00)²/39.00 = 121.00/39.00 = 3.103

χ² = 0.179 + 2.596 + 5.026 + 1.984 + 2.976 + 0.214 
     + 3.552 + 0.032 + 3.103
     
χ² = 19.662
```

**Step 5: Degrees of Freedom**
```
df = (rows - 1) × (columns - 1) = (3 - 1) × (3 - 1) = 2 × 2 = 4
```

**Step 6: Critical Value**
At α = 0.05, df = 4: Critical value = 9.488

**Step 7: Decision**
χ² = 19.662 > 9.488
**Reject H₀**

**Step 8: Interpretation**
There is **significant evidence** that product preference depends on age group. Looking at the data:
- Younger customers (18-30) prefer Clothing more than expected
- Middle-aged customers (31-50) prefer Electronics more than expected
- Older customers (51+) prefer Home Goods more than expected

This suggests the marketing team should tailor their strategies to age-specific preferences.

---

### EXAMPLE 5: Multinomial Goodness of Fit (Advanced)

**Scenario:** A website tracks visitor traffic by day of week. The manager believes traffic should be distributed as: Monday (10%), Tuesday (10%), Wednesday (15%), Thursday (15%), Friday (20%), Saturday (20%), Sunday (10%). 

Last month's data (1000 visitors):

| Day       | Visitors |
|-----------|----------|
| Monday    | 95       |
| Tuesday   | 105      |
| Wednesday | 140      |
| Thursday  | 160      |
| Friday    | 210      |
| Saturday  | 195      |
| Sunday    | 95       |

**Question:** Does the traffic follow the expected distribution?

---

**SOLUTION:**

**Step 1: Hypotheses**
- H₀: Traffic follows the specified distribution
- H₁: Traffic does not follow the specified distribution

**Step 2: Significance Level**
- α = 0.05

**Step 3: Calculate Expected Frequencies**

| Day       | Expected % | Expected Count (E) | Observed (O) |
|-----------|------------|-------------------|--------------|
| Monday    | 10%        | 1000 × 0.10 = 100 | 95           |
| Tuesday   | 10%        | 1000 × 0.10 = 100 | 105          |
| Wednesday | 15%        | 1000 × 0.15 = 150 | 140          |
| Thursday  | 15%        | 1000 × 0.15 = 150 | 160          |
| Friday    | 20%        | 1000 × 0.20 = 200 | 210          |
| Saturday  | 20%        | 1000 × 0.20 = 200 | 195          |
| Sunday    | 10%        | 1000 × 0.10 = 100 | 95           |

**Step 4: Calculate Chi-Square**

```
Monday:    (95 - 100)²/100 = 25/100 = 0.250
Tuesday:   (105 - 100)²/100 = 25/100 = 0.250
Wednesday: (140 - 150)²/150 = 100/150 = 0.667
Thursday:  (160 - 150)²/150 = 100/150 = 0.667
Friday:    (210 - 200)²/200 = 100/200 = 0.500
Saturday:  (195 - 200)²/200 = 25/200 = 0.125
Sunday:    (95 - 100)²/100 = 25/100 = 0.250

χ² = 0.250 + 0.250 + 0.667 + 0.667 + 0.500 + 0.125 + 0.250 = 2.709
```

**Step 5: Degrees of Freedom**
```
df = 7 - 1 = 6
```

**Step 6: Critical Value**
At α = 0.05, df = 6: Critical value = 12.592

**Step 7: Decision**
χ² = 2.709 < 12.592
**Fail to reject H₀**

**Step 8: Interpretation**
The observed traffic distribution is **consistent** with the manager's expected distribution. The website traffic pattern follows the hypothesized distribution across days of the week.

---

## 6. Assumptions and Conditions

### Critical Assumptions for Chi-Square Tests

**1. Independence of Observations**
- Each observation must be independent
- One person/item counted only once
- **Violation Example:** Surveying the same person multiple times

**2. Random Sampling**
- Data should be randomly collected
- Ensures representativeness

**3. Sample Size Requirements**
- **ALL expected frequencies must be ≥ 1**
- **At least 80% of expected frequencies must be ≥ 5**
- For 2×2 tables: All expected frequencies should be ≥ 5

**What if assumptions are violated?**
- Small expected frequencies: Use Fisher's Exact Test
- Dependent observations: Use McNemar's Test
- Combine categories to increase expected frequencies

### Checking Assumptions: Example

Given this table:

|        | Category A | Category B |
|--------|------------|------------|
| Group 1| 45         | 5          |
| Group 2| 40         | 10         |

Calculate expected frequencies:
```
E(1,A) = (50 × 85)/100 = 42.5 ✓
E(1,B) = (50 × 15)/100 = 7.5 ✓
E(2,A) = (50 × 85)/100 = 42.5 ✓
E(2,B) = (50 × 15)/100 = 7.5 ✓
```

All expected ≥ 5, so Chi-Square test is appropriate.

---

## 7. Advanced Applications

### Application 1: Effect Size - Cramér's V

Chi-Square tells us IF there's a relationship, but not HOW STRONG.

**Cramér's V Formula:**
```
V = √[χ² / (n × min(r-1, c-1))]

Where:
n = sample size
r = number of rows
c = number of columns
```

**Interpretation:**
- V = 0: No association
- V = 0.1: Weak association
- V = 0.3: Moderate association
- V = 0.5+: Strong association

**Example from Example 3:**
```
χ² = 18.182, n = 200, r = 2, c = 2

V = √[18.182 / (200 × min(1, 1))]
V = √[18.182 / 200]
V = √0.0909
V = 0.302

Interpretation: Moderate association between exercise and stress
```

---

### Application 2: Post-Hoc Analysis with Standardized Residuals

When Chi-Square is significant, identify which cells contribute most.

**Standardized Residual Formula:**
```
SR = (O - E) / √E
```

**Interpretation:**
- |SR| > 2: Cell contributes significantly
- |SR| > 3: Very strong contribution

**Example from Example 4:**

| Cell                    | O   | E     | SR    |
|-------------------------|-----|-------|-------|
| 18-30, Clothing         | 60  | 48.75 | +1.61 |
| 18-30, Home Goods       | 25  | 39.00 | -2.24 |
| 31-50, Electronics      | 55  | 45.50 | +1.41 |
| 51+, Home Goods         | 50  | 39.00 | +1.76 |

The cell "18-30, Home Goods" (SR = -2.24) shows young adults buy significantly fewer home goods than expected.

---

### Application 3: Multiple Comparisons

When testing multiple hypotheses, adjust significance level to avoid false positives.

**Bonferroni Correction:**
```
α_adjusted = α / number of tests

Example: 3 tests at α = 0.05
α_adjusted = 0.05 / 3 = 0.0167
```

Only reject H₀ if p-value < 0.0167 for each test.

---

### Application 4: Chi-Square for Trend (Linear-by-Linear Association)

Tests for a linear trend in ordered categories.

**Example:** Testing if disease severity increases with age:

| Age Group | Mild | Moderate | Severe |
|-----------|------|----------|--------|
| Young     | 30   | 15       | 5      |
| Middle    | 20   | 20       | 10     |
| Old       | 10   | 15       | 25     |

Use Chi-Square for Trend to test if severity systematically increases with age.

---

## 8. Common Mistakes and How to Avoid Them

### Mistake 1: Using Chi-Square with Continuous Data

**Wrong:** Testing if mean heights differ between groups
**Right:** Use t-test or ANOVA for continuous data

**Chi-Square needs:** Categories, counts, frequencies

---

### Mistake 2: Confusing Percentages with Counts

**Wrong:**
| Group   | Yes | No  |
|---------|-----|-----|
| Group A | 60% | 40% |
| Group B | 55% | 45% |

**Right:**
| Group   | Yes | No  |
|---------|-----|-----|
| Group A | 60  | 40  |
| Group B | 55  | 45  |

Chi-Square uses **actual counts**, not percentages.

---

### Mistake 3: Ignoring Expected Frequency Requirements

**Problem:** Expected frequency = 2 in a cell

**Solution:**
- Combine categories
- Use Fisher's Exact Test
- Collect more data

---

### Mistake 4: Testing Paired/Matched Data

**Wrong Scenario:** Same people surveyed before and after treatment

|        | Before: Yes | Before: No |
|--------|-------------|------------|
| After: Yes | 40      | 20         |
| After: No  | 10      | 30         |

**Right Test:** Use McNemar's Test for paired categorical data, not Chi-Square.

---

### Mistake 5: Multiple Testing Without Correction

Testing 10 hypotheses at α = 0.05 → ~40% chance of at least one false positive!

**Solution:** Apply Bonferroni or other corrections.

---

### Mistake 6: Confusing Causation with Association

Chi-Square shows **association**, not **causation**.

Example: Ice cream sales and drowning deaths are correlated (hot weather causes both).

---

## 9. Practice Problems

### Problem 1: Basic Goodness of Fit

A restaurant claims 30% of customers order appetizers, 50% order main courses only, and 20% order desserts. In a sample of 150 customers:
- Appetizers: 50
- Main only: 70
- Desserts: 30

Test at α = 0.05.

<details>
<summary>Click for Solution</summary>

**Expected:**
- Appetizers: 150 × 0.30 = 45
- Main only: 150 × 0.50 = 75
- Desserts: 150 × 0.20 = 30

**Chi-Square:**
χ² = (50-45)²/45 + (70-75)²/75 + (30-30)²/30
χ² = 0.556 + 0.333 + 0 = 0.889

**df = 2, Critical value = 5.991**

**Decision:** χ² < 5.991, Fail to reject H₀

**Conclusion:** Data supports the restaurant's claim.
</details>

---

### Problem 2: Test of Independence

Survey on smartphone preference by gender (200 people):

|        | iPhone | Android | Other |
|--------|--------|---------|-------|
| Male   | 35     | 45      | 20    |
| Female | 40     | 35      | 25    |

Test at α = 0.05 if preference depends on gender.

<details>
<summary>Click for Solution</summary>

**Expected frequencies:**
- Male, iPhone: (100 × 75)/200 = 37.5
- Male, Android: (100 × 80)/200 = 40
- Male, Other: (100 × 45)/200 = 22.5
- Female, iPhone: (100 × 75)/200 = 37.5
- Female, Android: (100 × 80)/200 = 40
- Female, Other: (100 × 45)/200 = 22.5

**Chi-Square:**
χ² = (35-37.5)²/37.5 + (45-40)²/40 + (20-22.5)²/22.5
     + (40-37.5)²/37.5 + (35-40)²/40 + (25-22.5)²/22.5
χ² = 0.167 + 0.625 + 0.278 + 0.167 + 0.625 + 0.278 = 2.14

**df = (2-1)(3-1) = 2, Critical value = 5.991**

**Decision:** χ² < 5.991, Fail to reject H₀

**Conclusion:** No significant relationship between gender and phone preference.
</details>

---

### Problem 3: Advanced - Multiple Categories

A genetics experiment expects offspring in ratio 9:3:3:1 (four phenotypes). Observed counts from 640 offspring:
- Type A: 370
- Type B: 120
- Type C: 110
- Type D: 40

Test at α = 0.01.

<details>
<summary>Click for Solution</summary>

**Expected:**
- Type A: 640 × (9/16) = 360
- Type B: 640 × (3/16) = 120
- Type C: 640 × (3/16) = 120
- Type D: 640 × (1/16) = 40

**Chi-Square:**
χ² = (370-360)²/360 + (120-120)²/120 + (110-120)²/120 + (40-40)²/40
χ² = 0.278 + 0 + 0.833 + 0 = 1.111

**df = 3, Critical value (α=0.01) = 11.345**

**Decision:** χ² < 11.345, Fail to reject H₀

**Conclusion:** Data strongly supports the 9:3:3:1 genetic ratio.
</details>

---

## Chi-Square Distribution Table

| df | α = 0.10 | α = 0.05 | α = 0.01 |
|----|----------|----------|----------|
| 1  | 2.706    | 3.841    | 6.635    |
| 2  | 4.605    | 5.991    | 9.210    |
| 3  | 6.251    | 7.815    | 11.345   |
| 4  | 7.779    | 9.488    | 13.277   |
| 5  | 9.236    | 11.070   | 15.086   |
| 6  | 10.645   | 12.592   | 16.812   |
| 7  | 12.017   | 14.067   | 18.475   |
| 8  | 13.362   | 15.507   | 20.090   |
| 9  | 14.684   | 16.919   | 21.666   |
| 10 | 15.987   | 18.307   | 23.209   |

---

## Quick Reference Formula Sheet

**Chi-Square Statistic:**
```
χ² = Σ[(O - E)²/E]
```

**Expected Frequency (Goodness of Fit):**
```
E = n × p
(n = total sample, p = expected proportion)
```

**Expected Frequency (Independence):**
```
E = (Row Total × Column Total) / Grand Total
```

**Degrees of Freedom:**
- Goodness of Fit: df = k - 1 (k = categories)
- Independence: df = (r - 1)(c - 1)

**Cramér's V:**
```
V = √[χ² / (n × min(r-1, c-1))]
```

**Standardized Residual:**
```
SR = (O - E) / √E
```

---

## Summary

### When to Use Chi-Square:
✓ Categorical data
✓ Count/frequency data
✓ Testing independence or goodness of fit
✓ Expected frequencies ≥ 5

### When NOT to Use Chi-Square:
✗ Continuous numerical data
✗ Small expected frequencies (<5)
✗ Paired/matched samples
✗ Percentage data (convert to counts first)

### Remember:
- Chi-Square shows **association**, not **causation**
- Check assumptions before using the test
- Consider effect size (Cramér's V) along with p-value
- Use post-hoc tests to identify which categories differ

---

*End of Complete Chi-Square Guide*
