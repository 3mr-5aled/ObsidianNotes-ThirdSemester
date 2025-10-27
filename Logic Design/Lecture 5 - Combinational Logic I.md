# ⚙️ Logic Design – Lecture 5: Combinational Logic I

> [!overview]
> This lecture explains **Combinational Logic Circuits**, focusing on **universal gates (NAND and NOR)**, **exclusive logic functions (XOR and XNOR)**, and their applications in **parity generation and checking**. It also covers the **analysis procedure** for deriving Boolean functions and truth tables from logic diagrams.

---

## 1. Universal Gates

### 1.1 NAND Gate
![[Pasted image 20251020235835.png]]
- **NAND** is a **universal gate** — any digital system can be implemented using NAND gates only.
- **Definition:**  
  $Y = (AB)' = \overline{A \cdot B}$
- **DeMorgan’s Theorem:**  
  $(xyz)' = x' + y' + z'$


AND
![[Pasted image 20251021000007.png]]
OR
![[Pasted image 20251020235948.png]]
Inverter
![[Pasted image 20251020235957.png]]

Conclusion
![[Pasted image 20251021000031.png]]
NAND and invert-OR are same value
![[Pasted image 20251021000108.png]]


> [!example]
> Implementing $F = AB + CD$ using NAND gates:
> $$
> F = ((AB)' (CD)')' = AB + CD
> $$

#### Two-Level NAND–Only Implementation Procedure
1. Simplify the function into **Sum of Products (SOP)**.  
2. Use **NAND gates** for each product term (first level).  
3. Use a **final NAND** for the sum term (second level).  
4. Single literals require **inverters** at the first level.

![[Pasted image 20251021000220.png]]

### Multilevel NAND Gate
![[Pasted image 20251021000325.png]]
NAND-Only Implementation
![[Pasted image 20251021000400.png]]
### 1.2 NOR Gate
![[Pasted image 20251021000449.png]]
- **NOR** is also a **universal gate** — can implement any logic function.
    
- **Definition:**  
    $Y = (A + B)' = \overline{A + B}$
    
- **DeMorgan’s Theorem:**  
    $(x + y + z)' = x'y'z'$
    

OR
![[Pasted image 20251021000510.png]]
AND
![[Pasted image 20251021000518.png]]
Inverter
![[Pasted image 20251021000535.png]]
Conclusion
![[Pasted image 20251021000552.png]]
NOR & Invert-AND are the same
![[Pasted image 20251021000629.png]]

NOR-Only Implementation
![[Pasted image 20251021000712.png]]

> [!example]  
> Implementing $F = (A + B)(C + D)E$ using NOR gates.

> [!tip]  
> To convert **AND-OR** logic to **NOR-NOR**:
> 
> - Replace **AND** with **NOR + inverter**
>     
> - Replace **OR** with **NOR**
>     

---

## 2. Exclusive Logic Functions

### 2.1 Exclusive-OR (XOR)

| **Property** | **Expression** | **Description** |
|---------------|----------------|-----------------|
| **Definition (XOR)** | $x \oplus y = xy' + x'y$ | Output is 1 when inputs differ |
| **Definition (XNOR)** | $(x \oplus y)' = xy + x'y'$ | Output is 1 when inputs are equal |
| **Identity 1** | $x \oplus x = 0$ | A variable XORed with itself is always 0 |
| **Identity 2** | $x \oplus x' = 1$ | A variable XORed with its complement is always 1 |
| **Identity 3** | $x \oplus 0 = x$ | XOR with 0 yields the variable itself |
| **Identity 4** | $x \oplus 1 = x'$ | XOR with 1 yields the complement |
| **Complement Relation 1** | $x \oplus y' = (x \oplus y)'$ | XOR with complement of y equals complement of XOR |
| **Complement Relation 2** | $x' \oplus y = (x \oplus y)'$ | XOR with complement of x equals complement of XOR |
| **Commutative Law** | $x \oplus y = y \oplus x$ | Order of operands does not affect result |
| **Associative Law** | $(x \oplus y) \oplus z = x \oplus (y \oplus z) = x \oplus y \oplus z$ | Grouping does not affect result |

Exclusive-OR Implementation
![[Pasted image 20251021000920.png]]
### 2.2 Exclusive-NOR (XNOR)

