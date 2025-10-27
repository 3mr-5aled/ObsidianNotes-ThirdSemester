# DLD – Boolean Algebra and Logic Gates (Lecture 3, 10/10/2025)

## Complement of a Function

The **complement of a function** $F$, denoted as $F'$, is found by **interchanging the 0s and 1s** in the function's output values.

A generalized method for finding the complement, based on **De Morgan’s theorem**, is to **interchange AND and OR operators** and **complement each literal**.

- If $F = A + B + C + \dots$, then $F' = A'B'C'\dots$
- If $F = ABC\dots$, then $F' = A' + B' + C' + \dots$

---

> [!example] **Finding the Complement**

1️⃣ **Find the complement of** $F_1 = x'yz' + x'y'z$

$$
\begin{aligned}
F_1' &= (x'yz' + x'y'z)' \\
     &= (x'yz')' \cdot (x'y'z)' \\
     &= (x + y' + z)(x + y + z')
\end{aligned}
$$

---

2️⃣ **Find the complement of** $F_2 = x(y'z' + yz)$

$$
\begin{aligned}
F_2' &= [x(y'z' + yz)]' \\
     &= x' + (y'z' + yz)' \\
     &= x' + (y'z')' \cdot (yz)' \\
     &= x' + (y + z)(y' + z') \\
     &= x' + yz' + y'z
\end{aligned}
$$

---

## Canonical and Standard Forms

Boolean functions can be expressed in several forms.  
The **canonical forms** are a unique representation of the function.

---

### **Minterms**

> [!info] **Definition: Minterm**  
> A **minterm**, or **standard product**, is an AND term that contains all variables of the function, either in their normal or complemented form.  
> For $n$ variables, there are $2^n$ possible minterms.

- A minterm evaluates to **1** for only one specific combination of variable values.  
- The designation $m_j$ is used, where $j$ is the decimal equivalent of the binary combination for which the minterm is 1.

---

#### **Minterms for Three Variables ($x, y, z$):**

| x | y | z | Term | Designation |
|---|---|---|---|---|
| 0 | 0 | 0 | $x'y'z'$ | $m_0$ |
| 0 | 0 | 1 | $x'y'z$ | $m_1$ |
| 0 | 1 | 0 | $x'yz'$ | $m_2$ |
| 0 | 1 | 1 | $x'yz$ | $m_3$ |
| 1 | 0 | 0 | $xy'z'$ | $m_4$ |
| 1 | 0 | 1 | $xy'z$ | $m_5$ |
| 1 | 1 | 0 | $xyz'$ | $m_6$ |
| 1 | 1 | 1 | $xyz$ | $m_7$ |

A Boolean function can be expressed algebraically as a **sum of minterms**.  
This is the **Sum of Products (SOP)** canonical form — the function equals the **OR** of all minterms corresponding to `1` in the truth table.

---

> [!example] **Sum of Minterms**

Given the function $F(x, y, z)$ which is `1` for binary combinations **001**, **100**, and **111**:

- The corresponding minterms are $m_1, m_4, m_7$
- The function is $F = x'y'z + xy'z' + xyz$
- Compact notation: $F(x, y, z) = \Sigma(1, 4, 7)$

---

### **Maxterms**

> [!info] **Definition: Maxterm**  
> A **maxterm**, or **standard sum**, is an OR term that contains all variables of the function, either in their normal or complemented form.  
> For $n$ variables, there are $2^n$ possible maxterms.

- A maxterm evaluates to **0** for only one specific combination of variable values.  
- Each maxterm is the **complement** of its corresponding minterm ($M_j = m_j'$).

---

#### **Maxterms for Three Variables ($x, y, z$):**

| x | y | z | Term | Designation |
|---|---|---|---|---|
| 0 | 0 | 0 | $x + y + z$ | $M_0$ |
| 0 | 0 | 1 | $x + y + z'$ | $M_1$ |
| 0 | 1 | 0 | $x + y' + z$ | $M_2$ |
| 0 | 1 | 1 | $x + y' + z'$ | $M_3$ |
| 1 | 0 | 0 | $x' + y + z$ | $M_4$ |
| 1 | 0 | 1 | $x' + y + z'$ | $M_5$ |
| 1 | 1 | 0 | $x' + y' + z$ | $M_6$ |
| 1 | 1 | 1 | $x' + y' + z'$ | $M_7$ |

A Boolean function can be expressed as a **product of maxterms**.  
This is the **Product of Sums (POS)** canonical form — the function equals the **AND** of all maxterms corresponding to `0` in the truth table.

---

> [!example] **Product of Maxterms**

Given $F(x, y, z) = \Sigma(1, 4, 7)$,  
the function is `0` for minterms $m_0, m_2, m_3, m_5, m_6$.

- Corresponding maxterms: $M_0, M_2, M_3, M_5, M_6$
- Function: $F = (x + y + z)(x + y' + z)(x + y' + z')(x' + y + z')(x' + y' + z)$
- Compact form: $F(x, y, z) = \Pi(0, 2, 3, 5, 6)$

---

### **Conversion Between Canonical Forms**

> [!tip] **Conversion Rule**  
> To convert between **Sum of Minterms** and **Product of Maxterms**,  
> interchange the symbols $\Sigma$ and $\Pi$ and list the numbers **missing** from the original form.

**Example:**

$$
F(A, B, C) = \Sigma(1, 4, 5, 6, 7)
$$

- Missing minterms: 0, 2, 3  
- Therefore:
$$
F(A, B, C) = \Pi(0, 2, 3)
$$

The **complement** of a function can be found easily from its canonical form:

$$
F'(A, B, C) = \Sigma(\text{missing minterms})
$$

So if $F(A, B, C) = \Sigma(1, 4, 5, 6, 7)$,  
then $F'(A, B, C) = \Sigma(0, 2, 3)$.

---
![[Pasted image 20251010194438.png]]

## Standard vs. Canonical Forms

| **Form**      | **Description**                                                                                        | **Example**                 |
| ------------- | ------------------------------------------------------------------------------------------------------ | --------------------------- |
| **Canonical** | Each term (minterm or maxterm) must contain **all variables** of the function.                         | $F_1 = xy'z + xyz' + x'yz'$ |
| **Standard**  | Terms may contain one, two, or any number of literals. Not all variables must be present in each term. | $F_1 = y' + xy + x'yz'$     |

A non-standard function can be converted to a **standard form** using Boolean algebra (e.g., distributive law).  
Standard forms are preferred because they simplify circuit implementation.

---

### **Two-Level Implementation**

Standard forms lead directly to **two-level logic gate implementations**:

- **SOP:** AND gates followed by an OR gate  
- **POS:** OR gates followed by an AND gate  

---
![[Pasted image 20251010205233.png]]
## 🧠 **Key Takeaways**

- **Canonical Forms** uniquely represent Boolean functions:
  - **SOP ($\Sigma$):** OR of minterms (1’s in truth table)
  - **POS ($\Pi$):** AND of maxterms (0’s in truth table)
- **Minterm ($m_j$):** AND term that’s 1 for one input combination.
- **Maxterm ($M_j$):** OR term that’s 0 for one input combination.  
  $M_j = m_j'$
- **Standard Forms** (SOP, POS) omit variables when not needed.
- **Standard forms** → direct **two-level logic implementations.**

![[Pasted image 20251010205251.png]]