# Statistical Analysis — Lecture 02  
**By:** Dr. Ghada Hamed & Dr. Fatma Naguib  
📧 [GhadaHamed@cis.asu.edu.eg](mailto:GhadaHamed@cis.asu.edu.eg)  
📧 [fatma_mohamed@cis.asu.edu.eg](mailto:fatma_mohamed@cis.asu.edu.eg)  

*Acknowledgment: Thanks to Dr. Mahmoud Mounir & Dr. Maryam El Berry for their contributions to the course content.*

---

## 📋 Agenda
- Recap  
- Histograms (continued)  
- Descriptive Statistics  
  - Central Tendency  
  - Measures of Dispersion  

---

## 🧠 Recap

### What is Statistics & Why?
> The science that deals with the collection, classification, analysis, interpretation, and drawing of conclusions from numerical data.

Statistics simplify complex data, helping visualize and communicate patterns.  
They summarize raw facts into meaningful insights.

---

## 📊 Types of Statistics

| **Descriptive** | **Inferential** |
|------------------|-----------------|
| Collecting | Generalization from samples to population |
| Organizing | Determining relationships among variables |
| Summarizing | Making predictions |
| Presenting | — |

---

## 📈 Phases of Statistical Analysis

### Phase 1 — Data Collection
**Sampling Types**
1. Simple Random Sampling (SRS)  
2. Systematic Sampling  
3. Stratified Sampling  
4. Cluster Sampling  

---

### Phase 2 — Data Organization

**Variables**

| **Qualitative (Categorical)** | **Quantitative** |
|--------------------------------|------------------|
| *Nominal:* Color, Nationality, Marital Status | *Discrete:* Number of goals, rooms, children |
| *Ordinal:* Grades, Flight classes | *Continuous:* Height, Weight, Temperature |

**Data Matrix:** Organizes cases (rows) and variables (columns).

---

### Phase 3 — Data Summary

- **Frequency Tables** (for qualitative data)  
- **Data Recoding**

---

### Phase 4 — Data Presentation

#### Graphs and Shapes of Distributions
- Pie Charts  
- Bar Charts  
- Histograms  
- Frequency Polygons  

---

### 🧩 Example 1 — Blood Type Distribution
> A pie chart shows blood types of 200 people.

a) AB type: `19% × 200 = 38`  
b) Not O type: `(100% - 40%) × 200 = 120`  
c) A or B type: `(16% + 25%) × 200 = 82`

---

### 🧩 Example 2 — Transportation Types
> A pie chart shows how 800 students commute.

a) Bicycle: `45% × 800 = 360`  
b) Not walking: `(100% - 15%) × 800 = 680`  
c) Bus or car: `(30% + 10%) × 800 = 320`

---

## 📊 Histograms and Frequency Distributions

**Histogram Objective:** Show the data distribution shape.  
Equal intervals are required for accurate area comparison.

---

### Example — Newborn Weights

Given 40 newborn weights (32–161 lbs):

- **Range:** `161 - 32 = 129`  
- **Number of Classes:** `1 + 3.3 log(40) ≈ 7`  
- **Class Width:** `129 / 7 ≈ 19`  

| Lower | Upper | Midpoint | Frequency | Relative % |
|--------|--------|-----------|------------|-------------|
| 32 | 51 | 41.5 | 1 | 2.5 |
| 51 | 70 | 60.5 | 2 | 5.0 |
| 70 | 89 | 79.5 | 3 | 7.5 |
| 89 | 108 | 98.5 | 10 | 25.0 |
| 108 | 127 | 117.5 | 12 | 30.0 |
| 127 | 146 | 136.5 | 9 | 22.5 |
| 146 | 165 | 155.5 | 3 | 7.5 |

**Total:** 40 (100%)

---

### Frequency Polygon
Connect midpoints of histogram bars with straight lines to show trend.

---

### Distribution Shapes
- **1 Mode:** Unimodal  
- **2 Modes:** Bimodal  
- **Negative Skew:** Tail on left  
- **Positive Skew:** Tail on right  

---

## 📈 Descriptive Statistics

### Why Descriptive Statistics?
Summarizing data through measures like **mean**, **median**, and **mode** supports better decision-making.  
Central tendency alone may mislead; dispersion adds context.

---

## 📏 Measures of Central Tendency

| **Measure** | **Use Case** | **Notes** |
|--------------|---------------|-----------|
| **Mode** | Non-numeric or small numeric data | Most frequent value |
| **Median** | When data has outliers or skewed | Middle value |
| **Mean** | Numeric, symmetric data | Sum / count; affected by outliers |

---

### Mean (Grouped Data)
Formula:  
$\bar{x} = \frac{\sum f x}{n}$

| Age | Frequency (f) | Midpoint (x) | fx |
|------|----------------|---------------|----|
| 30–34 | 4 | 32 | 128 |
| 35–39 | 5 | 37 | 185 |
| 40–44 | 2 | 42 | 84 |
| 45–49 | 9 | 47 | 423 |

**Mean = 820 / 20 = 41**

---

### Skewed Distributions
- **Positively skewed:** Mean > Median > Mode  
- **Negatively skewed:** Mean < Median < Mode  

---

## 📉 Measures of Dispersion

### 1. Range
$R = \text{Max} - \text{Min}$
Sensitive to outliers.

---

### 2. Interquartile Range (IQR)
$IQR = Q3 - Q1$
Used to identify variability and outliers.

**Example:**
- Q1 = 47  
- Q2 = 83.5  
- Q3 = 164  
- IQR = 117  
- Outliers:
  - Below Q1 − 1.5×IQR = −128.5  
  - Above Q3 + 1.5×IQR = 339.5  

---

### 3. Box Plot
Visualizes median, quartiles, range, and outliers.  
As data variation increases → IQR increases → Dispersion increases.

---

### 4. Variance and Standard Deviation
Measure how far values spread around the mean.

---

# ✅ Summary

**We covered:**
- Data Sampling  
- Data Organization  
- Data Summarization  
- Data Presentation  
- Descriptive Statistics (Central Tendency & Dispersion)

Next: **Inferential Statistics**

---

*End of Lecture 02*
