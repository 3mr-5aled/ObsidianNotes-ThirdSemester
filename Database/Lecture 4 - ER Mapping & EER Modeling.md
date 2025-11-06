# DBD – ER Mapping & EER Modeling 

---

## Chapter 7 – ER-to-Relational Mapping Algorithm

> [!summary]
> The **ER-to-Relational Mapping Algorithm** converts an **ER schema** into a **relational schema**.  
> It ensures that all entities, attributes, and relationships are represented as tables with appropriate keys and constraints.

---

### **Step 1: Mapping of Regular Entity Types**
- Create a **relation** (table) for each **regular entity type**.
- Include all **simple attributes** as columns.
- Choose one **key attribute** as the **primary key (PK)**.
- **Composite attributes** are broken into their components.
- **Multivalued attributes** are not included here (handled in Step 6).

> [!example]
> `EMPLOYEE(Fname, Minit, Lname, SSN, Bdate, Address, Sex, Salary, Super_ssn, Dno)`

---

### **Step 2: Mapping of Weak Entity Types**
- Create a **separate relation** for each **weak entity**.
- Include a **foreign key (FK)** to the **identifying entity**’s relation.
- The **PK** of the weak entity = combination of its **partial key + identifying FK**.

> [!example]
> `DEPENDENT(Essn, Dependent_name, Sex, Bdate, Relationship)`  
> - `Essn` → FK referencing `EMPLOYEE.SSN`  
> - PK = `(Essn, Dependent_name)`

---

### **Step 3: Mapping of Binary 1:1 Relationship Types**

There are **three approaches**:

1. **Foreign Key Approach:**  
   - Add FK from one entity (its PK) to the other.  
   - Prefer to take the entity with **total participation** to put fk.

   > [!example]
   > MANAGES(Dept_no → FK in DEPARTMENT referencing EMPLOYEE)

2. **Merged Relation Approach:**  
   - Merge both entities and the relationship into one table.  
   - Use when **both participations are total**.

3. **Cross-Reference Table:**  
   - Create a new relation for the relationship.
   - Contains PKs from both participating entities as FKs.

> [!tip]
> ✅ Prefer the **FK approach** for simplicity unless merging is required by design.

---

### **Step 4: Mapping of Binary 1:N Relationship Types**
- Add FK to the **N-side** entity’s relation.
- Include **any relationship attributes** as columns.
  
> [!example]
> `EMPLOYEE` includes `Dno` (FK referencing `DEPARTMENT.Dnumber`) to represent the **WORKS_FOR** relationship.

> [!mermaid]
> ```mermaid
> erDiagram
>     DEPARTMENT ||--o{ EMPLOYEE : WORKS_FOR
>     DEPARTMENT {
>         int Dnumber PK
>         string Dname
>     }
>     EMPLOYEE {
>         int SSN PK
>         string Name
>         int Dno FK
>     }
> ```

---

### **Step 5: Mapping of Binary M:N Relationship Types**
- Create a **new relation** to represent the M:N relationship.
- Include:
  - FKs from both participating entities.
  - Any relationship attributes.
- The **PK** is the combination of the two FKs.

> [!example]
> `WORKS_ON(Essn, Pno, Hours)`  
> - FKs: `Essn → EMPLOYEE`, `Pno → PROJECT`  
> - PK = `{Essn, Pno}`

---

### **Step 6: Mapping of Multivalued Attributes**
- Create a **new relation** for each multivalued attribute.
- Include:
  - Attribute value column.
  - FK referencing the entity’s PK.
- PK = combination of both.

> [!example]
> `DEPT_LOCATIONS(Dnumber, Dlocation)`  
> - Represents multivalued attribute `LOCATIONS` of `DEPARTMENT`

---

### **Step 7: Mapping of N-ary Relationship Types (n > 2)**
- Create a new **relation** for the n-ary relationship.
- Include:
  - FKs referencing each participating entity.
  - Relationship’s own attributes.
- PK = combination of all FKs.

![[Pasted image 20251031203022.png]]

