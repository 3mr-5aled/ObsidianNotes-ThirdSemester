# 🧠 **Lecture 4 Notes – Gate-Level Minimization (K-Maps)**

_Instructor: Dr. Mirvat Al-Qutt — Ain Shams University (FCIS)_  
_Course: Digital Logic Design_

---

## **📘 Chapter Outline**

1. Introduction
    
2. The Map Method
    
3. Four-Variable Map
    
4. Five-Variable Map
    
5. Product-of-Sums Simplification
    
6. Don’t-Care Conditions
    

---

## **1️⃣ Gate-Level Minimization**

### 🔹 Definition

**Gate-level minimization** = finding an **optimal Boolean implementation** of a digital circuit (fewest logic gates).

### 🔹 Representations of Boolean Functions

- **Boolean Expression:** many forms
    
- **Truth Table:** unique representation
    
- **Logic Gate Diagram:** many possible realizations
    

| Representation     | Count  | Example               |
| ------------------ | ------ | --------------------- |
| Boolean Expression | Many   | $( F = xy + x'z )$    |
| Truth Table        | Unique | Table of input/output |
| Logic Diagram      | Many   | AND–OR–NOT circuit    |
> [!tip]
> The **truth table** representation is unique, while **Boolean expressions and diagrams** have multiple valid forms.

---

## **2️⃣ The Map Method (Karnaugh Map – K-Map)**

### 🔹 Purpose

To **simplify Boolean expressions** and **reduce circuit complexity** pictorially.

### 🔹 Comparison

|Approach|Pros|Cons|
|---|---|---|
|**Algebraic Simplification**|Logical, stepwise|No fixed rules, non-unique results|
|**K-Map Method**|Visual, systematic, quick|Harder > 5 variables|

**Concept:**  
A K-Map is a **pictorial truth table** arranged so that **adjacent cells differ by only one variable** (Gray code).

> [!example]
> Adjacent cells differ by **one bit**, not by value.  
> Example: In 3-variable map → `000` is adjacent to `001` and `100`, not `011`.

---

## **3️⃣ Two-Variable Map**

- Variables: ( x, y ) → 4 minterms
    
- Rows = ( x, x' ), Columns = ( y, y' )
    

Example Simplification:  
$$  
m_3 = xy,\quad m_1+m_2+m_3 = x'y + xy' + xy  
$$  
$$  
= y(x'+x)+xy' = y+xy' = (y+x)(y+y') = x+y  
$$


>[!example]
| x\y |  y' |  y  |
|:---:|:---:|:---:|
| x'  |  0  |  1  |
| x   |  1  |  1  |
>
>✅ Simplified: **F = x + y**


> [!note]  
> For 2-variable maps, _pairs simplify to single literals._
---

## **4️⃣ Three-Variable Map**

- Variables: ( x,y,z ) → 8 minterms
    
- Adjacent cells differ by one variable (Gray code)
    
- Example adjacencies:
    
    - $( m_1+m_3 = x’z(y’+y)=x’z )$
        
    - $( m_1+m_3+m_5+m_6 = z(x’+x)=z )$
        

### 🔹 Example Simplification

$$ 
F(x,y,z) = \Sigma(2, 3, 4, 5) ⇒ F = x'y + xy'  
$$
>[!example]
>| x\yz | 00 | 01 | 11 | 10 |
|:----:|:--:|:--:|:--:|:--:|
| x'   |  0 |  1 |  1 |  0 |
| x    |  1 |  1 |  0 |  0 |
✅ Simplified: **F = x'y + xy'**


### 🔹 K-Map Rules

> [!important]
> 
> 1. Group $2^n$ adjacent 1’s (1, 2, 4, 8, …)
>     
> 2. Use wrapping for edges (map folds).
>     
> 3. Choose largest possible groups.
>     
> 4. Overlaps are allowed.
>     
> 5. Every 1 must be covered at least once.
>     
> 6. Stop when all 1’s are covered.
>     
> 7. Each group → one simplified term.
>     
> 8. Avoid redundant groups.
>

---

### 🔹 Examples

| Function                             | Minterms      | Simplified F     |
| ------------------------------------ | ------------- | ---------------- |
| $( F(x,y,z)=\sigma(3, 4, 6, 7) )$    | 3, 4, 6, 7    | ( F = yz + xz' ) |
| $( F(x,y,z)=\Sigma(0, 2, 4, 5, 6) )$ | 0, 2, 4, 5, 6 | ( F = z' + xy' ) |
| $( F(A,B,C)=A'C + A'B + AB'C + BC )$ | 1, 2, 3, 5, 7 | ( F = C + A'B )  |

---

## **5️⃣ Four-Variable Map (w,x,y,z)**

- 16 minterms arranged in Gray code order.
    
- Groups can be 2, 4, 8, or 16 cells.
    

### 🔹 Example

$$  
F(w,x,y,z)=\Sigma(0,1,2,4,5,6,8,9,12,13,14)  
$$  
✅ Simplified:  
$$
F = y' + w'z' + xz'  
$$

### 🔹 Another Example

$$
F=A'B'C' + B'CD' + A'BCD' + AB'C'D + AB'D'  
$$  
✅ Simplified:  
$$ 
F = B'C' + B'D' + A'CD'  
$$
>[!example]
| wx\yz | 00 | 01 | 11 | 10 |
|:-----:|:--:|:--:|:--:|:--:|
| 00    |  1 |  1 |  0 |  1 |
| 01    |  1 |  1 |  1 |  1 |
| 11    |  1 |  1 |  1 |  0 |
| 10    |  1 |  1 |  0 |  0 |
✅ Simplified: **F = x'y + xy'**
---

### 📈 Number of Adjacent Squares vs. Number of Literals

|Adjacent Squares|Literals in Term|
|--:|:--|
|1|4|
|2|3|
|4|2|
|8|1|
|16|0 (constant 1)|

---

## **6️⃣ Product-of-Sums (POS) Simplification**

Sometimes we need **POS** instead of **SOP**.

### 🔹 Steps

1. Find ( F' ) in **sum-of-products** (by grouping 0’s on K-Map).
    
2. Apply **De Morgan’s theorem**:  
    $$ 
    F = (F')' \Rightarrow \text{SOP} → \text{POS}  
    $$
### 🔹 Example
$$  
F'=yz+wx'y  
$$
$$
F=(yz+wx'y)'=(Y'+Z')(W'+X+Y')  
$$
### 🔹 Example 2
$$ 
F(x,y,z)=\Sigma(1,3,4,6)  
$$
$$ 
F'=x'z+xz' \Rightarrow F = (x'+z)(x+z')  
$$

### 🔹 Example 3

$$ 
F(A,B,C,D)=\Sigma(0,1,2,5,8,9,10)  
$$  
$$ 
F_{SOP}=B'D'+B'C'+A'C'D,\quad  
F'_{SOP}=AB+CD+BD'  
$$  
$$
✅  F_{POS}=(A'+B')(C'+D')(B'+D)  
$$
> [!tip]  
> POS = Product of Sums = **AND of OR terms**  
> SOP = Sum of Products = **OR of AND terms**

---

## **7️⃣ Don’t-Care Conditions**

### 🔹 Concept

When the function output is **unspecified for some input combinations**, these entries (“x” or “d”) can be treated as **0 or 1 to simplify F**.

### 🔹 Example

$$ 
F(w,x,y,z)=\Sigma(1,3,7,11,15),\quad  
d(w,x,y,z)=\Sigma(0,2,5)  
$$  
Combine F and d for simplification:  
$$ 
F = \Sigma(0,1,2,3,7,11,15)  
$$  
✅ **Simplified result:** $( F = \Sigma(1,3,5,7,11,15) )$

>[!example]  
Don’t-care conditions occur when certain input combinations never happen, such as unused input codes in a decoder.

---

## **💡 Key Takeaways**

- K-Maps provide a visual method to minimize Boolean functions.
    
- Group adjacent 1’s → SOP; group 0’s → POS.
    
- Don’t-care entries help achieve simpler circuits.
    
- Larger groups = fewer literals = simpler hardware.
    

---

## **📚 Suggested Resources**

- _M. Morris Mano,_ **Digital Design**, 6th Ed.
    
- _Floyd,_ **Digital Fundamentals** – Ch. 3 (K-Maps)
    
- YouTube: “Gate-Level Minimization & K-Maps – Neso Academy”
    
- Website: [AllAboutCircuits.com – K-Map Simplification$$(https://www.allaboutcircuits.com/)
    

---

## **🧩 Glossary**

| Term           | Meaning                                             |     |
| -------------- | --------------------------------------------------- | --- |
| **Minterm**    | AND combination where function = 1                  |     |
| **Maxterm**    | OR combination where function = 0                   |     |
| **SOP**        | Sum of Products                                     |     |
| **POS**        | Product of Sums                                     |     |
| **Don’t-Care** | Undefined output used for simplification            |     |
| **Gray Code**  | Code sequence where adjacent values differ by 1 bit |     |

---
>[!summary]
>## **🧠 Memory Aid**
>- **“2, 4, 8 – Group to Make It Great!”** → always group powers of two in K-Maps. 
>- **“1’s for SOP, 0’s for POS”** → remember which values to group.

---
## **📝 Exam-Style Questions**

1. Simplify ( F(x,y,z)=\Sigma(1, 3, 7) ) using a 3-variable K-Map.
    
2. Explain the difference between sum-of-products and product-of-sums forms.
    
3. Why do we use Gray code ordering in K-Maps?
    
4. Given don’t-care conditions ( d(x,y,z)=\Sigma(0, 2) ), simplify ( F(x,y,z)=\Sigma(1, 3, 7) ).
    
5. Derive the relationship between number of adjacent cells and literal count.
    

---

## **🪄 Mind Map – K-Map Simplification**

```
         ┌───────────────────────────────┐
         │     Gate-Level Minimization    │
         └────────────┬───────────────────┘
                      │
        ┌─────────────┴───────────────┐
        │                             │
  Map Method (K-Map)            Algebraic Method
        │
 ┌──────┴─────────────┐
 │                    │
SOP (Sum of Products) POS (Product of Sums)
 │                    │
Group 1’s → F        Group 0’s → F′ → F=(F′)′
 │
Don’t-Cares (x) → Simplify Further
```

---

Would you like me to convert these polished notes into a **formatted Word or PDF study guide** (with headings, color-coded highlights, and mind-map image included)?
# Notes
- F2,4,11,13 didn't take terminology  (slide 52) old lecture
- slide 51,52 summaries 
- x' y + y = x + y
- last two rows and last two columns are flipped in 4 variable 
- last two columns in 3 variable  are flipped
