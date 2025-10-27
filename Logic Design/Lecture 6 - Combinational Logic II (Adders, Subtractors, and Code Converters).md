---
course: Logic Design
lecture: Combinational Logic II (Adders, Subtractors, and Code Converters)
date: {{date}}
tags: [logic-design, combinational-logic, adders, subtractors, code-converters, university, notes]
---

> [!summary]
> This lecture extends **Combinational Logic I**, focusing on advanced design applications: **code converters**, **adders**, **subtractors**, and **adder-subtractor circuits**.  
> Students learn structured design steps, Boolean simplification, and the functional implementation of arithmetic circuits.

---

## 🔗 Continuity with Previous Lectures

> [!note]
> *Combinational Logic I* introduced:
> - **Logic gates**, **Boolean laws**, and **minimization** via K-maps.  
> - **Basic combinational circuits** (encoders, decoders, multiplexers).  
> 
> *This lecture builds on those principles* to create **custom arithmetic and conversion circuits** using similar logic simplification techniques.

---

## 🧩 Design Procedure

> [!note]
> General combinational circuit design steps:
> 1. Define **inputs** and **outputs**.
> 2. Construct the **truth table** linking them.
> 3. Simplify each **Boolean function**.
> 4. **Draw** and verify the **logic diagram**.

---

## ⚙️ Design Examples

### Example 1 – Squaring Circuit
> [!example]
> **Goal:** Design a circuit that takes input `X = x₁x₀` and outputs `Y = X²`.

| X₁ | X₀ | Decimal X | Binary Y (X²) | Y₃ | Y₂ | Y₁ | Y₀ |
|----|----|------------|----------------|----|----|----|----|
| 0 | 0 | 0 | 0000 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0001 | 0 | 0 | 0 | 1 |
| 1 | 0 | 2 | 0100 | 0 | 1 | 0 | 0 |
| 1 | 1 | 3 | 1001 | 1 | 0 | 0 | 1 |

> [!note]
> **Simplified Boolean Functions:**
> - $Y_3 = x_1x_0$
> - $Y_2 = x_1x'_0$
> - $Y_1 = 0$
> - $Y_0 = x_0$

> [!tip]
> **Mnemonic:** *Square circuits often reuse input bits in multiplicative patterns (e.g., $Y_3 = x_1x_0$).*

---

### Example 2 – Custom Output Circuit

> [!example]
> **Input:** `N = n₂ n₁ n₀`  
> **Output:** `M = M₂ M₁ M₀`

| n₂ | n₁ | n₀ | M₂ | M₁ | M₀ |
|----|----|----|----|----|----|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 1 | 1 | 0 |
| 1 | 1 | 0 | 1 | 1 | 1 |

> [!note]
> **Simplified Boolean Functions:**
> - $M_2 = n_2 + n_1$
> - $M_1 = n_0 + n_2n_1$
> - $M_0 = n_2n'_0$

---

## 🔢 Code Conversion Circuits

> [!note]
> **Purpose:** Convert one digital code to another to allow compatibility between subsystems.  
> Example: **BCD ↔ Excess-3**, **8-4-−2-−1 ↔ BCD**

### Example 3 – BCD to Excess-3 Code Converter

| BCD (A B C D) | Excess-3 (W X Y Z) |
|----------------|---------------------|
| 0000 | 0011 |
| 0001 | 0100 |
| 0010 | 0101 |
| 0011 | 0110 |
| 0100 | 0111 |
| 0101 | 1000 |
| 0110 | 1001 |
| 0111 | 1010 |
| 1000 | 1011 |
| 1001 | 1100 |

> [!note]
> **Simplified Boolean Equations:**
> - $z = D'$  
> - $y = CD + (C + D)'$  
> - $x = B'(C + D) + B(C + D)'$  
> - $w = A + B(C + D)$

> [!tip]
> **Memory Aid:** “Excess-3 adds +3 (0011) to every BCD value.”

---

### Example 4 – (8,4,−2,−1) Code to BCD Converter

| Input (A B C D) | Output (W X Y Z) |
|-----------------|------------------|
| 0000 | 0000 |
| 0100 | 0100 |
| 0101 | 0011 |
| 0110 | 0010 |
| 0111 | 0001 |
| 1000 | 1000 |
| 1001 | 0111 |
| 1010 | 0110 |
| 1011 | 0101 |
| 1111 | 1001 |

> [!note]
> **Simplified Boolean Functions:**
> - $W = AB + AC'D'$  
> - $X = B'C + B'D + B'C'D'$  
> - $Y = CD' + C'D$  
> - $Z = D$

