---
course: Discrete Mathematics
lecture: Lecture 6 – Proving Theorems
date: {{date}}
tags: [discrete-math, proofs, logic, lecture, university, notes]
---
# 🧠 Discrete Mathematics – Proving Theorems

> [!note]
> This lecture explains **methods of mathematical proof** including **Direct Proof**, **Proof by Contraposition**, **Proof by Contradiction**, and special cases like **Trivial** and **Vacuous Proofs**.  
> You’ll learn how to logically establish the truth of a statement and identify which method to use.

---

## 🧩 Continuity with Previous Lectures
This lecture builds on:
- **Logical equivalences** and **rules of inference** (Lecture 5)
- Used here to justify reasoning steps in proofs.

---

## 1. Introduction to Theorem Proving
A **theorem** is a statement that can be proven true using logical reasoning.  
To prove **p → q**, we show that whenever **p** is true, **q** must also be true.

🟢 **Basic Idea:**  
To prove a conditional statement, assume **p** is true and logically derive **q**.

> [!tip]
> 🔑 Mnemonic: “**Assume p → show q**”  
> دا معناه إنك تبدأ من الفرض (p) وتستخدم قوانين المنطق عشان توصل للاستنتاج (q).

---

## 2. Direct Proof

### Definition
> [!note]
> A **Direct Proof** of “if p → q” assumes **p is true**, and through logical reasoning, deduces that **q must be true**.

**Steps:**
1. Assume **p** is true.  
2. Use **definitions**, **axioms**, and **rules of inference**.  
3. Show that **q** logically follows.

🟢 Difficulty: Basic

---

### Example 1  
> [!example]
> **Statement:** If *n* is an odd integer, then *n²* is odd.

