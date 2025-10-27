# Lecture 1: Digital Systems and Binary Numbers  
**Instructor:** Mirvat Al-Qutt, Ph.D – Ain Shams University  
**Course:** Digital Logic Design  

---

## Agenda
- What’s this course about?
- Course arrangement
- Study materials
- Grading and assessment
- Teaching methods
- Planned syllabus
- Instructor contact

---

## What is Logic Design?
**Design:**  
- Systematic way of solving a problem with constraints (size, cost, power, elegance).  

**Logic Design:**  
- Collection of digital logic components and interconnections.  
- Functions: control, data manipulation, communication.  
- Often optimized or transformed for constraints.

---

## Why Study Logic Design?
- First step to understanding computer architectures (hardware + computation).  
- Base of all modern computing and control devices.  
- Enables:
  - Microprocessors
  - Dense and inexpensive storage
  - Wireless networking
  - New materials

---

## Study Materials
1. Notes / slides  
2. Tutorials and lab sheets  
3. Textbook: *Digital Design, 5th Edition* – M. Morris Mano & Michael Ciletti  

---

## Grading and Assessment
- Final Written Exam: 50  
- Midterm: 15  
- Quizzes: 5  
- Lab Activities, Assignments, Tasks: 10  
- Practical Exam: 20  

---

## Teaching Methods
- Interactive lectures  
- Discussions  
- Problem-based learning  
- Experimental learning (labs and hands-on practice)  

---

## Syllabus (Planned)
1. Digital Systems and Binary Numbers  
2. Boolean Algebra and Logic Gates  
3. Gate-Level Minimization  
4. Combinational Logic  
5. Synchronous Sequential Logic  
6. Registers and Counters  

---

## Instructor Contact
- **Mirvat Al-Qutt, Ph.D.**  
- Email: mmalqutt@cis.asu.edu.eg  

---

## Chapter Outline
1.1 Digital Systems  
1.2 Binary Numbers  
1.3 Number-Base Conversions  
1.4 Octal and Hexadecimal Numbers  
1.9 Binary Logic  

---

## Key Concepts

### Digital Systems
- Represent and manipulate discrete information.  
- Examples:
  - Decimal digits {0–9}  
  - Alphabet letters {A–Z}  
  - 64 chessboard squares  

### Signals
**Analog system:** continuous values.  
**Digital system:** discrete values.  

### Binary Digital Signal
- Two levels: 
	- Digits 0 and 1
	- False (F) and True (T)
	- Low (L) and High (H)
	- On and Off
---

## Number Systems
digits :LiArrowBigRight: { 0 , **base** - 1 } 
base = **radix**

### Decimal (Base 10)
- Digits: {0–9}  
- Value = Σ(digit × 10<sup>postion</sup>).  

### Binary (Base 2)
- Digits: {0,1}  
- Value = Σ(digit × 2<sup>position</sup>).  

### Base-5
- Digits: {0–4}  
- Value = Σ(digit × 5<sup>position</sup>).  

### Octal (Base 8)
- Digits: {0–7}  
- Value = Σ(digit × 8<sup>position</sup>).  

### Hexadecimal (Base 16)
- Digits: {0–9,A–F}  
- Groups binary into 4-bit chunks.  
- Used in addresses, instructions, data.  

---

## Binary System Notes
- Bits = binary digits.  
- Conversion to decimal: add powers of 2 for bits = 1.  
- Storage units:
  - 2<sup>10</sup> = 1K  (kilo)
  - 2<sup>20</sup> = 1M  (mega)
  - 2<sup>30</sup> = 1G  (giga)
  - 2<sup>40</sup> = 1T  (tera) 
- Byte = 8 bits.  

	![[Pasted image 20250924225114.png]]
	
	![[Pasted image 20250924225242.png]]
---

## Number Base Conversions
- **Decimal → Binary (integer):** divide repeatedly by 2.  
- **Decimal → Binary (fraction):** multiply repeatedly by 2.  
- **Decimal → Octal / Hex:** same process with base 8 or 16.  
- **Binary ↔ Octal:** group 3 bits.  
- **Binary ↔ Hexadecimal:** group 4 bits.  
- **Octal ↔ Hexadecimal:** convert via binary as intermediate.  


	![[Pasted image 20250924225313.png]]
---

## Conversion Tables
| Decimal | Binary | Octal | Hex |
|---------|--------|-------|-----|
| 0       | 0000   | 0     | 0   |
| 1       | 0001   | 1     | 1   |
| 2       | 0010   | 2     | 2   |
| 3       | 0011   | 3     | 3   |
| 4       | 0100   | 4     | 4   |
| 5       | 0101   | 5     | 5   |
| 6       | 0110   | 6     | 6   |
| 7       | 0111   | 7     | 7   |
| 8       | 1000   | 10    | 8   |
| 9       | 1001   | 11    | 9   |
| 10      | 1010   | 12    | A   |
| 11      | 1011   | 13    | B   |
| 12      | 1100   | 14    | C   |
| 13      | 1101   | 15    | D   |
| 14      | 1110   | 16    | E   |
| 15      | 1111   | 17    | F   |

---

## Practice Exercises
- Convert 41 decimal → binary.  
- Convert 153 decimal → octal.  
- Convert 0.6875 decimal → binary.  
- Convert 0.513 decimal → octal.  
- Convert (01101011.111100) binary → octal and hexadecimal.  
- Convert (673.12) octal → binary.  
- Convert (306.D) hexadecimal → binary.  

---

### Digital vs Analog
Digital :LiArrowBigRight: Discrete numbers
Analog :LiArrowBigRight: infinite numbers (continues)
### Numbering systems 
**(base == radix )**
* *Decimal*  (base 10)
* *Binary*  (base 2)
*  *Octal* (base 8)
* *Hexadecimal* (base 16)

### Equation to get total number of numbers in bytes
**n = 5** :LiArrowBigRight: XXXXX
	 ***0:LiArrowBigRight: 2<sup>n</sup>  -1**
0 :LiArrowBigRight: 31

## Conversions 
Decimal Numbering System
![[Pasted image 20250924195523.png]]
