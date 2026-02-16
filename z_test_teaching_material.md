# Z-Test in Hypothesis Testing: Complete Guide
## From Basic to Advanced

---

## Table of Contents
1. [The Intuition: Why Do We Need Z-Tests?](#section-1)
2. [Prerequisites: Building Blocks](#section-2)
3. [Understanding Hypothesis Testing](#section-3)
4. [The Z-Test: Core Concepts](#section-4)
5. [One-Sample Z-Test](#section-5)
6. [Two-Sample Z-Test](#section-6)
7. [Step-by-Step Examples](#section-7)
8. [Common Mistakes and How to Avoid Them](#section-8)
9. [Advanced Topics](#section-9)
10. [Practice Problems](#section-10)

---

## 1. The Intuition: Why Do We Need Z-Tests? {#section-1}

### The Real-World Problem

Imagine you're a quality control manager at a coffee company. Your bags are supposed to contain 500g of coffee. You randomly pick 50 bags and find the average weight is 495g. 

**The Big Question:** Is your production line broken, or is this just normal variation?

This is exactly what Z-tests help us answer. They tell us whether what we're seeing is:
- **Just random chance** (like flipping a coin and getting 6 heads out of 10), OR
- **Something actually unusual** that needs attention

### The Core Idea

A Z-test is like asking: "If everything was normal, how weird would my observation be?"

Think of it like this:
- You know what's "typical" (the population mean)
- You observe something in a sample
- You calculate: "How many standard deviations away from typical is my observation?"
- If it's too far (say, more than 2 standard deviations), you say: "This is probably not just chance"

---

## 2. Prerequisites: Building Blocks {#section-2}

### 2.1 The Normal Distribution

**What it is:** A bell-shaped curve that describes how data naturally spreads out.

**Why it matters:** Many things in nature follow this pattern:
- Heights of people
- Test scores
- Measurement errors
- Sample means (due to Central Limit Theorem)

**Key Properties:**
- Symmetric around the mean
- Mean = Median = Mode
- About 68% of data falls within 1 standard deviation
- About 95% within 2 standard deviations
- About 99.7% within 3 standard deviations (the 68-95-99.7 rule)

### 2.2 Standard Normal Distribution (Z-Distribution)

This is a special normal distribution with:
- Mean (μ) = 0
- Standard deviation (σ) = 1

**The Magic:** Any normal distribution can be converted to this standard form using the Z-score formula.

### 2.3 The Z-Score

**Formula:** Z = (X - μ) / σ

**What it means:** "How many standard deviations is X away from the mean?"

**Example:**
- Mean height = 170 cm, SD = 10 cm
- Your height = 190 cm
- Z-score = (190 - 170) / 10 = 2
- Interpretation: You're 2 standard deviations taller than average

### 2.4 Sampling Distribution

When you take multiple samples and calculate their means, those means form their own distribution called the **sampling distribution of the mean**.

**Central Limit Theorem (CLT):**
No matter what the original population looks like, if you take large enough samples (usually n ≥ 30), the distribution of sample means will be approximately normal.

**Standard Error:** The standard deviation of the sampling distribution
- Formula: SE = σ / √n
- It tells us how much sample means typically vary

---

## 3. Understanding Hypothesis Testing {#section-3}

### 3.1 The Logic of Hypothesis Testing

Think of hypothesis testing like a trial:
1. We assume innocence (null hypothesis)
2. We gather evidence (collect data)
3. We ask: "Is this evidence strong enough to prove guilt beyond reasonable doubt?"
4. We make a decision

### 3.2 The Two Hypotheses

**Null Hypothesis (H₀):**
- The "nothing special is happening" hypothesis
- Example: "The population mean is 500g"
- We assume this is true until proven otherwise

**Alternative Hypothesis (H₁ or Hₐ):**
- What we're trying to find evidence for
- Example: "The population mean is NOT 500g"

### 3.3 Types of Alternative Hypotheses

**Two-tailed test:**
- H₁: μ ≠ μ₀ (mean is different, could be higher OR lower)
- Use when: You care about any difference
- Example: "Is the coin fair?" (could be biased either way)

**Right-tailed test:**
- H₁: μ > μ₀ (mean is greater)
- Use when: You only care if it's higher
- Example: "Does this drug increase blood pressure?"

**Left-tailed test:**
- H₁: μ < μ₀ (mean is less)
- Use when: You only care if it's lower
- Example: "Does this training reduce defect rates?"

### 3.4 Significance Level (α)

**What it is:** The probability of rejecting H₀ when it's actually true (Type I error)

**Common values:**
- α = 0.05 (5% risk of false positive) - most common
- α = 0.01 (1% risk) - more conservative
- α = 0.10 (10% risk) - less stringent

**Interpretation:** If α = 0.05, we're willing to be wrong 5% of the time when we claim something is significant.

### 3.5 P-Value

**What it is:** The probability of getting your results (or more extreme) if H₀ is true.

**How to use it:**
- If p-value < α: Reject H₀ (result is statistically significant)
- If p-value ≥ α: Fail to reject H₀ (not enough evidence)

**Intuition:**
- Small p-value (< 0.05): "If H₀ were true, what I observed would be very unlikely"
- Large p-value (> 0.05): "My observation could easily happen by chance if H₀ is true"

### 3.6 Critical Values and Rejection Regions

**Critical value:** The Z-score that marks the boundary of the rejection region

For α = 0.05:
- Two-tailed: ±1.96
- Right-tailed: +1.645
- Left-tailed: -1.645

**Rejection region:** If your calculated Z-score falls here, you reject H₀

### 3.7 Type I and Type II Errors

**Type I Error (False Positive):**
- Rejecting H₀ when it's actually true
- Probability = α
- Example: Saying a person has a disease when they don't

**Type II Error (False Negative):**
- Failing to reject H₀ when it's actually false
- Probability = β
- Example: Saying a person is healthy when they have a disease

**Power of a Test:**
- Power = 1 - β
- The probability of correctly rejecting a false H₀
- Higher power is better (typically aim for 0.80 or 80%)

---

## 4. The Z-Test: Core Concepts {#section-4}

### 4.1 When to Use a Z-Test

**Requirements:**
1. The population standard deviation (σ) is known
2. Either:
   - The population is normally distributed, OR
   - Sample size is large (n ≥ 30) - CLT applies

**Reality check:** Z-tests are less common in practice because we rarely know σ. When σ is unknown, we use t-tests instead.

### 4.2 The Z-Test Statistic

**For one sample:**
Z = (X̄ - μ₀) / (σ / √n)

Where:
- X̄ = sample mean
- μ₀ = hypothesized population mean
- σ = population standard deviation (known)
- n = sample size

**What it tells us:** How many standard errors the sample mean is from the hypothesized mean

### 4.3 The Decision Rule

**Method 1: Critical Value Approach**
1. Calculate Z-statistic
2. Compare to critical value
3. If |Z| > critical value, reject H₀

**Method 2: P-Value Approach**
1. Calculate Z-statistic
2. Find corresponding p-value
3. If p-value < α, reject H₀

Both methods give the same conclusion!

---

## 5. One-Sample Z-Test {#section-5}

### 5.1 What It Tests

Compares a sample mean to a known population mean to see if they're significantly different.

**Question it answers:** "Is my sample mean unusually different from what I expected?"

### 5.2 Step-by-Step Procedure

**Step 1: State the hypotheses**
- H₀: μ = μ₀
- H₁: Choose based on research question (≠, >, or <)

**Step 2: Choose significance level**
- Typically α = 0.05

**Step 3: Check assumptions**
- Is σ known?
- Is n ≥ 30 or is population normal?

**Step 4: Calculate test statistic**
- Z = (X̄ - μ₀) / (σ / √n)

**Step 5: Find critical value or p-value**
- Look up in Z-table

**Step 6: Make decision**
- Compare Z to critical value, or p-value to α

**Step 7: State conclusion**
- In context of the problem

### 5.3 Detailed Example: Quality Control

**Scenario:**
A candy company produces bags with a stated weight of 200g. The population SD is known to be 5g. A quality inspector samples 36 bags and finds an average weight of 198.5g. Test at α = 0.05 whether the true mean differs from 200g.

**Solution:**

**Step 1: Hypotheses**
- H₀: μ = 200g (the bags meet specification)
- H₁: μ ≠ 200g (the bags don't meet specification)
- This is two-tailed because we care about both over and under-filling

**Step 2: Significance level**
- α = 0.05

**Step 3: Check assumptions**
- σ = 5g is known ✓
- n = 36 ≥ 30 ✓
- Z-test is appropriate

**Step 4: Calculate test statistic**
- X̄ = 198.5g
- μ₀ = 200g
- σ = 5g
- n = 36
- Z = (198.5 - 200) / (5 / √36)
- Z = -1.5 / 0.833
- Z = -1.80

**Step 5: Find critical value and p-value**
- For two-tailed test at α = 0.05: critical values = ±1.96
- P-value = 2 × P(Z < -1.80) = 2 × 0.0359 = 0.0718

**Step 6: Decision**
- Method 1: |Z| = 1.80 < 1.96, so fail to reject H₀
- Method 2: p-value = 0.0718 > 0.05, so fail to reject H₀

**Step 7: Conclusion**
At the 5% significance level, there is insufficient evidence to conclude that the true mean weight differs from 200g. The observed difference of 1.5g could reasonably be due to random sampling variation.

**Practical interpretation:** The production line appears to be working within acceptable limits.

### 5.4 Confidence Intervals Connection

A 95% confidence interval for μ is:
X̄ ± 1.96 × (σ / √n)

For our example:
198.5 ± 1.96 × (5 / √36) = 198.5 ± 1.63 = (196.87, 200.13)

Notice: 200g falls within this interval, consistent with failing to reject H₀!

**Key insight:** If the hypothesized value falls within the confidence interval, you won't reject H₀.

---

## 6. Two-Sample Z-Test {#section-6}

### 6.1 What It Tests

Compares means from two independent samples to see if they come from populations with different means.

**Question it answers:** "Are these two groups really different, or is the difference just chance?"

### 6.2 The Test Statistic

Z = (X̄₁ - X̄₂) - (μ₁ - μ₂) / √(σ₁²/n₁ + σ₂²/n₂)

Under H₀ (usually μ₁ = μ₂), this simplifies to:

Z = (X̄₁ - X̄₂) / √(σ₁²/n₁ + σ₂²/n₂)

### 6.3 When to Use It

**Requirements:**
1. Both population standard deviations are known
2. Independent samples
3. Either large samples (both n ≥ 30) or normal populations

### 6.4 Step-by-Step Procedure

**Step 1: State hypotheses**
- H₀: μ₁ = μ₂ (or μ₁ - μ₂ = 0)
- H₁: Choose based on question (μ₁ ≠ μ₂, μ₁ > μ₂, or μ₁ < μ₂)

**Step 2: Choose α**

**Step 3: Check assumptions**

**Step 4: Calculate Z-statistic**

**Step 5: Find critical value or p-value**

**Step 6: Make decision**

**Step 7: State conclusion**

### 6.5 Detailed Example: Comparing Two Treatments

**Scenario:**
A pharmaceutical company tests two weight-loss drugs. Drug A is tested on 50 people (mean loss = 12 lbs, σ₁ = 4 lbs). Drug B is tested on 60 people (mean loss = 10 lbs, σ₂ = 3 lbs). At α = 0.05, is Drug A more effective than Drug B?

**Solution:**

**Step 1: Hypotheses**
- H₀: μ₁ = μ₂ (drugs are equally effective)
- H₁: μ₁ > μ₂ (Drug A is more effective)
- This is right-tailed

**Step 2: α = 0.05**

**Step 3: Assumptions**
- σ₁ = 4, σ₂ = 3 are known ✓
- n₁ = 50, n₂ = 60, both ≥ 30 ✓
- Samples are independent ✓

**Step 4: Calculate Z**
- Z = (12 - 10) / √(4²/50 + 3²/60)
- Z = 2 / √(0.32 + 0.15)
- Z = 2 / √0.47
- Z = 2 / 0.686
- Z = 2.92

**Step 5: Critical value and p-value**
- Critical value for right-tailed at α = 0.05: 1.645
- P-value = P(Z > 2.92) = 0.0018

**Step 6: Decision**
- Z = 2.92 > 1.645, so reject H₀
- p-value = 0.0018 < 0.05, so reject H₀

**Step 7: Conclusion**
At the 5% significance level, there is strong evidence that Drug A is more effective than Drug B. The mean weight loss with Drug A is significantly greater.

---

## 7. Step-by-Step Examples {#section-7}

### Example 1: Two-Tailed Test (Machine Calibration)

**Problem:**
A machine fills bottles with a target of 500 ml. Historical records show σ = 10 ml. A sample of 40 bottles has a mean of 496 ml. At α = 0.01, is the machine properly calibrated?

**Solution:**

**Hypotheses:**
- H₀: μ = 500 ml
- H₁: μ ≠ 500 ml (two-tailed)

**Test statistic:**
- Z = (496 - 500) / (10 / √40)
- Z = -4 / 1.58
- Z = -2.53

**Critical values:** ±2.576 (for α = 0.01, two-tailed)

**P-value:** 2 × P(Z < -2.53) = 2 × 0.0057 = 0.0114

**Decision:**
- |Z| = 2.53 < 2.576, fail to reject H₀
- p-value = 0.0114 > 0.01, fail to reject H₀

**Conclusion:**
At the 1% significance level, there is insufficient evidence to conclude the machine is not properly calibrated. While the sample mean is below target, it's not extreme enough to reach significance at this very stringent α level.

**Note:** At α = 0.05, we would reject H₀ (since p = 0.0114 < 0.05). This shows how α affects our conclusions.

### Example 2: Right-Tailed Test (Educational Intervention)

**Problem:**
A new teaching method is tested. Historically, students score μ = 75 with σ = 12. After the new method, 100 students score an average of 78. At α = 0.05, did the method improve scores?

**Solution:**

**Hypotheses:**
- H₀: μ ≤ 75 (no improvement)
- H₁: μ > 75 (improvement)

**Test statistic:**
- Z = (78 - 75) / (12 / √100)
- Z = 3 / 1.2
- Z = 2.5

**Critical value:** 1.645 (right-tailed, α = 0.05)

**P-value:** P(Z > 2.5) = 0.0062

**Decision:**
- Z = 2.5 > 1.645, reject H₀
- p-value = 0.0062 < 0.05, reject H₀

**Conclusion:**
At the 5% significance level, there is strong evidence that the new teaching method improved student scores. The mean increase of 3 points is statistically significant.

### Example 3: Left-Tailed Test (Cost Reduction)

**Problem:**
A company's mean monthly expense is $50,000 (σ = $8,000). After cost-cutting measures, 36 months show a mean of $48,200. At α = 0.10, did expenses decrease?

**Solution:**

**Hypotheses:**
- H₀: μ ≥ 50,000 (no decrease)
- H₁: μ < 50,000 (decrease)

**Test statistic:**
- Z = (48,200 - 50,000) / (8,000 / √36)
- Z = -1,800 / 1,333.33
- Z = -1.35

**Critical value:** -1.28 (left-tailed, α = 0.10)

**P-value:** P(Z < -1.35) = 0.0885

**Decision:**
- Z = -1.35 < -1.28, reject H₀
- p-value = 0.0885 < 0.10, reject H₀

**Conclusion:**
At the 10% significance level, there is evidence that the cost-cutting measures reduced monthly expenses. The mean decreased by $1,800.

---

## 8. Common Mistakes and How to Avoid Them {#section-8}

### Mistake 1: Confusing "Fail to Reject" with "Accept"

**Wrong:** "We accept H₀"
**Right:** "We fail to reject H₀"

**Why it matters:** Failing to find evidence against H₀ doesn't prove H₀ is true. It just means we don't have enough evidence.

**Analogy:** In court, "not guilty" doesn't mean innocent; it means insufficient evidence to prove guilt.

### Mistake 2: Misinterpreting P-Values

**Wrong:** "P-value is the probability that H₀ is true"
**Right:** "P-value is the probability of getting our result (or more extreme) if H₀ is true"

**Example:** If p = 0.03:
- Wrong: "There's a 3% chance H₀ is true"
- Right: "If H₀ were true, we'd see results this extreme only 3% of the time"

### Mistake 3: Using Z-Test When σ is Unknown

**Problem:** Z-tests require known population SD

**Solution:** If σ is unknown:
- Use sample SD (s) and switch to a t-test
- t-tests account for the extra uncertainty

### Mistake 4: Ignoring Sample Size Requirements

**Problem:** Using Z-test with small samples from non-normal populations

**Solution:**
- If n < 30, check if population is approximately normal
- If not normal and n is small, consider non-parametric tests

### Mistake 5: Choosing the Wrong Tail

**How to choose:**
- Two-tailed: "Is there a difference?" (most conservative)
- Right-tailed: "Is it greater?"
- Left-tailed: "Is it less?"

**Red flag:** Don't look at your data first and then choose the tail. That's p-hacking!

### Mistake 6: Confusing Statistical and Practical Significance

**Example:**
- Sample: n = 10,000, X̄ = 500.1 g, σ = 10 g, μ₀ = 500 g
- Z = (500.1 - 500) / (10/√10,000) = 0.1 / 0.1 = 1.0

Wait, let's recalculate:
- Z = (500.1 - 500) / (10/√10,000) = 0.1 / 0.1 = 1.0

Actually with such large n:
- Z = 0.1 / (10/100) = 0.1 / 0.1 = 1.0

With very large samples, even tiny differences become "significant":
- A 0.01g difference might be statistically significant
- But is 0.01g practically important? Probably not!

**Lesson:** Always consider effect size, not just p-value.

### Mistake 7: Multiple Testing Problem

**Problem:** Running many tests increases false positive rate

**Example:** Test 20 hypotheses at α = 0.05
- Expected false positives = 20 × 0.05 = 1

**Solution:**
- Use Bonferroni correction: divide α by number of tests
- Or use methods designed for multiple comparisons

### Mistake 8: Assuming Causation from Significance

**Wrong:** "Drug A is significantly better, so it causes weight loss"
**Right:** "Drug A is significantly associated with greater weight loss"

**Remember:** Correlation ≠ Causation
- Need randomized controlled experiments to establish causation
- Observational studies can only show association

---

## 9. Advanced Topics {#section-9}

### 9.1 Effect Size

**What it is:** A measure of how large the difference is, independent of sample size

**Cohen's d:** (X̄ - μ₀) / σ

**Interpretation:**
- Small effect: d ≈ 0.2
- Medium effect: d ≈ 0.5
- Large effect: d ≈ 0.8

**Why it matters:**
- p-value tells you if effect is real
- Effect size tells you if effect is meaningful

**Example:**
- Difference = 2 points, σ = 10
- d = 2/10 = 0.2 (small effect)
- Might be significant with large sample, but not very important

### 9.2 Power Analysis

**What it is:** Determining required sample size to detect an effect

**Key components:**
1. Desired power (typically 0.80)
2. Significance level (α)
3. Expected effect size
4. Population standard deviation

**Formula for one-sample Z-test:**
n = [(Z₁₋α/₂ + Z₁₋β) × σ / (μ₁ - μ₀)]²

**Example calculation:**
Want to detect a difference of 5 units, σ = 15, α = 0.05, power = 0.80
- Z₁₋α/₂ = 1.96
- Z₁₋β = 0.84
- n = [(1.96 + 0.84) × 15 / 5]² = [8.4]² = 70.56 ≈ 71

**Practical use:** Determine sample size before conducting expensive studies

### 9.3 One-Sided vs Two-Sided: The Debate

**When to use one-sided:**
- Theory strongly predicts direction
- Only one direction has practical implications
- Example: Drug can only improve outcomes, not worsen

**When to use two-sided (safer choice):**
- Exploratory research
- Could be surprised by either direction
- Standard in most scientific journals

**Caution:** One-sided tests are more powerful but can miss important findings in the opposite direction

### 9.4 Relationship Between Z-Test and Confidence Intervals

**Key insight:** Hypothesis test and confidence interval are two sides of same coin

**Rule:**
If 95% CI for μ doesn't contain μ₀, then:
- Two-tailed test at α = 0.05 will reject H₀: μ = μ₀

**Example:**
- H₀: μ = 50
- 95% CI: (52, 58)
- Since 50 is not in CI, reject H₀ at α = 0.05

### 9.5 Sequential Testing and Optional Stopping

**The problem:** Looking at data multiple times and stopping when significant

**Why it's bad:** Inflates Type I error rate way above α

**Example:**
- Plan: test every 10 samples, stop if significant
- Intended α = 0.05
- Actual α can exceed 0.20!

**Solution:**
- Pre-specify sample size and stick to it
- Or use methods designed for sequential testing (group sequential designs)

### 9.6 Equivalence Testing (TOST)

**Different question:** "Are two treatments equivalent?" (not just "are they different?")

**Approach:** Two One-Sided Tests (TOST)
1. Test if difference < lower equivalence bound
2. Test if difference > upper equivalence bound
3. If both reject, treatments are equivalent

**Used in:**
- Generic drug approval
- Non-inferiority trials

### 9.7 Bayesian Alternative to Z-Test

**Frequentist Z-test:** "What's the probability of data given H₀?"

**Bayesian approach:** "What's the probability of H₀ given data?"

**Advantages:**
- More intuitive interpretation
- Can quantify evidence for H₀
- Incorporates prior knowledge

**Bayes Factor:** Ratio of evidence for H₁ vs H₀
- BF > 10: Strong evidence for H₁
- BF < 0.1: Strong evidence for H₀
- 0.1 < BF < 10: Inconclusive

---

## 10. Practice Problems {#section-10}

### Problem Set 1: Basic One-Sample Z-Tests

**Problem 1:**
A standardized test has a national mean of 100 with σ = 15. A school claims their students perform better. They test 50 students who score an average of 105. Test at α = 0.05.

**Problem 2:**
A machine produces parts with historical mean length of 10.0 cm (σ = 0.5 cm). After maintenance, 60 parts average 10.15 cm. Test if the mean changed at α = 0.01.

**Problem 3:**
Battery life should be 400 hours (σ = 40 hours). You test 75 batteries that average 390 hours. At α = 0.05, has battery life decreased?

### Problem Set 2: Two-Sample Z-Tests

**Problem 4:**
Compare two manufacturing plants. Plant A: n = 80, X̄ = 52 units/hour, σ = 8. Plant B: n = 90, X̄ = 49 units/hour, σ = 7. Test at α = 0.05 if they differ.

**Problem 5:**
Men's heights: n = 100, X̄ = 175 cm, σ = 8 cm. Women's heights: n = 120, X̄ = 162 cm, σ = 7 cm. Test if men are taller at α = 0.01.

### Problem Set 3: Mixed Applications

**Problem 6:**
Calculate the 95% confidence interval for Problem 1, and verify it's consistent with your hypothesis test conclusion.

**Problem 7:**
For Problem 3, calculate Cohen's d and interpret the effect size.

**Problem 8:**
You need to detect a mean difference of 3 units from μ = 50 (σ = 12). What sample size do you need for 80% power at α = 0.05?

### Problem Set 4: Critical Thinking

**Problem 9:**
A company tests 100 different products to see if they exceed a quality standard. They find 6 products significant at α = 0.05. Should they be concerned? Explain.

**Problem 10:**
A study with n = 10,000 finds a mean difference of 0.1 with p = 0.04. The researcher claims an important finding. Evaluate this claim considering both statistical and practical significance.

---

## Solutions to Practice Problems

### Solution 1:
- H₀: μ = 100, H₁: μ > 100 (right-tailed)
- Z = (105 - 100) / (15/√50) = 5 / 2.12 = 2.36
- Critical value = 1.645
- p-value = 0.0091
- **Decision:** Reject H₀. Evidence supports that the school's students perform better.

### Solution 2:
- H₀: μ = 10.0, H₁: μ ≠ 10.0 (two-tailed)
- Z = (10.15 - 10.0) / (0.5/√60) = 0.15 / 0.0645 = 2.33
- Critical values = ±2.576
- p-value = 0.0198
- **Decision:** Fail to reject H₀ at α = 0.01. Not enough evidence that mean changed.

### Solution 3:
- H₀: μ ≥ 400, H₁: μ < 400 (left-tailed)
- Z = (390 - 400) / (40/√75) = -10 / 4.62 = -2.17
- Critical value = -1.645
- p-value = 0.015
- **Decision:** Reject H₀. Evidence suggests battery life has decreased.

### Solution 4:
- H₀: μ₁ = μ₂, H₁: μ₁ ≠ μ₂
- Z = (52 - 49) / √(8²/80 + 7²/90) = 3 / 1.138 = 2.64
- Critical values = ±1.96
- p-value = 0.0083
- **Decision:** Reject H₀. The plants have significantly different productivity.

### Solution 5:
- H₀: μ₁ ≤ μ₂, H₁: μ₁ > μ₂ (right-tailed)
- Z = (175 - 162) / √(8²/100 + 7²/120) = 13 / 1.052 = 12.36
- Critical value = 2.326
- p-value ≈ 0
- **Decision:** Reject H₀. Men are significantly taller.

### Solution 6:
- CI = 105 ± 1.96 × (15/√50) = 105 ± 4.16 = (100.84, 109.16)
- Since 100 is not in the interval, consistent with rejecting H₀: μ = 100

### Solution 7:
- Cohen's d = (390 - 400) / 40 = -0.25
- Small effect size. While statistically significant, the practical impact is modest.

### Solution 8:
- n = [(1.96 + 0.84) × 12 / 3]² = [11.2]² = 125.44 ≈ 126 samples needed

### Solution 9:
- Expected false positives = 100 × 0.05 = 5
- Observing 6 is close to expectation
- Not necessarily evidence of real effects; could be multiple testing issue
- Should use corrected α = 0.05/100 = 0.0005 for each test

### Solution 10:
- Cohen's d = 0.1/σ (depends on σ, but likely very small)
- With n = 10,000, even tiny differences are "significant"
- p = 0.04 shows statistical significance
- But 0.1 difference may have no practical importance
- Need context: What's the scale? What's meaningful to users?
- **Conclusion:** Statistically significant but likely not practically significant

---

## Key Takeaways and Summary

### The Big Picture:
1. Z-tests help us decide if observed differences are real or just chance
2. We never "prove" anything, just gather evidence
3. Significance ≠ importance

### Essential Formulas:
- **One-sample Z:** Z = (X̄ - μ₀) / (σ/√n)
- **Two-sample Z:** Z = (X̄₁ - X̄₂) / √(σ₁²/n₁ + σ₂²/n₂)
- **Confidence interval:** X̄ ± Z × (σ/√n)
- **Effect size:** d = (X̄ - μ₀) / σ

### Decision Rules:
- Reject H₀ if: |Z| > critical value OR p-value < α
- Choose tail based on research question before seeing data
- Report both p-value and effect size

### Best Practices:
1. Always state hypotheses clearly
2. Check assumptions before testing
3. Pre-specify α and sample size
4. Report confidence intervals with test results
5. Consider practical significance, not just statistical
6. Be honest about limitations

### When NOT to Use Z-Tests:
- σ is unknown (use t-test)
- Small sample + non-normal data (consider non-parametric)
- Comparing more than 2 groups (use ANOVA)
- Paired/dependent data (use paired t-test)

---

## Further Resources

### For Deeper Understanding:
1. Study Central Limit Theorem visualizations
2. Practice with real datasets
3. Learn simulation methods to understand sampling distributions
4. Explore Bayesian alternatives

### Related Topics to Explore:
- T-tests (when σ unknown)
- ANOVA (comparing multiple groups)
- Chi-square tests (categorical data)
- Non-parametric tests (when assumptions violated)
- Multiple testing corrections
- Power analysis and sample size determination

### Common Statistical Software:
- R: `z.test()` from BSDA package
- Python: `statsmodels.stats.weightstats.ztest()`
- Excel: Can calculate manually with NORM.S.DIST()
- SPSS, SAS, Stata: All have built-in functions

---

**Remember:** Statistics is a tool for decision-making under uncertainty. The Z-test is just one tool in your toolkit. Understanding when and how to use it properly is more important than memorizing formulas!

Good luck with your statistical journey! 🎯📊