**Proof:**
Let $n = 2k + 1$, where *k* is an integer.  
$n² = (2k + 1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1$  
Thus, $n²$ is odd.

**بالعربي:** لو n عدد فردي، فـ n² برضه فردي لإن ناتج تربيع أي عدد فردي بيكون فيه +1 بعد مضاعف 2.

---

### Example 2  
> [!example]
> **Statement:** If *m* and *n* are perfect squares, then *mn* is a perfect square.

Let $m = s²$ and $n = t²$, where *s*, *t* ∈ ℤ.  
Then $mn = s²t² = (st)²$.  
Hence, *mn* is a perfect square.

---

## 3. Proof by Contraposition

> [!note]
> Instead of proving **p → q**, we prove **¬q → ¬p**, since they are logically equivalent.

🟡 Difficulty: Intermediate

**Idea:**  
If proving *p → q* directly is hard, assume *q* is false and show *p* must be false too.

**Formula:**  
$p \to q \equiv \neg q \to \neg p$

---

### Example 3  
> [!example]
> **Statement:** If 3n + 2 is odd, then n is odd.

**Contrapositive:** If n is even, then 3n + 2 is even.  
Assume $n = 2k$.  
Then $3n + 2 = 6k + 2 = 2(3k + 1)$ → even.  
Hence proved.

**بالعربي:** لما تبدأ بالعكس (n even) وتوصل إن الناتج even، يبقى الأصل صحيح.

---

### Example 4  
> [!example]
> **Statement:** If n = ab (positive integers), then $a ≤ √n ≤ b$.

Prove by contraposition: assume $a > √n$ and $b > √n$ → leads to contradiction.  
(Using multiplication and De Morgan’s Law.)

---

> [!tip]
> Mnemonic: “**Flip and Negate**”  
> لما تستخدم contraposition، بدّل p و q و اعكس الإشارة.

---

## 4. Proof by Contradiction

> [!note]
> To prove *p*, assume **¬p** and reach a **contradiction** (r ∧ ¬r).

🔴 Difficulty: Advanced

**Logic:**
$$
\neg p \rightarrow (r \land \neg r)
$$  
Since a contradiction is impossible, **p must be true**.

---

### Example 7  
> [!example]
> **Statement:** √2 is irrational.

**Proof:**
Assume √2 is rational → √2 = a/b, with integers a, b having no common factors.  
Then $2 = a² / b²$ → $a² = 2b²$.  
So a² even → a even → a = 2c → $b² = 2c²$ → b even.  
Thus a and b are both even → have common factor → contradiction.  
Hence √2 is irrational.

**بالعربي:** فرضنا إن الجذر التربيعي لـ2 نسبي، وطلع إن a و b لازم يكونوا even، فده يخالف الفرض إنهم مالهمش عوامل مشتركة → تناقض.

---

### Example 8  
> [!example]
> **Statement:** If 3n + 2 is odd, then n is odd.

Assume both **3n + 2 is odd (p)** and **n is even (¬q)**.  
Let n = 2k → 3n + 2 = 6k + 2 = 2(3k + 1) → even.  
Contradiction. Hence n must be odd.

---

## 5. Proof of Equivalence (p ↔ q)

> [!note]
> To prove p ↔ q, show **both directions**:  
> p → q and q → p.

🟡 Difficulty: Intermediate

### Example 9
> [!example]
> If n is a positive integer, then n is odd **iff** n² is odd.  
Both directions were proven in earlier examples.

**بالعربي:** "n فردي ↔ n² فردي"، لأن كل واحدة بتستلزم التانية.

---

## 6. Trivial and Vacuous Proofs

> [!note]
> **Trivial Proof:**  
> Show that q is true → then p → q is true automatically.  
> Example: “If it’s raining then 1 = 1.” (q always true)

> [!note]
> **Vacuous Proof:**  
> Show that p is false → then p → q is true automatically.  
> Example: “If I am both rich and poor then 2 + 2 = 5.” (p always false)

**بالعربي:**  
الـ Trivial بتثبت النتيجة مباشرة لأنها صحيحة دائمًا،  
والـ Vacuous بتبقى صحيحة لأن الفرض نفسه غلط من الأساس.

---

## 🧩 Hands-On Practice

1. Prove that if n is even, then n² is even.  
2. Show that if n² is divisible by 4, then n is even.  
3. Prove that if r and s are rational, then r – s is rational.  
4. Use proof by contradiction to show √3 is irrational.

---

## 📚 Glossary

| Term | Definition |
|------|-------------|
| **Direct Proof** | Show p → q by assuming p and proving q. |
| **Contrapositive** | Prove ¬q → ¬p instead of p → q. |
| **Contradiction** | Assume ¬p and derive a logical impossibility. |
| **Trivial Proof** | q is always true → p → q automatically true. |
| **Vacuous Proof** | p is always false → p → q automatically true. |
| **Biconditional (↔)** | Two-way conditional: both p → q and q → p. |

---

## 🧠 Key Takeaways

- Direct proof = straightforward, but not always easy.  
- Contraposition = reverse and negate both parts.  
- Contradiction = assume opposite and find impossibility.  
- Biconditional = prove both directions.  
- Trivial/Vacuous = special logical shortcuts.

---

## 🎓 Quick Review Card

> **Q:** What is the only case where p → q is false?  
> **A:** When p is true and q is false.

> **Q:** How does proof by contraposition work?  
> **A:** Prove ¬q → ¬p instead of p → q.

> **Q:** What’s the main idea of proof by contradiction?  
> **A:** Assume ¬p and show it leads to a contradiction.

> **Q:** What’s the difference between trivial and vacuous proofs?  
> **A:** Trivial → q true; Vacuous → p false.

> **Q:** When proving biconditional (↔), what must be shown?  
> **A:** Both directions: p → q and q → p.

---

## 🔗 Further Resources

- *Discrete Mathematics and Its Applications* by Kenneth Rosen — Sections 1.6 & 1.7  
- Khan Academy: *Introduction to Proofs*  
- Coursera: *Mathematical Thinking* by Stanford University  
- YouTube: *Proof Methods Explained (Direct, Contrapositive, Contradiction)*

---
