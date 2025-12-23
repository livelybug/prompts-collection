# Architecture Documentation Guide: Logic-Gate Framework

## Part 1: Writing Principles

### Tree-Based Flowchart Model

Flowcharts in the architecture doc MUST use a tree structure.

#### Definitions
* **Element**: A subsystem or module. A subsystem is composed of modules, not needed in a small system.
* **Node**: A flowchart that chains multiple elements.
* **Root Node**: The top-level node describing the entire system.
* **Parent Node**: A node that contains some elements that can be expanded further.
* **Child Node**: A node that explains one specific element of its parent node.

### Structural Rules

#### 1. Root Node

* Exactly one root node per system.
* Represents the highest level of the system.
* Chains major elements.

#### 2. Parent–Child Rules

* A parent node MAY have multiple child nodes.
* Each child node MUST:
  * Explain exactly one element from the parent.

#### 3. Expansion Criteria (Complexity Threshold)

An element MUST be expanded into a child node if it is qualitatively complex, including when it:

* Requires internal control flow to be understood

If none element in a node apply, the node remains a leaf.

#### 4. Leaf

* A node that's not expanded further is a leaf.
* A leaf represent an simple operation or a third-party black box.

### Other Rules
* Hierarchy Numbering & Naming: 
  * Use decimal outline numbering (e.g., 1.1 Root, 2.1 Child A, 2.2 Child B, 3.1 Grandchild A) to represent the tree depth.
* Flowchart rule:
  * Indentation: Use strictly nested bullet points to denote scope.
* Parent nodes MUST reference their child nodes.
* Localized Context (Terminology Ledger):
  * Each node (Root, Parent, or Child) must have its own Terminology Ledger immediately following its logic flow to define terms specific to that node.
* Style Constraint:
  * Use concise, declarative language. Eliminate decorative adjectives.

### Summary

* Flowcharts in an architecture docu forms a tree.
* Expansion is driven by qualitative complexity.
* Each child node explains one parent element.

---

## Part 2: Tree-Based Document Template

### 1. [Root Node]: System Master Orchestration

*Scope: The highest-level flow chaining the primary elements.*

#### 1.1 Root Logic Flow

* **IF** `[Global Trigger]` is detected:
* **THEN** execute `[Element A]`.
* **AND** execute `[Element B]`.
* **IF** results from both are valid:
  * **THEN** commit to `[Global Persistence]`.
* **ELSE**:
  * **THEN** trigger `[Global Error Handler]`.

#### 1.1T Root Terminology Ledger

| Term | Definition |
| --- | --- |
| **Global Persistence** | Save the data to global storage. |

---

### [Node N]: [Element Name] (Child of Node [Parent ID])

*Repeat this structure for every element that meets the complexity threshold.*

#### N.1 Logic Flow

* **FOR EACH** `[Input]` from `[Parent Node]`:
  * **IF** `[Internal Condition X]`:
    * **THEN** route to `[Module N.a]`.
  * **ELSE IF** `[Internal Condition Y]`:
    * **THEN** route to `[Module N.b]`.

* **WHILE** `[Process]` is active:
  * **THEN** update `[Local State]`.

* return `[Output]` to `[Parent Node]`.

#### N.1T Node N Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Local State]** | Ephemeral data stored within the scope of this node. |

---

### [Node N.x]: [Element Name] (Leaf Node of Node [Parent ID])

*Scope: Final node of logic. No further child nodes.*

#### N.x.1 Logic Flow

* **IF** `[Condition]`:
  * **THEN** perform `[Atomic Action]`.
* **ELSE**:
  * **THEN** return `[Default Value]`.

#### N.x.1T Node N.x Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Atomic Action]** | A single, non-divisible technical operation. |

---
