# Example 2: Interval Constraint Propagation

**Status**: Reference Implementation  
**Last Updated**: 2026-07-06  
**Difficulty**: Intermediate

---

## Problem

Solve over intervals $[0, 100]$:
- $x > 5$
- $y < 20$
- $x + y < 100$
- $x \geq y$

**Find**: Tightest possible bounds.

---

## SYSCO Solution

### Step 1: Define Constraint Lattice

Domain: Interval assignments  
Order: Reverse inclusion (tighter = more informative)

### Step 2: Define Rewrite Rules

**Rule 1**: $x > 5$ $\to$ Update lower bound  
**Rule 2**: $y < 20$ $\to$ Update upper bound  
**Rule 3**: $x + y < 100$ $\to$ Propagate bounds  
**Rule 4**: $x \geq y$ $\to$ Synchronize bounds

### Step 3: Execute Propagation

**Iteration 1**:
- Rule 1: $x \in [5.00001, 100]$
- Rule 2: $y \in [0, 19.99999]$
- Rule 4: $a_y := a_x = 5.00001$

**Iteration 2**:
- Rule 3: $b_x := 100 - a_y = 94.99999$

**Converged**: Fixed point reached

### Step 4: Fixed Point

$$x \in [5.00001, 94.99999]$$
$$y \in [5.00001, 19.99999]$$

---

## Properties Demonstrated

✓ **Termination**: $O(n^3)$ propagation  
✓ **Confluence**: All orderings yield same result  
✓ **Reversibility**: Forward rules can be inverted

---

**End of Example 2**
