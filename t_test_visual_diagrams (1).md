# Visual Diagrams for t-Test Learning

## 1. Distribution Comparison Visual

```
NORMAL DISTRIBUTION vs t-DISTRIBUTION

Height of curve represents probability density

NORMAL (z-distribution):
        
              ┃
              ┃
         ╱────┃────╲
       ╱      ┃     ╲
     ╱        ┃       ╲
   ╱          ┃         ╲
 ╱            ┃           ╲
╱_____________┃_____________╲___
         μ=0 (mean)

Properties:
- Fixed shape
- Thin tails
- Use when σ known


t-DISTRIBUTION (df = 5):
        
              ┃
              ┃
        ╱─────┃─────╲
      ╱       ┃      ╲
    ╱         ┃        ╲
  ╱           ┃          ╲
╱             ┃            ╲
──────────────┃──────────────────
          μ=0 (mean)

Properties:
- Fatter tails (more area in extremes)
- More probability of extreme values
- Shape depends on df


t-DISTRIBUTION (df = 20):
        
              ┃
              ┃
        ╱─────┃─────╲
      ╱       ┃      ╲
    ╱         ┃        ╲
  ╱           ┃          ╲
 ╱            ┃           ╲
╱_____________┃_____________╲__
          μ=0 (mean)

Properties:
- Closer to normal
- Less fat tails than df=5
- As df→∞, approaches normal
```

---

## 2. Hypothesis Testing Regions Visual

```
TWO-TAILED TEST REGIONS (α = 0.05)

                Critical Values
                ↓           ↓
    Reject H₀   │Accept H₀ │ Reject H₀
      (2.5%)    │  (95%)   │  (2.5%)
                │          │
    ▓▓▓▓▓▓▓▓╱───┼──────────┼───╲▓▓▓▓▓▓▓
    ▓▓▓▓▓▓╱     │          │    ╲▓▓▓▓▓▓
    ▓▓▓▓╱       │          │     ╲▓▓▓▓
    ▓▓╱         │          │      ╲▓▓
    ▓╱__________│__________│_______╲▓
             -t_crit      +t_crit
              (-2.086)    (+2.086)  [df=20]
              
    If calculated t falls in shaded region → Reject H₀


RIGHT-TAILED TEST (α = 0.05)

                         Critical Value
                              ↓
         Accept H₀        │  Reject H₀
          (95%)           │   (5%)
                          │
        ╱─────────────────┼───╲▓▓▓▓▓▓▓
       ╱                  │    ╲▓▓▓▓▓▓
      ╱                   │     ╲▓▓▓▓
     ╱                    │      ╲▓▓
    ╱_____________________│_______╲▓
               0         +t_crit
                        (+1.725)  [df=20]
                        
    If calculated t > t_crit → Reject H₀


LEFT-TAILED TEST (α = 0.05)

        Critical Value
             ↓
      Reject H₀      │    Accept H₀
        (5%)         │     (95%)
                     │
    ▓▓▓▓▓▓╱──────────┼─────────────╲
    ▓▓▓▓▓╱           │              ╲
    ▓▓▓╱             │               ╲
    ▓╱               │                ╲
    ▓╱_______________│_________________╲
               -t_crit        0
              (-1.725)        [df=20]
              
    If calculated t < -t_crit → Reject H₀
```

---

## 3. Decision Tree for Choosing t-Test

