---
course: Statistical Analysis
lecture: Discrete Probability Distributions and the Binomial Distribution
date: {{date}}
tags: [statistical_analysis, probability, lecture, university, notes]
---

# 🧠 Statistical Analysis – Discrete Probability Distributions and the Binomial Distribution

> [!note]  
> This lecture introduces **discrete probability distributions**, their key measures (mean, variance, standard deviation, expectation), and the **binomial distribution**. Worked examples are included for clarity.

---

## 1. Probability Distributions

### 1.1 Random Variables

> [!note]  
> A **random variable (X)** is a function that associates a **real number** with each element in the **sample space (S)**. Its values are determined by **chance**.  

- **Discrete random variable:** Values can be listed individually.  
- **Continuous random variable:** Values can take any value within a range.

> [!tip]  
> Think: Discrete → countable, Continuous → measurable.

---

### 1.2 Discrete Probability Distribution

> [!note]  
> A **discrete probability distribution** lists all possible values of a random variable and their associated probabilities.  

**Requirements:**
- $0 \le P(X) \le 1$  
- $\sum P(X) = 1$

**Example 1: Single Coin Toss**  
S = {T, H}, X = number of heads  

| X | 0 | 1 |
|---|---|---|
| P(X) | 0.5 | 0.5 |

**Example 2: Two Coin Tosses**  
S = {TT, TH, HT, HH}, X = number of heads  

| X | 0 | 1 | 2 |
|---|---|---|---|
| P(X) | 0.25 | 0.5 | 0.25 |

**Example 3: Three Coin Tosses**  
S = {TTT, TTH, THT, HTT, HHT, HTH, THH, HHH}, X = number of heads  

| X | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| P(X) | 0.125 | 0.375 | 0.375 | 0.125 |

> [!tip]  
> To graph: X-axis → number of heads, Y-axis → P(X).

---

### 1.3 Real-World Example: Baseball World Series

> [!example]  
Data (1965–2005, total series = 40):  

| X (games) | 4 | 5 | 6 | 7 |
|------------|---|---|---|---|
| Frequency | 8 | 7 | 9 | 16 |
| P(X) | 0.2 | 0.175 | 0.225 | 0.4 |

> [!tip]  
> Probability = Frequency / Total series  

- Check: $0.2 + 0.175 + 0.225 + 0.4 = 1$

---

### 1.4 Validating a Probability Distribution

> [!example]  

| X | 0 | 5 | 10 | 15 | 20 |
|---|---|---|---|---|---|
| P(X) | ? | ? | ? | ? | ? |

- Must satisfy: $0 \le P(X) \le 1$ and $\sum P(X) = 1$

---

## 2. Measures of Discrete Probability Distribution

### 2.1 Mean (Expected Value)

> [!note]  
> Formula:  
$$
\mu = E(X) = \sum X_i \cdot P(X_i)
$$

**Example 5-6: Two Children in Family**  

- X = number of girls, S = {BB, BG, GB, GG}  
- P(X) = {0.25, 0.5, 0.25}  

$$
\mu = 0 \cdot 0.25 + 1 \cdot 0.5 + 2 \cdot 0.25 = 1
$$

**Example 5-7: Three Coin Tosses**  

| X | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| P(X) | 0.125 | 0.375 | 0.375 | 0.125 |

$$
\mu = 0\cdot0.125 + 1\cdot0.375 + 2\cdot0.375 + 3\cdot0.125 = 1.5
$$

---

### 2.2 Variance and Standard Deviation

> [!note]  
> Formulas:  
> 
> - Variance:  
> $$
> \sigma^2 = \sum (X_i - \mu)^2 \cdot P(X_i)
> $$
> 
> - Standard Deviation:  
> $$
> \sigma = \sqrt{\sigma^2}
> $$


**Example 5-10: Numbered Balls**  

- Balls: {3,3,4,5,5} → X = {3,4,5}  
- Probabilities: P(3) = 2/5, P(4) = 1/5, P(5) = 2/5  
- Mean:  
$$
\mu = 3\cdot0.4 + 4\cdot0.2 + 5\cdot0.4 = 4
$$  
- Variance:  
$$
\sigma^2 = (3-4)^2\cdot0.4 + (4-4)^2\cdot0.2 + (5-4)^2\cdot0.4 = 0.8
$$  
- Standard Deviation:  
$$
\sigma = \sqrt{0.8} \approx 0.894
$$

---

## 3. The Binomial Distribution

> [!note]  
> A **binomial experiment** satisfies:
1. Each trial has **two outcomes** (success/failure).  
2. Fixed **number of trials (n)**.  
3. **Independent** trials.  
4. Probability of success **p** remains constant.  

**Notation:**  

| Symbol | Meaning |
|--------|---------|
| p | Probability of success |
| q | Probability of failure = 1 − p |
| n | Number of trials |
| X | Number of successes (0…n) |

