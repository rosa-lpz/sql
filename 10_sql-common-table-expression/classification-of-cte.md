# Classification of Common Table Expression (CTE)

In terms of SQL terminology, database architecture, and standard classifications, a **Common Table Expression (CTE)** is classified along four main dimensions:

---

### ANSI/ISO Standard Classification: *Query Expression*

In the official **ANSI/ISO SQL standard** (introduced in **SQL:1999**), a CTE is formally classified as a **`query expression`** or a **`with clause`**.

It falls under the functional category of a **Derived Table** or **Inline Named View**. Rather than being a physical database object, it is classified as a syntactic construction designed to define named, temporary intermediate result sets inline within a single statement.

---

### SQL Language Category: *DML (Data Manipulation Language)*

SQL syntax is typically split into DDL, DML, DCL, and TCL:

* **CTE Classification:** **DML (Data Manipulation Language)**.
* **Why:** CTEs do not create, alter, or drop schema objects in the database catalog (which would be DDL like `CREATE TABLE` or `CREATE VIEW`). Instead, a CTE is executed entirely within the context of a DML query statement (`SELECT`, `INSERT`, `UPDATE`, or `DELETE`).

---

### Database Object vs. Runtime Construct: *Non-Persistent Virtual Construct*

When categorizing how database systems handle SQL artifacts:

* **Persistent Schema Objects** (e.g., *Tables, Permanent Views*): Saved in the system catalog and accessible across sessions.
* **Session Objects** (e.g., *Temp Tables, Session Temp Views*): Stored in temporary storage (like `tempdb` or local driver memory) for the life of a session.
* **Inline runtime constructs (CTEs & Subqueries):** **No catalog persistence**. A CTE exists **only in memory/CPU execution plans** for the exact millisecond-duration that the host query runs.

---

### Categorization by Structural Type

Depending on how a CTE is constructed, query engines classify it into two functional types:

1. **Non-Recursive CTE:** A simple inline subquery that evaluates once to modularize or simplify complex relational logic.
2. **Recursive CTE:** A specialized query structure that references its own name. Engine execution planners classify this as an **iterative fixed-point operation** used to traverse hierarchical structures (like trees, org charts, or bill-of-materials).

---

### Summary Matrix

| Taxonomy Level | Classification |
| --- | --- |
| **ANSI Standard Category** | Derived Table / Named Query Expression (`WITH` Clause) |
| **Language Class** | DML (Data Manipulation Language) |
| **Persistence Class** | Non-persistent / In-memory query scope |
| **Execution Class** | Subquery Refactoring / Pipeline Optimization |