```
                    START: I have data to analyze
                                │
                                │
            ┌───────────────────┴───────────────────┐
            │                                       │
    How many groups/samples?                   What am I
            │                               comparing to?
            │                                       │
    ┌───────┴────────┬─────────────┐              │
    │                │             │              │
  ONE             TWO          THREE+             │
  GROUP          GROUPS        GROUPS             │
    │                │             │              │
    │                │          Use ANOVA      KNOWN VALUE
    │                │          (not t-test)   or POPULATION
    │                │                         PARAMETER
    │                │                              │
    │                │                              │
    │         ┌──────┴──────┐                      │
    │         │             │                      │
    │    Are groups     Related                    │
    │    related?       (paired)                   │
    │         │             │                      │
    │    Independent        │                      │
    │         │             │                      │
    │         │             │                      │
    ▼         ▼             ▼                      ▼
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  ONE-SAMPLE t-TEST                                      │
│  ───────────────────                                    │
│  Example: Is average height = 170 cm?                   │
│  Formula: t = (x̄ - μ₀)/(s/√n)                          │
│  df = n - 1                                             │
│                                                         │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  INDEPENDENT TWO-SAMPLE t-TEST                          │
│  ──────────────────────────────                         │
│  Example: Do men and women differ in height?            │
│  Formula: t = (x̄₁ - x̄₂)/√[s²ₚ(1/n₁ + 1/n₂)]           │
│  df = n₁ + n₂ - 2                                       │
│                                                         │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  PAIRED SAMPLE t-TEST                                   │
│  ─────────────────────                                  │
│  Example: Weight before vs. after diet                  │
│  Formula: t = d̄/(sᵈ/√n)                                │
│  df = n - 1                                             │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 4. Calculation Workflow Visual

```
STEP-BY-STEP CALCULATION PROCESS