**Probability of exactly X successes:**  

$$
P(X=x) = \binom{n}{x} p^x q^{n-x}
$$

> [!tip]  
> $\binom{n}{x} = \frac{n!}{x!(n-x)!}$

---

### 3.1 Worked Examples

**Example 1: Tossing Coins**  
- Toss 3 coins, X = 2 heads, p = 0.5, q = 0.5  
$$
P(X=2) = \binom{3}{2} (0.5)^2 (0.5)^1 = 3 \cdot 0.25 \cdot 0.5 = 0.375
$$

**Example 2: Doctor Visits**  
- n = 10, x = 3, p = 0.2, q = 0.8  
$$
P(X=3) = \binom{10}{3} (0.2)^3 (0.8)^7 = 120 \cdot 0.008 \cdot 0.2097152 \approx 0.201
$$

**Example 3: Teen Employment**  
- n = 5, x ≥ 3, p = 0.3, q = 0.7  
$$
P(X\ge3) = P(3)+P(4)+P(5) 
$$
$$
= \binom{5}{3}0.3^3 0.7^2 + \binom{5}{4}0.3^4 0.7 + \binom{5}{5}0.3^5
$$
$$
= 10\cdot0.027\cdot0.49 + 5\cdot0.0081\cdot0.7 + 0.00243
$$
$$
\approx 0.132 + 0.02835 + 0.00243 = 0.1628
$$

---

### 3.2 Mean, Variance, Standard Deviation for Binomial

> [!note]  
> Formulas:  
$$
\mu = n \cdot p, \quad \sigma^2 = n \cdot p \cdot q, \quad \sigma = \sqrt{n \cdot p \cdot q}
$$

**Example 4: Tossing Coin 4 Times**  
- n = 4, p = 0.5  
- Mean: $\mu = 4*0.5 = 2$  
- Variance: $\sigma^2 = 4*0.5*0.5 = 1$  
- SD: $\sigma = 1$

**Example 5: Rolling Die 360 Times (Number of 4s)**  
- n = 360, p = 1/6  
- Mean: $\mu = 360*(1/6) = 60$  
- Variance: $\sigma^2 = 360*(1/6)*(5/6) = 50$  
- SD: $\sigma = \sqrt{50} \approx 7.07$

**Example 6: Traffic Lights**  
- n = 15, p = 0.2, q = 0.8  
- a) Exactly 2 stops:  
$$
P(X=2) = \binom{15}{2} (0.2)^2 (0.8)^{13} \approx 0.27
$$  
- b) At least 1 stop:  
$$
P(X\ge1) = 1-P(X=0) = 1-(0.8)^{15} \approx 0.964
$$

---

## 🧩 Hands-On Practice

1. Construct probability distribution for tossing four coins. Compute mean, variance, SD.  
2. A die is rolled 100 times; find probability of getting exactly 20 sixes.  
3. If p = 0.3 for success in 10 trials, compute probability of ≤ 2 successes.

---

## 📋 Lecture Questions

> [!question]  
> - Determine whether each distribution is a probability distribution.  
> - A student guesses randomly on a 6-question quiz: probability of exactly 3 correct?  
> - Compute mean, variance, SD for given binomial distributions.  
> - Determine probability of “at least X successes” in a binomial experiment.

---

## Glossary

- **Random Variable (X):** Numerical outcome of a chance experiment.  
- **Discrete Probability Distribution:** Table of X values and probabilities.  
- **Mean (µ):** Expected value of a random variable.  
- **Variance (σ²):** Measure of spread of probabilities.  
- **Standard Deviation (σ):** Square root of variance.  
- **Binomial Experiment:** Probability experiment with 2 outcomes per trial.  
- **Success (p) / Failure (q):** Probabilities in a binomial setting.  

---

## Key Takeaways

- Discrete probability distributions model **countable outcomes**.  
- Mean, variance, and standard deviation describe **central tendency and variability**.  
- Binomial distribution is a key model for **two-outcome experiments**.  
- Probabilities must always satisfy **0 ≤ P(X) ≤ 1** and **sum = 1**.  

---

## Quick Review Card

- Q: Formula for mean of discrete variable?  
  A: $\mu = \sum X_i P(X_i)$

- Q: Conditions for binomial experiment?  
  A: Fixed trials, two outcomes, independent, constant p

- Q: Binomial probability formula?  
  A: $P(X=x) = \binom{n}{x} p^x q^{n-x}$

- Q: Variance of binomial?  
  A: $\sigma^2 = n p q$

- Q: SD of binomial?  
  A: $\sigma = \sqrt{n p q}$

---

## Further Resources

- Sheldon Ross, *Introduction to Probability and Statistics for Engineers and Scientists*  
- William Mendenhall, *Statistics for Engineering and the Sciences*  
- Khan Academy: Probability & Statistics series  
