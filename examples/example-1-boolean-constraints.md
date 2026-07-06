# Example 1: Boolean Constraint Solving

**Status**: Reference Implementation  
**Last Updated**: 2026-07-06  
**Difficulty**: Beginner

---

## Problem

Solve:
- $x \vee y = \text{true}$
- $\neg z = \text{true}$
- $x \wedge z = \text{false}$

**Find**: All satisfying assignments.

---

## SYSCO Solution

### Step 1: Define Constraint Lattice

Domain: Partial truth assignments  
Order: Refinement (unknown $\leq$ true/false)

### Step 2: Define Rewrite Rules

**Rule 1**: If $x = \text{false}$ then $y := \text{true}$  
**Rule 2**: $z := \text{false}$  
**Rule 3**: If $x = \text{true}$ then $z := \text{false}$

### Step 3: Execute Propagation

**Initial**: $x = \text{unknown}, y = \text{unknown}, z = \text{unknown}$

**Iteration 1**: Apply Rule 2 $\to$ $z := \text{false}$

**Iteration 2**: No new constraints

**Fixed Point**: $z = \text{false}$, $x, y$ constrained by Rule 1

### Step 4: Extract Solutions

1. $(\text{true}, \text{true}, \text{false})$ ✓
2. $(\text{true}, \text{false}, \text{false})$ ✓
3. $(\text{false}, \text{true}, \text{false})$ ✓
4. $(\text{false}, \text{false}, \text{false})$ ✗ (violates Rule 1)

---

## Properties Demonstrated

✓ **Termination** (Theorem 3.1)  
✓ **Confluence** (Theorem 3.2)  
✓ **Decidability** (Theorem 3.3)

---

**End of Example 1**
