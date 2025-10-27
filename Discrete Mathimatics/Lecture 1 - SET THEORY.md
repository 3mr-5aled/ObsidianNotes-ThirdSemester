**Table of Contents**
- [[#Grading]]
- [[#Course Outline]]
- [[#Chapter 1 – Basic Structures]]
- [[#Notes ⭐]]
---
# Discrete Mathematics – Lecture Notes  
*Dr. Wael Fathy Abdelhamid*  
*Textbook: Kenneth H. Rosen, Discrete Mathematics and Its Applications, 7th Edition (2011)*  

---

## Grading
- Attendance and Assignments: **20 Marks**  
- Midterm (Week 7): **20 Marks**  
- Final Exam (Week 16): **60 Marks**  
**Total: 100 Marks**

---

## Course Outline
- **Weeks 1–3**: Basic Structures – Sets, Functions, Sequences, Sums, Matrices  
- **Weeks 4–6**: Logic and Proofs  
- **Week 7**: Midterm Revision  
- **Week 8**: Midterm Exam  
- **Weeks 9–10**: Induction and Recursion  
- **Weeks 11–12**: Relations  
- **Week 13**: Number Theory  
- **Week 14**: Graph Theory  
- **Week 15**: Final Revision  
- **Week 16**: Final Exam  

---

# Chapter 1 – Basic Structures
## Section 2.1 – Set Theory

### Section Summary
1. Definition
2. Describing sets (notation)  
3. Equality of sets  
4. Subsets and proper subsets  
5. Cartesian product  
6. Power set  
7. Cardinality  
---
## Sets

- ⭐ A set is an **unordered collection** of **unique** objects.
- The objects in a set are called its **elements**, or **members**.
- A set is said to contain its *elements*.
- The order in which elements occur in sets is *irrelevant*.
    - Example: `{a, b, c, d, e} = {c, e, a, d, b}`
- We ignore any duplicates.
    - Example: `{a, a, a, b, c} = {a, b, c}` are equivalent.

---
## The Elements of a Set

- ⭐ We normally use **uppercase letters** ~={red}(A, B , C)=~ to represent the **names of sets**, and *lowercase letters* ~={red}( a, b, c )=~ to represent their *elements*.
- To denote that `a` is an **element** of *set* `S` we write:
    - `a ∈ S`
- To denote that `a` is not an **element** of *set* `S` we write:
    - `a ∉ S`

---
### Set Notation
Two ways to describe sets:  
1. **Listing Elements**  
   - Example: Vowels → `V = {a, e, i, o, u}`  
   - Example with ellipsis → `H = {1, 2, 3, …, 100}`  
2. **Set Builder Notation**  
   - `S = {x | x is the square of an integer}`  
   - Common sets:  
     - `N = {0, 1, 2, 3, …}`   set of natural numbers
     - `Z = {…, -2, -1, 0, 1, 2, …}`  set of integers
     - `Z+ = {1, 2, 3, …}`  set of positive integers
     - `Q = {p/q | p ∈ Z, q ∈ Z, q ≠ 0}`   set of rational numbers
     -  `Q+ = ` set of positive rational numbers
     - `R` = Real numbers  
	  
	- ⭐ 0 ∉ Z+, Z-                                       
    - ⭐ 0 ∈ N *( natural numbers )*          
     

---

### Equality of Sets
- Two sets are equal if they have the same elements.  
- Empty set (null set): `∅` or `{}`  
  - `A = {∅, a}` has 2 elements  
  - `B = {∅}` has 1 element   ⭐
  - `C = ∅` has 0 elements  

- ⭐ Consider sets A and B. Then A = B (A and B are equal) if and only if:
    - $∀x ((x ∈ A) ↔ (x ∈ B))$ 

---

### WHAT CAN CONSTITUTE A SET?  :LiArrowBigRight:  Venn Diagrams
- Rectangle → universal set  
- Circles → sets  
- Points → elements  
![[Pasted image 20250927214857.png]]
---

### Subsets
- `A ⊆ B` ⇔ every element of A is in B  
- Every set is a subset of itself: `A ⊆ A`  
- Empty set is a subset of every set  
* ⭐Proper Subsets
	
![[Pasted image 20250927215626.png]]
---
## Subset

- The empty set, , is a subset of every other set.
- For example, if set `S = {a, b}`, then it has 4 subsets: `{{a}, {b}, {a, b}, ∅}`.

---

## Properties of Sets
- One way to show that two sets are equal is to show that each set is a subset of the other.
- Every nonempty set `S` must have at least two subsets: $∅$ and `S`.
- **Theorem**: For every set S:
    - $∅ ⊆ S$
    - $S ⊆ S$

---

## The Cardinality of a Set (ORDER)
- Given a set `S`, and $n ∈ N$ (n is an element of the set of natural numbers), if there are exactly `n` distinct elements in `S`, then:
    - `S` is a **finite set**.
    - `n` is the **cardinality** of `S`.
- The cardinality of `S` is represented by $|S|$.
- The cardinality is also called the **ORDER** of the set. #EXAM
---

## Powerset
- The **powerset** of `S` is the set of all subsets of `S`.
- The powerset of `S` is represented by $P(S)$.
- The number of elements in the powerset is $2^{|S|}$.
- **Example 1**: If `S = {a, b}`, then:
    - $P(S) = \{\{a\}, \{b\}, \{a, b\}, ∅\}$
    - The cardinality $|S|$ is 2, so the cardinality of the powerset is $|P(S)| = 2^2 = 4$.
- **Example 2**: The powerset of the set containing only the empty set:
    - $P(\{∅\}) = \{∅, \{∅\}\}$

---

## Cartesian Product
- The **Cartesian product**, or cross product, of two sets is the set of ordered pairs of elements from the two sets.
- The cross product of sets `A` and `B` is written as $A × B$.
- **Example**:
    - Given set `A = {a, b}` and set `Y = {x, y}`
    - The Cartesian product is $A × Y = \{(a,x), (a,y), (b,x), (b,y)\}$


---
## Notes ⭐
**Relationships**
- **Elements** & **Sets**: (∈ / ∉)
- **Sets** & **Sets**: (⊆ / ⊄)

**Properties**
- A set is a subset of itself: `A ⊆ A`
- The empty set is a subset of any set: `∅ ⊆ Any set`

**Empty Set (∅) Examples**
- ` {∅} ≠ ∅`
- `∅ ∈ {∅,1,2}` and `∅ ⊆ {∅,1,2}`
- `∅ ⊆ {1,2}`
- ` {∅} ⊄ {1,2}`

![[lecture 1.pdf]]



#EXAM
- Proof by Mathematical Induction [Final Exam]
- Topics: Sets, Logic, Relations, Math Induction