> [!example]
> `SUPPLY(Sname, Part_no, Proj_name, Quantity)`  
> - Represents ternary relationship **SUPPLY(SUPPLIER, PART, PROJECT)**  
> - PK = `{Sname, Part_no, Proj_name}`

> [!mermaid]
> ```mermaid
> erDiagram
>     SUPPLIER ||--o{ SUPPLY : supplies
>     PROJECT ||--o{ SUPPLY : receives
>     PART ||--o{ SUPPLY : includes
> ```

---

### **Summary of Mapping Constructs**

| ER Model Concept             | Relational Model Equivalent             |
|------------------------------|-----------------------------------------|
| Entity type                  | Entity relation                         |
| 1:1 / 1:N relationship       | Foreign key or relationship relation     |
| M:N relationship             | Relationship relation + 2 FKs            |
| n-ary relationship           | Relationship relation + n FKs            |
| Simple attribute             | Column                                  |
| Composite attribute          | Set of component columns                 |
| Multivalued attribute        | Separate relation + FK                   |
| Key attribute                | Primary key                             |

---

> [!question]
> - Why do we prefer placing the FK on the total participation side in 1:1 relationships?  
> - What issues arise if a multivalued attribute is not normalized into a separate table?

---

### **Main Takeaways**
- Every ER construct maps systematically into a relational schema.  
- Proper placement of keys maintains referential integrity.  
- N-ary and multivalued attributes require separate relations.  

---

## Chapter 4 – Enhanced Entity-Relationship (EER) Modeling

> [!summary]
> **EER Modeling** extends the ER model to include **inheritance, specialization, and generalization**—allowing more precise conceptual representation.

---

### **Key Concepts**
- **Superclass/Subclass** hierarchy
- **Specialization / Generalization**
- **Attribute and Relationship Inheritance**
- **Disjointness and Completeness Constraints**
- **Shared Subclasses (Multiple Inheritance)**

---

### **Subclasses and Superclasses**
- A **subclass** is a subset of entities from a **superclass**.
- There are called **"IS_A"** relationship
- Each subclass may have:
  - **Local attributes** (specific to subclass)
  - **Local relationships**

> [!example]
> - `EMPLOYEE` superclass → subclasses: `ENGINEER`, `MANAGER`, `TECHNICIAN`, etc.  
> - Each inherits `Name`, `SSN`, etc., from `EMPLOYEE`.

> [!mermaid]
> ```mermaid
> graph TD
>   EMPLOYEE --> ENGINEER
>   EMPLOYEE --> MANAGER
>   EMPLOYEE --> TECHNICIAN
> ```

![[Pasted image 20251027234954.png]]

---

### **Attribute Inheritance**
- Each subclass **inherits**:
  - All attributes of superclass.
  - All relationships of superclass.

> [!tip]
> **Inheritance rule:**  
> If `SECRETARY` is a subclass of `EMPLOYEE`, every `SECRETARY` entity **must** also be an `EMPLOYEE`.

![[Pasted image 20251027235059.png]]

---

### **Specialization**
- **Definition:** Process of defining subclasses from a superclass based on distinguishing characteristics.  
- **Top-down approach.**

> [!example]
> `{SECRETARY, ENGINEER, TECHNICIAN}` = specialization of `EMPLOYEE` based on `JobType`.

![[Pasted image 20251027235200.png]]

---

### **Generalization**
- **Definition:** Reverse of specialization; combines multiple entity types into a superclass.  
- **Bottom-up approach.**

> [!example]
> `CAR` and `TRUCK` → generalized into `VEHICLE`.

> [!mermaid]
> ```mermaid
> graph TD
>   CAR --> VEHICLE
>   TRUCK --> VEHICLE
> ```

![[Pasted image 20251027235217.png]]

---

### **Constraints in EER**

#### **1. Disjointness Constraint**
- **Disjoint (d):** An entity can belong to only one subclass.  
- **Overlapping (o):** Entity may belong to multiple subclasses.

#### **2. Completeness Constraint**
- **Total (double line):** Every superclass entity must belong to a subclass. 
- **Partial (single line):** Some superclass entities may not belong to any subclass.


