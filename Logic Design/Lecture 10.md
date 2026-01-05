---
course: Logic Design
lecture: Synchronous Sequential Logic – Part 2 (Design Procedures)
date: {{date}}
tags: [logic-design, lecture, university, notes]
---

# 🧠 Logic Design – Synchronous Sequential Logic (Lecture 9)

> [!note] Overview  
> This lecture focuses on the **design methodology** for synchronous sequential circuits, including state diagrams, state tables, flip-flop excitation, and deriving input/output equations for D, JK, and T flip-flops.

---

## 1. Design Procedure for Synchronous Sequential Circuits  
🟡 **Intermediate**

> [!note] Standard 4-Step Design Flow  
1. From word description → **Draw state diagram**  
   - Assign **binary codes** to states  
   - Number of flip-flops = number of state bits  
2. Build the **state table**  
3. Derive **flip-flop input equations** and **output equations**  
4. Draw the **logic diagram**

---

## 2. Example 1 — 2-Bit Counter (0 → 1 → 2 → 3 → 0) Using D Flip-Flops  
🟢 **Basic**

### 2.1 State Assignment  
- Sequence: **00 → 01 → 10 → 11 → 00**  
- Two flip-flops: **A (MSB)**, **B (LSB)**

### 2.2 State Table  
| A(t) | B(t) | A(t+1) | B(t+1) |
|------|------|---------|--------|
| 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |

### 2.3 FF Input Equations  
Since **D FF → Q(t+1) = D**:

- **DA = A ⊕ B**  
- **DB = B'**

---

## 3. Example 1 — 2-Bit Counter Using T Flip-Flops  
🟢 **Basic**

### 3.1 State Table  
Same as previous.

### 3.2 Determine T Inputs  
Recall:  
- **T = 1 → toggle**, **T = 0 → no change**

| A(t)→A(t+1) | TA |  
|-------------|-----|
| 0→0 | 0 |
| 0→1 | 1 |
| 1→1 | 0 |
| 1→0 | 1 |

From transitions:

- **TA = B**  
- **TB = 1**

---

## 4. Example 1 — 2-Bit Counter Using JK Flip-Flops  
🟡 **Intermediate**

Recall JK excitation:

| Q(t) | Q(t+1) | J | K |
|------|---------|---|---|
| 0 | 0 | 0 | X |
| 0 | 1 | 1 | X |
| 1 | 0 | X | 1 |
| 1 | 1 | X | 0 |

### 4.1 Derived Inputs  
From transitions:

- **JA = B**  
- **KA = B**  
- **JB = 1**  
- **KB = 1**

---

## 5. Example 2 — JK FF Design from Given State Diagram  
🟡 **Intermediate**

Assume states encoded as **AB**, input **X**.

### 5.1 Build Excitation Table

| X | A(t) | B(t) | A(t+1) | B(t+1) | JA | KA | JB | KB |
|---|------|------|---------|--------|----|----|----|----|
| 0 | 0 | 0 | 0 | 1 | 0 | 1 | X  | 1 |
| 0 | 0 | 1 | 0 | 0 | 0 | X | 1 | X |
| 0 | 1 | 0 | 1 | 1 | X | 0 | 1 | X |
| 0 | 1 | 1 | 0 | 0 | 1 | X | X | 1 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | X | 0 |
| 1 | 0 | 1 | 1 | 0 | 1 | X | X | 1 |
| 1 | 1 | 0 | 1 | 0 | X | 0 | 0 | X |
| 1 | 1 | 1 | 1 | 1 | X | 0 | X | 0 |

### 5.2 Final Simplified Equations  
- **JA = B**  
- **KA = B X'**  
- **JB = X'**  
- **KB = A ⊕ X**

---

## 6. Example 3 — D FF Design from Given State Diagram  
🟡 **Intermediate**

### 6.1 State Table  
| A(t) | B(t) | X | A(t+1) | B(t+1) | DA | DB | Y |
|------|------|---|---------|--------|----|----|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 0 | 1 | 0 | 0 |

### 6.2 Derived Equations  
- **DA = X B + X A**  
- **DB = A' X**  
- **Y = A X' + B X'**

---

## 7. Notes on Counters  
🟢 **Basic**

> [!note] Terminology  
- **2-bit counter:** Counts 0–3  
- **3-bit counter:** Counts 0–7  
- **n-bit counter:** Counts 0 → 2ⁿ – 1

> [!warning] Missing States  
If the state diagram excludes a binary state, that missing state can transition to **any** defined next state (its next state is “don’t care”).

---

## 8. Continuity with Previous Lectures  
This lecture builds on the foundational model of sequential circuits from Lecture 8 by applying flip-flop behavior to **real design workflows**, focusing on deriving equations and implementing state-machine behavior.

---

## 🧩 Hands-On Practice  
*(No additional examples included, per instruction)*

---

## 📝 Lecture Questions  
The slides did not include explicit instructor questions.

---

## Glossary  
- **State Diagram:** Graph showing state transitions.  
- **State Table:** Tabular form listing present state, next state, inputs, outputs.  
- **Excitation Table:** Table defining flip-flop inputs required for a given transition.  
- **Counter:** Sequential circuit that cycles through a predefined set of states.  
- **Transition Equation:** Expression defining next state logic.

---

## Key Takeaways  
- Sequential design follows a structured 4-step methodology.  
- Flip-flop choice (D, JK, T) influences derivation of input equations.  
- State diagrams and tables drive all subsequent logic design.  
- Counters are a core application of synchronous circuit design.  
- Excitation tables ensure correct FF behavior for each transition.

---

## Quick Review Card  

**Q:** How many flip-flops are required for 6 states?  
**A:** 3 FFs (since 2³ = 8 ≥ 6).

**Q:** What is DA for the D FF design in Example 3?  
**A:** DA = X B + X A.

**Q:** What does TB = 1 imply?  
**A:** Flip-flop B toggles every clock pulse.

**Q:** What makes JK FF suitable for counters?  
**A:** It supports toggle mode when J = K = 1.

**Q:** What determines the number of states?  
**A:** The binary encoding and flip-flop count.

---

## Further Resources  
- Mano & Ciletti – *Digital Design*  
- Roth – *Fundamentals of Logic Design*  
- Brown & Vranesic – *Fundamentals of Digital Logic with VHDL Design*