┌─────────────────────────────────────────────────────────┐
│ STEP 1: STATE HYPOTHESES                                │
├─────────────────────────────────────────────────────────┤
│  H₀: [Null - no effect/difference]                      │
│  H₁: [Alternative - what you're testing]                │
│  α = 0.05 (or your chosen level)                        │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│ STEP 2: COLLECT AND ORGANIZE DATA                       │
├─────────────────────────────────────────────────────────┤
│  List all observations                                  │
│  Check for outliers                                     │
│  Verify data entry                                      │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│ STEP 3: CALCULATE DESCRIPTIVE STATISTICS                │
├─────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────┐               │
│  │ Sample Mean (x̄)                     │               │
│  │ x̄ = Σx / n                          │               │
│  │                                     │               │
│  │ Sample: 10, 12, 14, 11, 13          │               │
│  │ x̄ = (10+12+14+11+13)/5 = 12        │               │
│  └─────────────────────────────────────┘               │
│                                                         │
│  ┌─────────────────────────────────────┐               │
│  │ Sample Standard Deviation (s)       │               │
│  │                                     │               │
│  │ Step 1: Find deviations from mean   │               │
│  │ (10-12)=-2, (12-12)=0, (14-12)=2    │               │
│  │ (11-12)=-1, (13-12)=1                │               │
│  │                                     │               │
│  │ Step 2: Square deviations           │               │
│  │ 4, 0, 4, 1, 1                       │               │
│  │                                     │               │
│  │ Step 3: Sum = 10                    │               │
│  │                                     │               │
│  │ Step 4: Variance = 10/(5-1) = 2.5   │               │
│  │                                     │               │
│  │ Step 5: s = √2.5 = 1.58             │               │
│  └─────────────────────────────────────┘               │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│ STEP 4: CALCULATE t-STATISTIC                           │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  t = (x̄ - μ₀) / (s / √n)    [One-sample example]       │
│                                                         │
│  t = (12 - 10) / (1.58 / √5)                            │
│  t = 2 / (1.58 / 2.236)                                 │
│  t = 2 / 0.707                                          │
│  t = 2.83                                               │
│                                                         │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│ STEP 5: DETERMINE CRITICAL VALUE                        │
├─────────────────────────────────────────────────────────┤
│  df = n - 1 = 5 - 1 = 4                                 │
│  α = 0.05, two-tailed                                   │
│                                                         │
│  Look up in t-table:                                    │
│  t_critical = ±2.776                                    │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│ STEP 6: COMPARE AND DECIDE                              │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Decision Rule: Reject H₀ if |t| > t_critical          │
│                                                         │
│  Our t = 2.83                                           │
│  Critical value = 2.776                                 │
│                                                         │
│  Since 2.83 > 2.776  → REJECT H₀                        │
│                                                         │
│       │                                                 │
│       ├─→ YES → Reject H₀ → Significant result         │
│       │                                                 │
│       └─→ NO → Fail to reject → Not significant        │
│                                                         │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│ STEP 7: INTERPRET IN CONTEXT                            │
├─────────────────────────────────────────────────────────┤
│  "The sample mean (12) is significantly different       │
│  from the hypothesized value (10), t(4) = 2.83,         │
│  p < 0.05."                                             │
│                                                         │
│  In plain English: The data provides strong evidence    │
│  that the true mean is not 10.                          │
└─────────────────────────────────────────────────────────┘
```

---

## 5. Type I and Type II Errors Visual

```
REALITY vs YOUR DECISION

                    REALITY (Unknown)
                │                        │
                │   H₀ is TRUE          │   H₀ is FALSE
                │   (No effect)         │   (Real effect)
    ────────────┼───────────────────────┼─────────────────
                │                        │
    REJECT H₀   │   TYPE I ERROR        │   ✓ CORRECT
    (Claim      │   (False Positive)    │   (True Positive)
    effect      │                        │
    exists)     │   Probability = α     │   Probability = 1-β
                │   (Significance level)│   (Statistical Power)
                │                        │
    ────────────┼───────────────────────┼─────────────────
                │                        │
    FAIL TO     │   ✓ CORRECT           │   TYPE II ERROR
    REJECT H₀   │   (True Negative)     │   (False Negative)
    (No claim   │                        │
    of effect)  │   Probability = 1-α   │   Probability = β
                │                        │
    ────────────┴───────────────────────┴─────────────────


MEDICAL TEST ANALOGY:

            REALITY: Disease Status
            │                    │
            │  Healthy           │  Diseased
  ──────────┼────────────────────┼──────────────
            │                    │
  Test      │  FALSE POSITIVE    │  TRUE POSITIVE
  Positive  │  (Type I Error)    │  (Correct!)
            │  Anxiety for       │  Get treatment
            │  patient           │
  ──────────┼────────────────────┼──────────────
            │                    │
  Test      │  TRUE NEGATIVE     │  FALSE NEGATIVE
  Negative  │  (Correct!)        │  (Type II Error)
            │  Patient relieved  │  Miss disease!
            │                    │  Most dangerous
  ──────────┴────────────────────┴──────────────


BALANCING THE ERRORS:

  Strict α (e.g., 0.01)
  ├─ Fewer Type I errors (good)
  └─ More Type II errors (bad)
  
  Lenient α (e.g., 0.10)
  ├─ More Type I errors (bad)
  └─ Fewer Type II errors (good)
  
  Best: Increase sample size!
  └─ Reduces BOTH error types
```

---

## 6. P-Value Visualization

```
UNDERSTANDING P-VALUES

What is a p-value?
The probability of obtaining results as extreme as (or more 
extreme than) the observed results, assuming H₀ is true.


Example: Two-Tailed Test, t = 2.5

              │
              │         Shaded areas = p-value
              │         (Both tails combined)
         ╱────┼────╲
       ╱      │     ╲    ▓▓ = probability of getting
     ╱▓▓      │      ▓▓╲      t ≤ -2.5 or t ≥ 2.5
   ╱▓▓        │        ▓▓╲    IF H₀ is true
 ╱▓▓__________│__________▓▓╲
        -2.5  0  2.5
         ↑         ↑
    Our result  Our result


Interpreting p-values:

p-value     Strength of Evidence Against H₀
─────────────────────────────────────────────
> 0.10      Little to no evidence
0.05-0.10   Weak evidence
0.01-0.05   Moderate evidence (often "significant")
0.001-0.01  Strong evidence
< 0.001     Very strong evidence


COMMON MISCONCEPTION:

❌ "p = 0.03 means there's a 3% chance H₀ is true"

✓ "p = 0.03 means if H₀ were true, there's a 3%
   chance we'd get results this extreme or more"


Decision Rule:
├─ If p < α → Reject H₀
└─ If p ≥ α → Fail to reject H₀
```

---

## 7. Confidence Interval Visual

```
95% CONFIDENCE INTERVAL

Population Mean (μ) is somewhere in this range:

      │                                      │
      │         Point Estimate (x̄)          │
      │               ↓                      │
  ────┼───────────────●───────────────────┼────
      │               │                      │
   Lower          Sample                 Upper
   Bound           Mean                  Bound
  (x̄ - ME)                             (x̄ + ME)
  
  ME = Margin of Error = t_critical × SE


Interpretation of 95% CI:

"If we repeated this study 100 times, about 95 of the 
100 confidence intervals would contain the true 
population mean."


Example: Weight Loss Study

    95% CI: [3.2 lbs, 6.3 lbs]
    
          │           │           │
    ──────┼───────────●───────────┼──────
          │           │           │
         3.2        4.75         6.3
                     │
              Point Estimate
    
    Interpretation:
    "We are 95% confident the true average weight 
    loss is between 3.2 and 6.3 lbs"


Relationship to Hypothesis Testing:

    H₀: μ = 0 (no weight change)
    
          0           │           │
    ──────┼───────────┼───────────┼──────
          ↑           │           │
        H₀ value     3.2         6.3
        is NOT
        in interval
        
    Therefore: REJECT H₀
    (Consistent with hypothesis test)


CI Width and Sample Size:

    Small n (n=10):
    ────┼─────────────●─────────────┼────
        │    Wide interval          │
        
    Large n (n=100):
    ──────┼─────●─────┼──────
          │ Narrow  │
          
    Larger n → More precise estimate → Narrower CI
```

---

## 8. Effect Size Visualization

```
STATISTICAL SIGNIFICANCE vs PRACTICAL SIGNIFICANCE

Scenario A: Large Sample (n=1000)
─────────────────────────────────
Mean difference: 0.5 points
p-value: 0.03 (significant!)
Cohen's d: 0.1 (tiny effect)

    Group 1: ──●──  (mean = 50.0)
    Group 2:   ──●──  (mean = 50.5)
                 ↑
           Only 0.5 difference
           
Result: Statistically significant but practically meaningless


Scenario B: Small Sample (n=20)
────────────────────────────────
Mean difference: 5.0 points
p-value: 0.08 (not significant)
Cohen's d: 0.8 (large effect)

    Group 1: ──●──  (mean = 50.0)
    Group 2:        ────●────  (mean = 55.0)
                         ↑
                   5 point difference
                   
Result: Not statistically significant but large practical effect
(May need more participants)


Cohen's d Scale:

    0        0.2      0.5      0.8      1.2
    │───────●────────●────────●────────●────
    Negligible Small  Medium  Large    Very Large
    
    
Visual Overlap of Distributions:

Small Effect (d = 0.2):
    ╱──────╲  ╱──────╲
   ╱        ╲╱        ╲
  ╱          ╳         ╲
 ╱__________╱ ╲__________╲
        Group1  Group2
        (High overlap)


Medium Effect (d = 0.5):
    ╱────╲   ╱────╲
   ╱      ╲ ╱      ╲
  ╱        ╳        ╲
 ╱________╱ ╲________╲
       Group1  Group2
       (Moderate overlap)


Large Effect (d = 0.8):
    ╱───╲    ╱───╲
   ╱     ╲  ╱     ╲
  ╱       ╲╱       ╲
 ╱________╱╲________╲
      Group1  Group2
      (Little overlap)
```

---

## 9. Sample Size and Power

```
STATISTICAL POWER RELATIONSHIPS

Power = Probability of detecting a real effect


Effect of Sample Size on Power:

Small Sample (n=20):
Low Power (60%)

    ╱─────╲         ╱─────╲
   ╱H₀     ╲       ╱ H₁    ╲
  ╱         ╲     ╱         ╲
 ╱___________╲▓▓▓╱___________╲
              ↑Critical
              value
         ▓ = Power (area we detect H₁)
         Small area = Low power


Large Sample (n=100):
High Power (95%)

    ╱╲          ╱───────╲
   ╱H₀╲        ╱   H₁    ╲
  ╱    ╲      ╱           ╲
 ╱______╲▓▓▓▓╱_____________╲
         ↑
    Critical value
    
    Large ▓ area = High power


Power is affected by:

    Factor              Effect on Power
    ────────────────────────────────────
    Sample Size ↑       Power ↑
    Effect Size ↑       Power ↑
    Alpha (α) ↑         Power ↑
    Variability ↓       Power ↑
    

Recommended Power:
    Minimum: 0.80 (80%)
    Preferred: 0.90 (90%)
    

Sample Size Planning:

            Large effect size
                   │
                   ▼
    Need        Smaller
    Fewer    ←  sample
    Subjects    size
                   │
                   
            Small effect size
                   │
                   ▼
    Need        Larger
    More     ←  sample
    Subjects    size
```

---

## 10. Assumption Checking Visual

```
CHECKING t-TEST ASSUMPTIONS

1. NORMALITY CHECK
──────────────────

Histogram:        Q-Q Plot:

Symmetric:        Points follow line:
  ┃                   •
 ┃┃┃                 •
┃┃┃┃┃               •
───────             •─────
✓ Normal            ✓ Normal


Skewed:           Points curve:
┃                    •
┃┃                  •
┃┃┃               •
┃┃┃┃           •
───────        •─────
✗ Not normal   ✗ Not normal


2. EQUAL VARIANCE CHECK (Independent t-test)
─────────────────────────────────────────────

Group 1:  ──╱────╲──
Group 2:  ──╱────╲──

Spread similar → ✓ Equal variance


Group 1:  ──╱──╲──
Group 2:  ───╱──────╲───

Spread different → ✗ Unequal variance
                   → Use Welch's t-test


Rule of Thumb:
If (larger variance)/(smaller variance) < 2
→ Equal variance assumption OK


3. INDEPENDENCE CHECK
─────────────────────

✓ Independent:
Person 1: ●        ●        ●
Person 2: ●        ●        ●
Person 3: ●        ●        ●

Each observation unrelated


✗ Not Independent:
Person 1: ●─────────●  (before/after)
Person 2: ●─────────●
Person 3: ●─────────●

Observations related → Use paired t-test


4. OUTLIER CHECK
────────────────

Boxplot:

    │
    ├──┬──┐
    │  │  │       ●  ← Outlier
    ├──┴──┤          (>1.5 IQR from box)
    │
    
Check outliers:
- Data entry error? Fix it
- True extreme value? Consider robust methods
- One outlier in small sample? Big impact!
```

---

## 11. Common Scenarios Decision Map

```
WHICH TEST DO I NEED?

Scenario: Comparing average height to 170cm
    └─→ ONE-SAMPLE t-test


Scenario: Men vs Women height
    ├─ Different people?
    │   └─→ INDEPENDENT t-test
    │
    └─ Same people measured twice?
        └─→ PAIRED t-test


Scenario: Before and after treatment
    └─→ PAIRED t-test (same people)


Scenario: Treatment vs Control groups
    └─→ INDEPENDENT t-test (different people)


Scenario: Three different diets
    └─→ NOT t-test! Use ANOVA


Scenario: Comparing to published standard (μ=100, σ=15)
    └─→ ONE-SAMPLE t-test
        (if σ known and n>30, could use z-test)


Scenario: Twins - one gets treatment, other doesn't
    └─→ PAIRED t-test (matched pairs)


Scenario: Survey of East vs West customers
    ├─ Random independent samples?
    │   └─→ INDEPENDENT t-test
    │
    └─ Same customers at two times?
        └─→ PAIRED t-test
```

---

## 12. Critical Value Lookup Guide

```
HOW TO USE t-TABLE

Table Structure:

     df │  α=0.10  α=0.05  α=0.01  (Two-tailed)
        │  0.05    0.025   0.005   (One-tailed)
    ────┼────────────────────────────────────
     1  │  6.314   12.706   63.657
     2  │  2.920    4.303    9.925
     5  │  2.015    2.571    4.032
    10  │  1.812    2.228    3.169
    20  │  1.725    2.086    2.845
    30  │  1.697    2.042    2.750
    ∞   │  1.645    1.960    2.576


Step 1: Calculate df
    └─ One-sample: df = n-1
    └─ Independent: df = n₁+n₂-2
    └─ Paired: df = n-1


Step 2: Determine α and tails
    └─ Two-tailed: Use top row
    └─ One-tailed: Use bottom row


Step 3: Find intersection
    
    Example: df=20, two-tailed, α=0.05
    
     df │  α=0.05
    ────┼─────────
    20  │  2.086  ← Your critical value
    
    
Step 4: Apply to test
    └─ Two-tailed: ±2.086
    └─ Right-tailed: +2.086
    └─ Left-tailed: -2.086
```

This visual guide complements the main t-test document and provides
quick reference diagrams for understanding key concepts visually.

