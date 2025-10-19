# SAT Solver in Haskell

A complete **functional SAT solver** implemented in Haskell, inspired by the DPLL and CDCL algorithms.  
The project models Boolean formulas in Conjunctive Normal Form (CNF), implements progressively optimized solving techniques, and applies the solver to the **3-coloring problem** in graphs.

---

## Overview
The project explores the problem of **Boolean satisfiability (SAT)** using the functional paradigm of Haskell.  
It develops from basic formula representation and naive solving by enumeration to advanced strategies like unit propagation, pure literal elimination, conflict-driven clause learning, and non-chronological backtracking.

**Language:** Haskell  
**Focus:** Functional programming, lazy evaluation, type systems, recursion, and declarative problem-solving  

---

## Features

### 1. Boolean Formula Representation
Implemented in `Formula.hs`, this component defines:
- **Data structures** for literals, clauses, and formulas using sets (`Data.Set`)
- **Basic operations** for creating and manipulating CNF formulas
- **Naive SAT checking** via interpretation enumeration
- **Functional style** implementations using list/set comprehensions and higher-order functions  

### 2. Extended Formula Evaluation
Implemented in `ExtendedFormula.hs`, extending the solver to support:
- **Formula simplification** after assumptions  
  - Clause removal when a literal is satisfied  
  - Complement elimination from remaining clauses  
- **Unit clause propagation** for automatic assignments  
- **Pure literal elimination** for deterministic simplifications  
- **Mapping formulas** to associative structures (`Data.Map`) to retain links between simplified and original clauses  
- **Recursive and functional transformations** for formula reduction without explicit mutation  

### 3. Complete SAT Solver
Implemented in `Solver.hs`, integrating all mechanisms into a full DPLL/CDCL-style solver:
- **Unit propagation** and **pure literal elimination** loops  
- **Backtracking and conflict resolution**
  - Detection of conflicts through empty clauses  
  - Clause learning using **resolution**  
  - **Non-chronological backtracking** to earliest decision points
- **Heuristic literal selection** for branching  
- **Learned clause integration** to avoid repeating conflicts  

### 4. Application: Graph 3-Coloring
The solver is applied to encode and solve the **graph 3-coloring problem**:
- Each node is assigned three Boolean variables (for Red, Green, Blue)
- Clauses ensure:
  - Each node has **at least one color**
  - Each node has **at most one color**
  - Adjacent nodes have **different colors**
- The solver determines a satisfying assignment representing a valid coloring.

---

## Example Use Cases
- Verify whether a CNF formula is satisfiable and obtain a satisfying interpretation.  
- Simplify formulas dynamically during solving.  
- Learn new clauses from conflicts to optimize search.  
- Use SAT solving to compute valid **graph colorings**.

---

## Learning Outcomes
- Built a complete **SAT solver** purely in Haskell using functional constructs.  
- Practiced **lazy evaluation**, **pattern matching**, **algebraic data types**, and **higher-order functions**.  
- Applied **polymorphism**, **type abstraction**, and **monadic evaluation** in a declarative context.  
- Translated a theoretical **NP-complete problem** into a structured, functional implementation.  

---

## Project Structure
| File | Description |
|------|--------------|
| `Formula.hs` | Basic Boolean formula representation and naive SAT checking. |
| `ExtendedFormula.hs` | Formula simplification, unit propagation, and pure literal elimination. |
| `Solver.hs` | Full CDCL-based SAT solver with conflict analysis and backtracking. |


