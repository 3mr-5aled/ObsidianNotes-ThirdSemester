# 📊 CIS240 - Statistical Analysis Lecture 03  
**By Dr. Ghada Hamed & Dr. Fatma Naguib**

---

## **Agenda**
- Descriptive Statistics  
- Measures of Dispersion (Variance & Standard Deviation)  
- Z-Score  

---

## **1️⃣ Measures of Dispersion (Variability)**

### **A. Variance**
- Measures average **squared distance** of observations from the mean.  
- Formula (Ungrouped):  
  $$
  s^2 = \frac{\sum (x - \bar{x})^2}{n - 1}
  $$
- Reason for squaring: deviations above and below mean cancel out; squaring removes negatives.  
- For grouped data:  
  $$
  s^2 = \frac{\sum f x^2 - (\sum f x)^2/n}{n - 1}
  $$

### **B. Standard Deviation (SD)**
- Square root of variance; gives **average linear distance** from mean.  
- Formula:  
  $$
  s = \sqrt{\frac{\sum (x - \bar{x})^2}{n - 1}}
  $$
- Sensitive to outliers.  
- Units are same as data, unlike variance.  

**Interpretation:**  
Higher SD → more spread in data.  
Lower SD → data clustered around mean.  

---

## **2️⃣ Z-Score (Standard Score)**

### **Definition**
- Indicates **how many standard deviations** an observation is from the mean.  
- Formula:  
  $$
  Z = \frac{x - \bar{x}}{s}
  $$
- Standardizes data for comparison across different scales.

### **Interpretation**
- $Z = 0$ → at the mean  
- $Z > 0$ → above the mean  
- $Z < 0$ → below the mean  

**Applications:**  
- Detecting exceptional or common observations.  
- Comparing across distributions with different means and SDs.

---

## **3️⃣ The Empirical Rule (Normal Distribution)**
Applicable for **bell-shaped** distributions:
- **68 %** of data → within ± 1 SD of mean  
- **95 %** → within ± 2 SD  
- **99.7 %** → within ± 3 SD  

**Example:**  
For IQ $(\mu = 100, \sigma = 10)$:  
- 90–110 → 68 %  
- 80–120 → 95 %  
- 70–130 → 99.7 %  

---

## **4️⃣ Chebyshev’s Theorem (Any Distribution)**
- Works for **any shape** of data, not just normal.  
- At least $(1 - 1/k^2)$ of data lie within k SDs of mean.  
  - For $k = 2$ → ≥ 75 %  
  - For $k = 3$ → ≥ 89 %

---

## **5️⃣ Worked Examples**

### **Example 1**
- Dataset: school grades.  
- Found outlier = 4.1 (below $Q_1 − 1.5 IQR$).  
- Mean = 6.86, SD = 1.27.  
- Z-score used to confirm exceptional value.

### **Example 2**
- Heights (100 men): mean = 69.92 in, SD = 1.7 in.  
- 68 % within ± 1 SD, 95 % within ± 2, 100 % within ± 3 SD.  

### **Example 3**
- Male height $(\mu = 69.6, \sigma = 1.4)$:  
  - 68.2–71.0 → 68 %  
  - 66.8–72.4 → 95 %  
  - 65.4–73.8 → ~100 %
### **Example 4 (IQ Scores)**
- 110 → 84th percentile.  
- 120 → 97.5th.  
- 130 → 99.85th.  
### **Example 5 (Chebyshev’s)**
- $n = 50$, mean = 28, SD = 3  
- Interval (22, 34) = ± 2 SD  
- At least 75 % (≈ 38 values) within interval.  
- At most 12 outside.  

---

## **6️⃣ Key Takeaways**
- **Variance:** squared measure of spread.  
- **Standard Deviation:** practical measure (same unit as data).  
- **Z-Score:** standardizes scores for comparison.  
- **Empirical Rule:** for normal data.  
- **Chebyshev’s Rule:** for any data.  
- Always check for **outliers** — they distort variability.  


#### Notes
here's when to use IQR, Z-score, Chebyshev's Theorem, or the Empirical Rule for identifying outliers:

1. **IQR (Interquartile Range)**
    
    - **When to use**: The note mentions an outlier being found "below " in Example 1. This method is particularly useful for detecting outliers, especially when the data is **skewed** or not normally distributed, as it is less sensitive to extreme values than methods relying on the mean and standard deviation.
    - **How it works for outliers**: Values that fall below  or above  are typically considered outliers.
2. **Z-Score (Standard Score)**
    
    - **When to use**: The note states Z-scores are used for "Detecting exceptional or common observations" and "Standardizes data for comparison across different scales." You would use Z-scores when you want to understand how far an individual data point is from the mean in terms of standard deviations.
    - **How it works for outliers**: Observations with a Z-score that has a large absolute value (e.g., typically  or ) are considered exceptional or potential outliers, as they are many standard deviations away from the mean.
3. **Empirical Rule**
    
    - **When to use**: This rule is "Applicable for **bell-shaped** distributions" (i.e., approximately normal distributions). You would use it when you have data that you know or suspect follows a normal distribution.
    - **How it works for outliers**:
        - Approximately 95% of data falls within  standard deviations of the mean.
        - Approximately 99.7% of data falls within  standard deviations of the mean.
        - Therefore, any data point falling outside  standard deviations (especially outside  standard deviations) is a strong candidate for an outlier in a normal distribution.
4. **Chebyshev's Theorem**
    
    - **When to use**: This theorem "Works for **any shape** of data, not just normal." You would use Chebyshev's Theorem when you need to identify potential outliers in a dataset whose distribution shape is unknown or is known to be non-normal.
    - **How it works for outliers**: It provides a _minimum_ percentage of data that must lie within a certain number of standard deviations from the mean. For example, at least 75% of data lies within  standard deviations, and at least 89% within  standard deviations. If a data point falls far outside these bounds, it is an outlier. While less precise than the Empirical Rule for normal data, it offers a robust, conservative estimate for any distribution.

In summary:

- Use **IQR** for skewed data or when you want a robust method less affected by extreme values.
- Use **Z-score** to quantify how "unusual" a specific data point is relative to the mean and standard deviation, especially for roughly symmetric data.
- Use the **Empirical Rule** for data that is known to be or closely approximates a bell-shaped (normal) distribution.
- Use **Chebyshev's Theorem** for _any_ data distribution when you need a general, conservative estimate of how much data falls within a certain range, and thus to identify values that are exceptionally far from the mean.

عشان الdata عندنا مش هتعمل normal distribution عشان نطبق الemprical rule و الoutliers بنجيبهم بالIQR زي ما موجود السلايد إلي قبلها