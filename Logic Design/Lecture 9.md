---
course: Logic Design
lecture: Synchronous Sequential Logic – Part 1
date: {{date}}
tags: [logic-design, lecture, university, notes]
---

# 🧠 Logic Design – Synchronous Sequential Logic (Lecture 8)

> [!note] Overview  
> Introduction to **synchronous sequential circuits**, their core components, and the operation of **latches** and **flip-flops**. Establishes foundational concepts for analyzing and designing clocked sequential logic systems.

---

## 1. Sequential Circuits  
🟢 **Basic**

> [!note] Definition  
> **Sequential circuits** are digital systems whose outputs depend on:  
> • **Present inputs**  
> • **Stored state** (i.e., past inputs captured in storage elements)

### 1.1 Combinational vs Sequential Systems  
- **Combinational circuits:** Output depends only on current input values.  
- **Sequential circuits:** Output depends on both input and **state Q(t)**; next state is **Q(t+1)**.

### 1.2 General Sequential Circuit Structure  
- **External Inputs**  
- **Storage Element (latch/flip-flop)**  
- **Combinational Logic**  
- **External Outputs**

---

## 2. Types of Sequential Circuits  
🟢 **Basic**

### 2.1 Synchronous Sequential Circuits  
> [!note] Key Idea  
> A synchronous sequential circuit updates its state **only at discrete time instants**, controlled by a **clock signal**.

- Clock = periodic pulses.  
- Storage elements change **only at clock edges or levels**.  
- Most modern digital designs use synchronous circuits.  
- Example: A binary adder that stores its output on each clock pulse.

### 2.2 Asynchronous Sequential Circuits  
- State changes occur **whenever inputs change**.  
- Typically use **time-delay elements**.  
- Less common in practice due to instability and hazards.

> [!warning]  
> Asynchronous circuits are difficult to design and analyze due to race conditions and hazards.

---

## 3. Storage Elements  
🟡 **Intermediate**

Two broad categories:

### 3.1 Latches  
- Operate with **signal levels**.  
- Transparent while enable = HIGH.  
- Simpler but prone to timing problems.

### 3.2 Flip-Flops  
- Operate on **clock transitions** (edge-triggered).  
- More robust and used in synchronous systems.

> [!tip]  
> Latch = level-triggered  
> Flip-Flop = edge-triggered

---

## 4. SR Latch  
🟢 **Basic**

### 4.1 SR Latch Using NOR Gates  
- Inputs: **S (Set)**, **R (Reset)**  
- Outputs: **Q**, **Q'**

#### Behavior Summary  
| S | R | Action        | Q(next) |
|---|---|---------------|---------|
| 0 | 0 | No change     | Q       |
| 0 | 1 | Reset         | 0       |
| 1 | 0 | Set           | 1       |
| 1 | 1 | Invalid       | Undefined |

> [!warning]  
> **S = 1 and R = 1** simultaneously is invalid because Q and Q' both become 0, violating complementarity.

### 4.2 SR Latch Using NAND Gates  
- Inputs typically active-LOW.  
- Invalid state occurs when **S = 0 and R = 0**.

---

## 5. SR Latch with Control Input  
🟢 **Basic**

- Adds an **enable** input allowing activation only when control = 1.  
- Used to gate data during specific intervals.

---

## 6. D Latch  
🟢 **Basic**

> [!note] Definition  
> A **D (Data) latch** removes invalid states of the SR latch by enforcing **R = D'** and **S = D**.

- Transparent: Output follows D while clock/enable = HIGH.  
- Holds value when clock/enable = LOW.

---

## 7. D Flip-Flop  
🟡 **Intermediate**

- Edge-triggered version of D latch.  
- Captures data on clock rising or falling edge.  
- Variants include **asynchronous reset**.

### 7.1 D Flip-Flop with Asynchronous Reset  
- Reset forces Q = 0 immediately, independent of the clock.  
- Common in hardware initialization.

---

## 8. JK Flip-Flop  
🟡 **Intermediate**

> [!note] Operation Summary  
| J | K | Operation |
|---|---|-----------|
| 0 | 0 | No change |
| 0 | 1 | Reset     |
| 1 | 0 | Set       |
| 1 | 1 | Toggle    |

- Eliminates the invalid state of SR FF.  
- Used in counters and control circuits.

---

## 9. T (Toggle) Flip-Flop  
🟢 **Basic**

> [!note] Behavior  
| T | Q(t) | Q(t+1) |
|---|------|--------|
| 0 | Q    | Q      |
| 1 | Q    | Q'     |

- Simplest flip-flop.  
- When T = 1 → toggles output each clock cycle.  
- Widely used in counters.

---

## 10. Characteristic Tables  
🟡 **Intermediate**

Characteristic equations describe **next-state logic**.

### 10.1 D Flip-Flop  
- **Q(t+1) = D**

### 10.2 JK Flip-Flop  
- **Q(t+1) = JQ' + K'Q**

### 10.3 T Flip-Flop  
- **Q(t+1) = T ⊕ Q**

---

## 11. Analysis of Clocked Sequential Circuits  
🟡 **Intermediate**

Sequential circuit analysis steps:

1. **Identify state variables** (flip-flops A, B, …)  
2. **Extract flip-flop input equations**  
3. **Build the state table**:
   - Present State  
   - Inputs  
   - FF Inputs  
   - Next State  
4. **Derive output equations**

> [!note]  
> State Diagram is a graphical representation of the state table.

---

## 12. Continuity with Previous Lectures  
This lecture builds directly on combinational logic concepts by introducing **state**, **memory**, and **time-dependence**, forming the foundation of sequential circuit design and analysis.

---

## 🧩 Hands-On Practice  
*(No additional examples included, per instruction)*

---

## 📝 Lecture Questions  
The slides did not contain explicit instructor questions.

---

## Glossary  
- **Sequential Circuit:** Circuit whose output depends on past inputs.  
- **Latch:** Level-triggered storage element.  
- **Flip-Flop:** Edge-triggered storage element.  
- **State:** Stored information representing system history.  
- **Characteristic Table:** Defines relation between inputs and next state.

---

## Key Takeaways  
- Sequential circuits use memory to store past information.  
- Latches are level-triggered; flip-flops are edge-triggered.  
- SR, D, JK, and T flip-flops form the core building blocks.  
- Characteristic equations define FF behavior precisely.  
- Clock-driven synchronous circuits dominate real-world systems.

---

## Quick Review Card  

**Q:** What distinguishes synchronous sequential circuits?  
**A:** State updates occur only on clock events.

**Q:** Why is the SR latch’s (1,1) input invalid?  
**A:** Outputs violate complementarity (both become 0).

**Q:** What is the characteristic equation of a T FF?  
**A:** Q(t+1) = T ⊕ Q.

**Q:** What does a D FF do on a clock edge?  
**A:** Captures the value of D.

**Q:** Which FF supports toggle operation inherently?  
**A:** T flip-flop.

---

## Further Resources  
- Mano & Ciletti – *Digital Design*  
- Floyd – *Digital Fundamentals*  
- Roth – *Fundamentals of Logic Design*  