![[Pasted image 20251027235327.png]]
![[Pasted image 20251027235336.png]]
![[Pasted image 20251027235344.png]]
![[Pasted image 20251027235352.png]]

> [!example]
> - Disjoint total → every `EMPLOYEE` is either a `MANAGER` or `ENGINEER`, not both.  
> - Overlapping partial → some `EMPLOYEES` belong to none or multiple subclasses.

---

### **Hierarchies, Lattices, and Shared Subclasses**
- **Hierarchy:** Subclass has **one superclass** (single inheritance).  
- **Lattice:** Subclass can have **multiple superclasses** (multiple inheritance).  
- **Shared subclass:** Appears under more than one superclass.

> [!example]
> `ENGINEERING_MANAGER` = subclass of both `ENGINEER` and `MANAGER`.

> [!mermaid]
> ```mermaid
> graph TD
>   ENGINEER --> ENGINEERING_MANAGER
>   MANAGER --> ENGINEERING_MANAGER
> ```

![[Pasted image 20251027235436.png]]

---
### **Types of Specialization/Generalization**

| Type | Disjointness | Completeness |
|------|---------------|--------------|
| Disjoint Total | d | Total |
| Disjoint Partial | d | Partial |
| Overlapping Total | o | Total |
| Overlapping Partial | o | Partial |


![[Pasted image 20251027235446.png]]

---

> [!question]
> - How does multiple inheritance affect database schema design?  
> - Why is specialization considered a top-down conceptual refinement?

---

### **Mnemonic**
> **“SDHTGC” → Steps Define Hierarchy, Then Generalize Carefully**  
> Helps remember the EER progression:  
> **S**pecialization → **D**isjointness → **H**ierarchy → **T**otality → **G**eneralization → **C**ompleteness

| Step                   | Concept                                                                                                                                                                         |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **S – Specialization** | Start by identifying **subclasses** from a superclass. Example: `Employee` → `Manager`, `Engineer`.                                                                             |
| **D – Disjointness**   | Decide if subclasses are **disjoint (mutually exclusive)** or **overlapping**. Example: A person can’t be both a `Student` and `Teacher` (disjoint).                            |
| **H – Hierarchy**      | Define the **inheritance hierarchy** — how attributes and relationships flow from superclass to subclasses. Example: All subclasses inherit `Employee`’s attributes.            |
| **T – Totality**       | Specify if the specialization is **total (every entity belongs to a subclass)** or **partial (some don’t)**. Example: Every employee is either `Manager` or `Engineer` (total). |
| **G – Generalization** | Reverse of specialization. Combine similar entities into a **superclass**. Example: Combine `Car`, `Truck`, `Bus` into `Vehicle`.                                               |
| **C – Completeness**   | Ensure **all entities and attributes are covered** in the hierarchy; no data loss or redundancy.                                                                                |

---

## **Glossary**

| Term | Definition |
|------|-------------|
| **ER Model** | Conceptual model defining entities and their relationships. |
| **EER Model** | Extension of ER including inheritance and specialization. |
| **Superclass** | General entity type containing shared attributes. |
| **Subclass** | Specialized entity type inheriting attributes/relationships. |
| **Specialization** | Top-down process forming subclasses. |
| **Generalization** | Bottom-up process forming superclasses. |
| **Disjointness Constraint** | Restricts subclass membership exclusivity. |
| **Completeness Constraint** | Specifies total or partial subclass coverage. |
| **Weak Entity** | Depends on another entity for identification. |
| **Multivalued Attribute** | Attribute with multiple possible values. |

---

## **Recommended Resources**
- **Book:** *Elmasri & Navathe, Database Systems: Fundamentals of Database Systems (6th Edition)*  
- **Video:** [Neso Academy – ER to Relational Mapping](https://www.youtube.com/watch?v=Uon4W_yZK1U)  
- **Article:** *GeeksforGeeks – ER to Relational Model Conversion*  
- **Tool:** *draw.io* or *Mermaid Live Editor* for practicing ER/EER diagrams.

---

> [!note]
> This lecture bridges **conceptual modeling (ER/EER)** and **logical schema design (Relational)**—a crucial foundation for normalization and advanced database design.

---
