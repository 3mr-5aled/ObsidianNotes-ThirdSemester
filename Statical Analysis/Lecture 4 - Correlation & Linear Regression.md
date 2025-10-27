# Correlation & Linear Regression

**Instructors:** Dr. Ghada Hamed & Dr. Fatma Naguib  
**Course Credits:** Dr. Mahmoud Mounir & Dr. Maryam El Berry

---

## **Agenda**

- **Correlation**
    
- **Linear Regression**
    

---

## **1️⃣ Correlation**

### **1.1 Purpose**

- Study and display the **relationship between two variables**.
    
- Determine whether the variables are **correlated or independent**.
    

### **1.2 Types of Data Relationships**

|Variable Type|Suitable Method|
|---|---|
|Nominal/Ordinal|Contingency Table (Crosstabs)|
|Quantitative|Scatter Plot|

---

### **1.3 Contingency Table (Crosstabs)**

- A **contingency table** displays the joint distribution of **two categorical variables**.
    
- Unlike a **frequency table** (which handles one variable), a contingency table considers **two variables simultaneously**.
    
- Enables analysis of **conditional proportions** (e.g., proportion of people in a category of variable Y given a category of X).
    

#### **Key Concepts**

- **Conditional proportion:** The proportion of cases that fall in a particular cell **given** a category of another variable.
    ![[Pasted image 20251014170921.png]]
- **Column percentages** often used to compare distributions across groups.
    ![[Pasted image 20251014170934.png]]
![[Pasted image 20251014170946.png]]
**Example:**

|Chocolate Consumption|< 50 kg Weight|≥ 50 kg Weight|
|---|---|---|
|Low|17%|83%|
|High|45%|55%|

---

### **1.4 Scatter Plot**

- Used for **quantitative variables**.
    
- **X-axis:** Independent variable
    
- **Y-axis:** Dependent variable
    
- Each data point represents one case.
    

#### **Types of Relationships (Direction)**

- **Positive (Direct):** X ↑ → Y ↑
    
- **Negative (Inverse):** X ↑ → Y ↓
    
- **No Relationship:** X and Y vary independently.
    
![[Pasted image 20251014171929.png]]
#### **Strength of Relationship**

- **Strong:** Points tightly clustered around a line
    
- **Moderate:** Noticeable trend, but some scatter
    
- **Weak:** Wide dispersion of points
    
![[Pasted image 20251014171941.png]]
---

## **2️⃣ Correlation Coefficient (Pearson’s r)**

### **2.1 Definition**

A numerical measure expressing both **direction** and **strength** of a **linear relationship** between two variables.

$$[  
-1 \leq r \leq +1  
]$$

|r Value Range|Relationship Type|
|---|---|
|+1|Perfect positive|
|–1|Perfect negative|
|0|No linear correlation|
|0.6 – 1.0|Strong|
|0.3 – 0.6|Moderate|
|≤ 0.3|Weak|
![[Pasted image 20251014173430.png]]

---

### **2.2 Coefficient of Determination (r²)**

- Indicates how much of the variation in Y is explained by X.
    
- Formula:  
    $$[  
    0 \leq r^2 \leq 1  
    ]$$
    
- **Example:** If r² = 0.86 → 86 % of Y’s variation explained by X.
    

---

### **2.3 Important Notes**

- Always **check scatterplot first**.
    
- **If not linear**, **do not** compute Pearson’s r — it measures only **linear** correlation.
    
- A **curvilinear** relationship may yield a low r (e.g., r = –0.15) despite a strong nonlinear pattern.
    

---

### **2.4 Example Summaries**

- **Example 1:** r = 0.93 → Strong positive (direct) relationship.
    
- **Example 4:** Weak, negative relationship → as X ↑, Y slightly ↓.
    
- **Example 5:** r = 0.693 → Strong positive linear relation; r² = 0.480 (48 % of Y variation explained).
    

---

## **3️⃣ Linear Regression**

### **3.1 Definition**

A statistical method to:

- Find the **best linear relationship** between variables Y (dependent) and X (independent).
    
- **Quantify strength** of that relationship.
    
