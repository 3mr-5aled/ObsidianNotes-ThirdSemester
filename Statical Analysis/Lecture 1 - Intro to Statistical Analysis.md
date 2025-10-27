# Lecture 01: Statistical Analysis  
By: Dr. Ghada Hamed & Dr. Fatma Naguib  

Emails: GhadaHamed@cis.asu.edu.eg | fatma_mohamed@cis.asu.edu.eg  

---

## Agenda
- Probability
- What is Statistical Analysis? Why?
- Statistics Types
- Statistics VS Probability
- Applications
- Goal & Syllabus
- Course Outline
- Sampling
- Exploring Data
- Data Representation in Matrix
- Data Summary
- Graphs & Shapes

---

## Probability
- **Branch of mathematics** concerning numerical descriptions of how likely an **event is to occur** (possible outcomes), or how likely a **proposition is true.**

---

## What is Statistics & Why?

> [!col]
> - Science of **collection**, **classification**, **analysis**, **interpretation**, and **conclusion of numerical facts/data.**  
> 	
>- Makes complex things **simple**.  
>	
>- Summarizes raw facts into **meaningful insights.**  
>	
>- Allows visualization and communication of patterns.  
>
>
>> [!col-md]
>>![[Pasted image 20250925142248.png]]


---
## Statistics Types
![[Pasted image 20250925143349.png]]
### Descriptive
- Collecting  
- Organizing  
- Summarizing  
- Presenting  

### Inferential
- Generalization from sample to population  
- Determining relations among variables  
- Making predictions  

---

## Statistics VS Probability
Both involve:
- Size
- Mean
- Variance
- Std deviation  

Difference: use of different symbols and equations.  
![[Pasted image 20250925143415.png]]

| population | sample     |
| ---------- | ---------- |
| parameter  | statistics |
population :LiArrowBigRight: sample :LiEqual: probability 
sample :LiArrowBigRight: population :LiEqual: statical analysis

---
## Applications
- Stock Market Analysis  
- Artificial Intelligence  
- Data Representation  
- Market Research  

---

## Course Outline
- Exploring data, descriptive analysis, mean, variance, graphical representation, quartiles, IQR, Z-scores  
- Probability distributions (discrete, continuous, normal, binomial)  
- Correlation and regression  
- Data representation and description  
- Statistical inference and confidence intervals  

---
## Assessment

### Methods
- Midterm
- Quiz 1
- Quiz 2
- Assignment
- Final Exam  

### Weights
- Midterm: 15%  
- Quiz 1: 10%  
- Quiz 2: 10%  
- Assignment: 5%  
- Final Exam: 60%  

**Total: 100%**  

---

## Books References
- Witte & Witte, *Statistics*, 11th Edition  
- Walpole et al., *Probability and Statistics for Engineers and Scientists*, 9th Ed.  
- Ye & Meyers, *Solution Manual* for Probability and Statistics, 8th Ed.  
- Griffiths, *Head First Statistics*  
- Caffo, *Statistical Inference for Data Science*  
- James et al., *Introduction to Statistical Learning* (with R)  

---

