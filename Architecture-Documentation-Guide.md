# Architecture Documentation Guide: Logic-Gate Framework

## Part 1: Writing Principles

**1. Recursive Depth**

* **Level 1** is the root (System Context).
* **Level ** explains any node from **Level ** that requires further technical breakdown.
* Stop nesting only when a node represents an atomic operation or a third-party black box.

**2. Multi-Component Expansion**

* Each level can contain multiple sub-sections.
* If Level 1 contains `[Subsystem A]` and `[Subsystem B]`, then Level 2 must contain a dedicated breakdown for both if they meet the complexity threshold.

**3. Logic-Gate Flowcharts**

* All flows must be written in declarative pseudo-code.
* Use indentation to show nesting.
* **Keywords:** `IF`, `AND`, `OR`, `THEN`, `ELSE`, `WHILE`, `FOR EACH`, `EXIT`.

**4. Localized Terminology**

* Define `[Terms]` at the specific level where they are introduced.
* Use the **Terminology Ledger** table immediately following the flow logic.

**5. Style Constraint**

* Eliminate subjective/decorative language (e.g., "fast," "easy," "efficient").
* Use only objective, declarative statements.

---

# Part 2: Recursive Document Template

## Level 1: [System Name] Root Orchestration

*Scope: The highest-level chain connecting external triggers to the system boundary.*

### 1.1 Master Logic Flow

* **IF** `[Global Trigger]` occurs:
* **THEN** route to `[Subsystem A]`.
* **AND** route to `[Subsystem B]`.
* **IF** `[Subsystem A]` AND `[Subsystem B]` return `[Success]`:
* **THEN** update `[Primary State Store]`.


* **ELSE**:
* **THEN** execute `[Global Recovery Flow]`.





### 1.2 Level 1 Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Term]** | Objective technical description. |

---

## Level [N]: [Subsystem/Module Name] Breakdown

*Repeat this section for every complex node identified in Level [N-1].*

### [N].1 Logic Flow for [Component Name]

* **FOR EACH** `[Input Unit]` from `[Level N-1]`:
* **IF** `[Internal Condition]`:
* **THEN** execute `[Child Module X]`. (Expanded in Level N+1).


* **ELSE**:
* **THEN** execute `[Child Module Y]`. (Expanded in Level N+1).




* **IF** all units processed:
* **THEN** return `[Aggregated Output]` to `[Level N-1]`.



### [N].2 Level [N] Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Term]** | Objective technical description. |

---

## Level [N+1]: [Atomic Component Name]

*Scope: The final layer of logic where no further sub-components exist.*

### [N+1].1 Logic Flow

* **IF** `[State A]`:
* **THEN** execute `[Atomic Function]`.


* **THEN** return `[Result]` to `[Level N]`.

### [N+1].2 Level [N+1] Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Term]** | Objective technical description. |