- **Predict Y** given X.
    

---

### **3.2 Equation**

$$[  
Y = a + bX  
] $$ 
Where:

- **Y:** Dependent variable
    
- **X:** Independent variable
    
- **a:** Intercept
    
- **b:** Slope (rate of change of Y per unit X)
    

---

### **3.3 Computation Steps**

1. Calculate **mean** and **standard deviation** of X and Y.
    
2. Compute **Z-scores** for X (Zx) and Y (Zy).
    
3. Multiply: Zx × Zy.
    
4. Sum products and divide by n → **r**.
    
5. Use r to calculate regression parameters.
    
$$ \hat{y} = b_1x + b_0 $$

$$ b_1 = r \left(\frac{S_y}{S_x}\right) $$

$$ b_1 = \frac{\sum(x - \bar{x})(y - \bar{y})}{\sum(x - \bar{x})^2} $$

$$ b_1 = \frac{n\sum{xy} - (\sum{x})(\sum{y})}{n\sum{x^2} - (\sum{x})^2} $$

$$ b_0 = \bar{y} - b_1\bar{x} $$

$$ b_0 = \frac{\sum{y} - b_1\sum{x}}{n} $$

---

### **3.4 Least Squares Method**

- Minimizes the **sum of squared differences** between observed Y and predicted Ŷ.
    
- Provides the **best-fitting line** through the data points.
    

---

## **4️⃣ Key Takeaways**

- **Correlation** ≠ **Causation**.
    
- Use **Crosstabs** for categorical data, **Scatterplots** for quantitative.
    
- **Pearson’s r** quantifies linear relationships; **r²** measures explanatory power.
    
- **Regression** predicts Y using the best linear fit.
    
- Always **visualize data** before running correlation/regression analyses.
    

---

## **5️⃣ Glossary**

|Term|Definition|
|---|---|
|**Correlation**|Degree of relationship between two variables.|
|**Contingency Table**|Table showing frequency distribution of variables.|
|**Scatter Plot**|Graph showing how two quantitative variables relate.|
|**Pearson’s r**|Statistic measuring strength/direction of linear correlation.|
|**r² (Coefficient of Determination)**|Proportion of Y variation explained by X.|
|**Regression Line**|Line representing best linear prediction of Y from X.|

---

## **6️⃣ Thought-Provoking Questions**

1. Why must we visualize data before calculating r?
    
2. What real-world problems might a strong correlation mislead in?
    
3. How does r² change when adding outliers?
    
4. Can a nonlinear model outperform a linear one when r is low?
    

---

## **7️⃣ Real-World Applications**

- Predicting **sales from advertising spend**.
    
- Studying **BMI vs. calorie intake**.
    
- Forecasting **student performance vs. study hours**.
    
- Measuring **economic growth vs. investment rate**.
    

---

## **8️⃣ Mnemonic Aid**

**“D-S-C-R”** → **Direction, Strength, Causation, Regression**  
Check **Direction** → Measure **Strength** → Avoid assuming **Causation** → Build **Regression** for prediction.

---

## **9️⃣ Potential Exam Questions**

1. Define Pearson’s correlation coefficient and interpret r = –0.75.
    
2. Differentiate between correlation and regression.
    
3. Explain what an r² = 0.65 implies.
    
4. Why can a low r value occur even when two variables are related?
    
5. Write the linear regression equation and interpret coefficients.
    

---

## **🔟 Suggested Resources**

- **Textbook:** _Statistics for Business and Economics_ – Anderson et al.
    
- **Video:** Khan Academy – Correlation & Regression Basics
    
- **Tool:** Excel or SPSS → Scatterplots and r calculation
    

---

## **📈 Concept Diagram (Text-Only)**

```
Correlation & Regression
│
├── Correlation
│   ├── Crosstabs → Nominal/Ordinal
│   ├── Scatterplot → Quantitative
│   ├── Pearson's r (−1 to +1)
│   └── r² = variation explained
│
└── Linear Regression
    ├── Equation: Y = a + bX
    ├── Least Squares Method
    ├── Prediction & Interpretation
    └── Visual check → linearity
```
---