- **Definition:**  
    $(x \oplus y)' = xy + x'y'$
    

> [!note]  
> XOR is called an **odd function** (output = 1 for odd number of 1s).  
> XNOR is an **even function** (output = 1 for even number of 1s).
![[Pasted image 20251021000942.png]]
#### Example

$$  
A \oplus B \oplus C = \Sigma(1,2,4,7)  
$$
Diagram of XOR, XNOR
![[Pasted image 20251021001012.png]]

Four-variable Exclusive-OR function
![[Pasted image 20251021001050.png]]

---

## 3. Parity Generation and Checking

### 3.1 Concept

Used in **error detection** to ensure data integrity.

- **Even Parity Generator:**  
    $$  
    P = x \oplus y \oplus z  
    $$
    
- **Parity Check:**  
    $$  
    C = x \oplus y \oplus z \oplus P  
    $$
    
    - If $C=1$: one-bit error (odd number of bit errors)
        
    - If $C=0$: correct or even number of bit errors
        
![[Pasted image 20251021001421.png]]
### 3-bit even parity generator
![[Pasted image 20251021001146.png]]
![[Pasted image 20251021001304.png]]
![[Pasted image 20251021001312.png]]
### 4-bit even parity generator
![[Pasted image 20251021001233.png]]
![[Pasted image 20251021001327.png]]
![[Pasted image 20251021001335.png]]

> [!example]  
> For **even parity** with bits `1 0 1`:
> 
> - $P = 1 \oplus 0 \oplus 1 = 0$
>     
> - Transmitted: `1 0 1 0`
>     
> - If received correctly: $C = 0$
>     

---

## 4. Combinational vs Sequential Logic
![[Pasted image 20251021001437.png]]

|Type|Components|Output Depends On|
|---|---|---|
|**Combinational**|Logic gates only|Current inputs|
|**Sequential**|Logic gates + storage elements|Current + past inputs|

### Combinational Logic

- For **n input variables**, there are **$2^n$ possible binary input combinations**.  
- Each combination produces **one unique output value**.  
- A combinational circuit can be described using a **truth table** or **m Boolean functions**, where each output is expressed in terms of the **n input variables**.


> [!note]  
> A **combinational circuit** transforms binary input data directly into output data using logic gates.

---

## 5. Analysis Procedure
- **Analysis** is the reverse of **design** — it determines the **Boolean function** a given circuit implements.  
- Begin with a **logic diagram** and verify that it is **combinational** (no feedback or memory elements).  
- Derive the **Boolean expressions** or **truth table** for the outputs.
### 5.1 Steps to Analyze a Combinational Circuit

1. Verify the circuit has **no feedback** (not sequential).
    
2. **Label outputs** of gates that depend on input variables. (T1, T2 , T3)
    
3. Determine **Boolean functions** for intermediate gates.
    
4. Substitute step-by-step until the **final output function** is derived.
    
5. Optionally, construct the **truth table**.
    
![[Pasted image 20251021001916.png]]
![[Pasted image 20251021001925.png]]

---
## 🧩 Glossary

| Term                      | Definition                                                               |
| ------------------------- | ------------------------------------------------------------------------ |
| **Universal Gate**        | A logic gate that can implement all Boolean functions (e.g., NAND, NOR). |
| **Exclusive-OR (XOR)**    | Outputs 1 when the number of 1s in inputs is odd.                        |
| **Exclusive-NOR (XNOR)**  | Outputs 1 when the number of 1s in inputs is even.                       |
| **Parity Bit**            | Bit added to detect errors in transmitted data.                          |
| **Combinational Circuit** | Output depends solely on current input values.                           |

---

## 🚀 Key Takeaways

- NAND and NOR gates can replicate **any** logic circuit.
    
- XOR/XNOR handle **parity checking** and **error detection**.
    
- **Combinational logic** has no memory; **sequential logic** includes state.
    
- Circuit analysis involves **backward tracing** and **Boolean simplification**.
    

---

## 📚 Further Resources

- _M. Morris Mano_, **Digital Design**, 6th Edition.
    
- _Floyd & Buchla_, **Digital Fundamentals**.
    
- Online NAND/NOR circuit simulator: [falstad.com/circuit](https://falstad.com/circuit)