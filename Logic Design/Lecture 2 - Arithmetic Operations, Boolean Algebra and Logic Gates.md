# 📚 Lecture 2: Arithmetic Operations, Boolean Algebra and Logic Gates

* **Source:** Digital Logic Design  
* **Instructor:** Mirvat Al-Qutt, Ph.D  
* **Department:** Computer Systems Department, FCIS, Ain Shams University  

---

## Part 1: Arithmetic Operations

Arithmetic operations with numbers in base $r$ follow the same rules as for decimal numbers (base 10). When performing operations in any base, use only the $r$-allowable digits.

### Addition
When the sum of a column is equal to or greater than the base, subtract multiples of the base from the sum, record the remainder, and **carry** to the next column to the left.

#### Binary Addition (Base 2)
Rules:
* $0 + 0 = 0$
* $0 + 1 = 1$
* $1 + 0 = 1$
* $1 + 1 = (2)_{10} = (01)_2$ → result = 0, carry = 1
* $1 + 1 + 1 = (3)_{10} = (11)_2$ → result = 1, carry = 1

#### Addition Examples
|   Operation   | Base |         Example         |     Sum     | Carry Row |
| :-----------: | :--: | :---------------------: | :---------: | :-------: |
| Decimal-style |  10  |      $3758 + 4657$      |    8415     |    111    |
|    Binary     |  2   |    $110111 + 011100$    |  $1010011$  |   1111    |
|  Hexadecimal  |  16  | $7C39_{16} + 37F2_{16}$ | $B42B_{16}$ |    11     |
|     Octal     |  8   |    $6437_8 + 2510_8$    |  $11147_8$  |    11     |

---

### Subtraction
When you can’t subtract in a column, **borrow** from the next higher column.

#### Binary Subtraction
In binary, you borrow **2 units** (because base = 2), add that to the column you are subtracting from.

* **Example:** $110011_2 - 011100_2 = 10111_2$

---

## Part 2: Complements

Two complement systems exist per base-$r$ system:
- **Diminished Radix Complement** ($(r-1)$’s Complement)  
- **Radix Complement** ($r$’s Complement)

### Diminished Radix Complement ($(r-1)$’s Complement)
For an $n$-digit number $N$ in base $r$:
$$(r^n - 1) - N$$

* **1’s Complement (Binary, $r=2$):**  
  Flip all bits (0 → 1, 1 → 0).  
  Example: 1’s complement of $(10110000)_2 = (01001111)_2$.

### Radix Complement ($r$’s Complement)
For an $n$-digit number $N$ in base $r$:
- If $N \ne 0$: $r^n - N$
- If $N = 0$: complement = 0

* **2’s Complement (Binary):**  
  Method 1: Take 1’s complement, then add 1.  
  Method 2: Toggle all bits left of the least significant ‘1’.  
  Example: 2’s complement of $10110000 = 01010000$.

### Subtraction with Complements: $M - N$
| Method | Steps |
| :---: | :--- |
| **1’s Complement** | 1. Compute 1’s complement of $N$. <br>2. Add $M + (\text{1’s comp of }N)$. <br>3. If carry, add it to sum. <br>4. If no carry, result = negative of 1’s complement of sum. |
| **2’s Complement** | 1. Compute 2’s complement of $N$. <br>2. Add $M + (\text{2’s comp of }N)$. <br>3. If carry, discard it. <br>4. If no carry, result = negative of 2’s complement of sum. |

---

## Part 3: Boolean Algebra and Logic Gates

Boolean algebra is essential for simplifying circuits. Simpler circuits cost less and are more reliable.

### Axiomatic Definition & Postulates
Boolean algebra was developed by **George Boole** and formalized via Huntington’s postulates.

- **Domain:** $B = \{0,1\}$
- **Operators:** OR (+), AND (·)

| Postulate | OR Form | AND Form |
| :---: | :---: | :---: |
| Identity | $x + 0 = x$ | $x \cdot 1 = x$ |
| Complement | $x + x' = 1$ | $x \cdot x' = 0$ |
| Commutative | $x + y = y + x$ | $xy = yx$ |
| Associative | $x + (y + z) = (x + y) + z$ | $x(yz) = (xy)z$ |
| Distributive | $x + yz = (x + y)(x + z)$ | $x(y + z) = xy + xz$ |

---

### Theorems & Properties
| Theorem | OR Form | AND Form |
| :---: | :---: | :---: |
| Idempotence | $x + x = x$ | $x \cdot x = x$ |
| Null Elements | $x + 1 = 1$ | $x \cdot 0 = 0$ |
| Involution | $(x')' = x$ | — |
| Absorption | $x + x y = x$ | $x(x + y) = x$ |
| De Morgan’s | $(x + y)' = x' y'$ | $(x y)' = x' + y'$ |
| Consensus | $xy + x'z + yz = xy + x'z$ | $(x + y)(x' + z)(y + z) = (x + y)(x' + z)$ |

#### Operator Precedence
1. Parentheses  
2. NOT ($'$)  
3. AND (·)  
4. OR (+)

---

### Boolean Functions & Logic Gates

A **Boolean function** uses binary variables, OR, AND, NOT, and parentheses.  
It can be expressed in multiple Boolean expressions or circuit (gate) diagrams.  
Each function corresponds to a **unique truth table** of size $2^n$ (for $n$ variables).  
**Simplification** reduces gates and input lines.

Below is a **logic gate reference diagram** you can embed or link:

> ![[Pasted image 20251004195038.png]]  
> Or use these sample diagrams:  
> - [Logic gates with truth tables](https://schoolphysics.co.uk/age16-19/Electronics/Logic%20gates/text/Logic_gates/index.html)   
> - [Various logic gates diagram](https://circuitglobe.com/logic-gates.html)   

Below is the gate summary table:

| Gate Name | Boolean Expression | Output Condition |
| :---: | :---: | :---: |
| **AND** | $F = x \cdot y$ | 1 only when both inputs = 1 |
| **OR** | $F = x + y$ | 1 when either or both inputs = 1 |
| **NOT** | $x'$ | Output is inverse of input |
| **NAND** | $(xy)'$ | 0 only when both inputs = 1 |
| **NOR** | $(x + y)'$ | 1 only when both inputs = 0 |
| **XOR** | $x y' + x' y = x \oplus y$ | 1 when inputs differ |
| **XNOR** | $xy + x'y' = (x \oplus y)'$ | 1 when inputs are same |

---

### Where to Insert Images in Your Obsidian Note

You can embed or link images like this in Obsidian:

![[Pasted image 20251004194947.png]]



# Notes
* Identity element : is element that doesn't affect the mathematical operation