## Course References
All materials (lectures, labs, books, etc.) available at:  
[Course SharePoint](https://cisasuedu-my.sharepoint.com/:f:/g/personal/ghadahamed_cis_asu_edu_eg/EoEIa5cesr9JnOkGjQqZr0EBSxwk2P4S-OhU3vzvztl4iQ?e=4iVceC)

---

---
## Sampling
- Collect feedback (students, Uber users, exams).  
- Must get **unbiased data**.  

### Types
#### 1. Simple Random Sampling (SRS)
> [!col]
>- Population Size = 30  
>- Sample Size = 10  
>- Use random number generator.  
>- (+) **Popular** and simple  
>- (–) May cluster into one group unintentionally (*Baised*) 
>
>> [!col]
>>![[Pasted image 20250925143536.png]]

#### 2. Systematic Sampling
> [!col]
>- Population Size = 30  
>- Sample Size = 10  
>- K = 30 / 10 = 3  
>- Take every K-th element.  
>- (+) More organized  
>- (+) Ensures groups included  
>
>> [!col]
>> ![[Pasted image 20250925143829.png]]

#### 3. Stratified Sampling (classify then collect)
>[!col]
>- Divide population into strata (e.g., gender, color, street).  
>- Sample taken *from each* stratum.  
>- Ensures representation from all groups.  
>
>>[!col]
>>![[Pasted image 20250925145227.png]]
#### 4. Cluster Sampling (classify then select one group)
>[!col]
>- Divide data into clusters.  (groups based on criteria)
>- Choose *one or few* clusters (layer or group) as sample.  
>
>>[!col]
>>![[Pasted image 20250925145348.png]]
---

## Exploring Data
- Data represented as: Cases, Variables, Levels of Measurement.  

	 **CASE** has datatype
	 
	
	
![[Pasted image 20250925145710.png]]
![[Pasted image 20250925150459.png]]
![[Pasted image 20250925150509.png]]
![[Pasted image 20250925150520.png]]
![[Pasted image 20250925150530.png]]
### Levels of Measurement
- Categorical (Qualitative): Nominal, Ordinal  
- Quantitative: Ratio, Interval  
- Discrete: e.g., number of goals  
- Continuous: e.g., weight, height  
![[Pasted image 20250925150544.png]]
---

## Data Matrix & Summary
- Data matrix = cases × variables.  
- Each value = observation.  
- Handle missing values.  (remove or calc the mean) 
	
![[Pasted image 20250925205503.png]]
	
- Summarize using frequency tables:
  - Frequency
  - Percentage
  - Cumulative percentage  
- Recoding: quantitative → ordinal categories.  
![[Pasted image 20250925150602.png]]
![[Pasted image 20250925150626.png]]
![[Pasted image 20250925150642.png]]

![[Pasted image 20250925150804.png]]
	
	If you have a **huge** dataset summarize it into *frequency table*
	
![[Pasted image 20250925150814.png]]
![[Pasted image 20250925150835.png]]
![[Pasted image 20250925150851.png]]
	
Cumulative Percentage :LiArrowBigRight: current % + past %
	
![[Pasted image 20250925150910.png]]
![[Pasted image 20250925150921.png]]
![[Pasted image 20250925150933.png]]


### Summary
1. Convert data to cases and variables in a data matrix.
 2. Data matrix now become the source of all your statistical analysis.
 3. Each variable’s value is called observation.
 4. Each observation (attribute) has a level of measurement which is either quantitative or qualitative.
 5. However, if you want to present your findings to other people, you must summarize your data in form of for example frequency table.
 6. If necessary, you can recode your quantitative values into ordinal ones
![[Pasted image 20250925150955.png]]



---

## Graphs & Shapes of Distributions
- Visualize frequency tables with charts.  
![[Pasted image 20250925151058.png]]

### Charts
- **Pie chart** → small categories, relative frequencies.  
- **Bar chart** → ordinal/discrete data.  
- **Histogram** → large continuous data, intervals.  

![[Pasted image 20250925151121.png]]
![[Pasted image 20250925151132.png]]


### Examples
![[Pasted image 20250925151200.png]]
![[Pasted image 20250925151209.png]]
![[Pasted image 20250925151216.png]]
![[Pasted image 20250925151224.png]]
![[Pasted image 20250925151233.png]].![[Pasted image 20250925151241.png]]
![[Pasted image 20250925151249.png]]
![[Pasted image 20250925151259.png]]
![[Pasted image 20250925151307.png]]
![[Pasted image 20250925151315.png]]
### Summary
![[Pasted image 20250925151330.png]]

*Qualitative* :LiArrowBigRight: **Bar chart :LiBarChartBig:** & **Pie Chart** :LiChartPie:
*Quantitative* :LiArrowBigRight: **Histogram** & **Dot Graph**

Same width in histogram  :LiArrowBigRight: compare in height 
Not Same width :LiArrowBigRight: compare in Area (==Not Good==)

---

## Next Lecture
- Measures of Central Tendency  
- Measures of Variability  


