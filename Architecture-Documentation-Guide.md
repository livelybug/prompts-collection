# Architecture Documentation Guide: Logic-Gate Framework

## Part 1: Writing Principles

### Tree-Based Flowchart Model

Nodes in the architecture doc MUST use a tree structure.

#### Definitions
* **Element**: A subsystem or module. A subsystem is composed of modules, not needed in a small system.
* **Flowchart**: A flowchart that chains multiple elements, using pseudo-code logic gates for flow representation.
* **Node**: A node contains a flowchart and optionally a terminology ledger.
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

### Flowchart Rules:
Flowcharts must utilize the Logic-Gate Syntax defined below. Visual diagrams are replaced by conditional pseudo-code.
* Indentation: Indentation levels and bullet buttons represent the visual "path" of a diagram.
* Keywords: Capitalize logical operators (IF, AND, OR, THEN, ELSE, WHILE, EXIT).
* References: Elements in parent nodes MUST reference the corresponding child nodes if any, enclosing child node link in [CHILD NODE NAME].

### Other Rules
* Tree Hierarchy Numbering & Naming: 
  * Apply Standard Tree Numbering (e.g., 1.0 Root, 1.1 Child A, 1.2 Child B, 1.1.1 Grandchild A) to represent the tree depth.
* Localized Context (Terminology Ledger):
  * Each node (Root, Parent, or Child) may have its own Terminology Ledger immediately following its logic flow to define terms specific to that node.
* Style Constraint:
  * Use concise, declarative language. Eliminate decorative adjectives.

---

## Part 2: Tree-Based Document Template

### 1.0 [Root Node]: System Master Orchestration

*Scope: The highest-level flow chaining the primary elements.*

#### 1.0.1 Root Logic Flow

* **IF** `[Global Trigger]` is detected:
  * **THEN** execute `[Element A]` (See Node 1.1 [Node A name]).
    * **AND** execute `[Element B]` (See Node 1.2 [Node B name]).
* **IF** results from both are valid:
  * **THEN** commit to `[Global Persistence]`.
* **ELSE**:
  * **THEN** trigger `[Global Error Handler]`.

#### 1.0.2 Root Terminology Ledger

| Term | Definition |
| --- | --- |
| **Global Persistence** | Save the data to global storage. |

---

### Node 1.1: [Node A Name] (Child of Node 1.0)

*Repeat this structure for every element that meets the complexity threshold.*

#### 1.1.1 Logic Flow

* **FOR EACH** `[Input]` from `[Parent Node]`:
  * **IF** `[Internal Condition X]`:
    * **THEN** route to `[Module 1.1.1]` (See Node 1.1.1 [Module Name]).
  * **ELSE IF** `[Internal Condition Y]`:
    * **THEN** route to `[Module 1.1.2]` (See Node 1.1.2 [Module Name]).

* **WHILE** `[Process]` is active:
  * **THEN** update `[Local State]`.

* return `[Output]` to `[Parent Node]`.

#### 1.1.2 Node 1.1 Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Local State]** | Ephemeral data stored within the scope of this node. |

---

### Node 1.1.1: [Module 1.1.1 Name] (Leaf Node of Node 1.1)

*Scope: Final node of logic. No further child nodes.*

#### 1.1.1.1 Logic Flow

* **IF** `[Condition]`:
  * **THEN** perform `[Atomic Action]`.
* **ELSE**:
  * **THEN** return `[Default Value]`.

#### 1.1.1.2 Node 1.1.1 Terminology Ledger

| Term | Definition |
| --- | --- |
| **[Atomic Action]** | A single, non-divisible technical operation. |

---