---

## ➕ Arithmetic Circuits

### Half Adder

> [!note]
> Performs addition of **two bits**.
>
> **Inputs:** x, y  
> **Outputs:** Sum (S), Carry (C)
>
> **Simplified Functions:**
> - $S = x \oplus y$
> - $C = xy$

> [!example]
> | x | y | S | C |
> |---|---|---|---|
> | 0 | 0 | 0 | 0 |
> | 0 | 1 | 1 | 0 |
> | 1 | 0 | 1 | 0 |
> | 1 | 1 | 0 | 1 |

> [!tip]
> **Mnemonic:** *Half = no carry-in.*

---

### Full Adder

> [!note]
> Adds **three bits**: A, B, and Carry-in (Cₙ).

**Equations:**
- $S = A \oplus B \oplus C_{in}$
- $C_{out} = AB + C_{in}(A \oplus B)$

> [!example]
> **Implementation:** Two half adders + one OR gate.

> [!tip]
> **Mnemonic:** *Full = includes carry-in.*

---

### 4-bit Binary Adder

> [!note]
> Connects 4 full adders in series.  
> Each carry-out becomes next stage’s carry-in.

> [!example]
> A = 1011  
> B = 0011  
> → Result = 1110  
> (Carry propagates across stages)

---

### 4-bit Binary Subtractor

> [!note]
> Subtraction implemented via 2’s complement addition.

$$
A - B = A + (\overline{B} + 1)
$$

---

### 4-bit Adder-Subtractor

> [!example]
> **Control signal M:**  
> - M = 0 → Addition  
> - M = 1 → Subtraction

| Operation | M | Function |
|------------|---|-----------|
| Add | 0 | A + B |
| Subtract | 1 | A + B' + 1 |

> [!note]
> Implemented using **XOR gates** to conditionally invert B bits.

> [!warning]
> **Overflow:** Occurs when result exceeds n-bit capacity.

> [!tip]
> XOR properties:  
> - $B \oplus 0 = B$  
> - $B \oplus 1 = B'$  

---

## 🧠 Concept Hierarchy Diagram

```mermaid
mindmap
  root((Combinational Logic II))
    Design Procedure
      Truth Tables
      Boolean Simplification
    Code Converters
      BCD ↔ Excess-3
      (8,4,-2,-1) ↔ BCD
    Arithmetic Circuits
      Half Adder
      Full Adder
      4-bit Adder
      Subtractor
      Adder-Subtractor
```

---

## 🧩 Hands-On Practice

1. Design a circuit that outputs $Y = A^2$ for A = 00–11.
    
2. Implement BCD → Excess-3 converter using two-level NAND logic.
    
3. Construct a 4-bit adder-subtractor using XOR gates and verify overflow.
    

---

## 📚 Glossary

|Term|Definition|
|---|---|
|**Combinational Circuit**|Output depends only on present input values.|
|**Code Converter**|Circuit that translates one binary code into another.|
|**Half Adder**|Adds two bits, no carry input.|
|**Full Adder**|Adds three bits including carry input.|
|**Adder-Subtractor**|Dual-purpose circuit using XOR control.|
|**Overflow**|Error when arithmetic result exceeds n-bit range.|

---

## 🔑 Key Takeaways

- Code converters ensure system compatibility.
    
- Arithmetic operations can be expressed with basic Boolean logic.
    
- XOR gates enable both addition and subtraction control.
    
- Simplified Boolean expressions reduce gate count.
    
- Overflow must be handled in fixed-width binary operations.
    

---

## 🧾 Quick Review Card

> [!question] What does a half adder compute?  
> Sum and carry of two input bits.

> [!question] How is subtraction performed in binary circuits?  
> By adding the 2’s complement of the subtrahend.

> [!question] What role does XOR play in adder-subtractor design?  
> It conditionally inverts input bits based on the control signal.

> [!question] Define overflow in digital arithmetic.  
> Occurs when the result exceeds the range of representable bits.

> [!question] What is the key feature of code converters?  
> Translating between incompatible binary encodings.

---

## 📘 Further Resources

- **M. Morris Mano**, _Digital Design_, 6th Edition.
    
- **Floyd**, _Digital Fundamentals_.
    
- YouTube: _“Half Adder and Full Adder Explained”_ (Neso Academy).
    
- Simulation: [Falstad Logic Simulator](https://falstad.com/circuit/)
    

---