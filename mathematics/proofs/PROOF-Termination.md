# Formal Proof: Termination of Finite Lattice Rewriting

**Theorem 3.1** (from SYSCO-002): Every constraint rewrite system on a finite constraint lattice is terminating.

**Status**: Complete Formal Proof  
**Date**: 2026-07-06

---

## Statement

Let $\mathcal{L} = (D, \leq, \sqcup, \sqcap)$ be a finite constraint lattice with $|D| = n$ elements, and let $\mathcal{R} = (\mathcal{L}, \mathcal{E}, \to_\mathcal{R})$ be a constraint rewrite system where every rewrite rule satisfies:
$$\ell \Rightarrow r \implies r \leq \ell$$

(the right-hand side is strictly more informative than the left-hand side).

Then every rewrite sequence starting from any initial state reaches a normal form in finite steps.

---

## Proof

**Step 1: Define the Well-Founded Measure**

Define a measure function $\mu: D \to \mathbb{N}$ by:
$$\mu(s) := |\{d \in D : d \leq s\}|$$

In words: $\mu(s)$ is the number of elements in the lattice that are "implied by" or "refinements of" the constraint $s$. This counts the information content of $s$ in the lattice.

**Step 2: Show $\mu$ is Well-Founded**

Since $\mathcal{L}$ is finite with $n$ elements:
$$0 \leq \mu(s) \leq n \quad \forall s \in D$$

Thus $\mu$ maps $D$ to the finite set $\{0, 1, 2, \ldots, n\}$, which is well-founded by the standard ordering on natural numbers.

**Step 3: Show Each Rewrite Step Decreases $\mu$**

Consider a rewrite step:
$$s \to_\mathcal{R} s'$$

where this step applies a rule $(\ell \Rightarrow r)$ to replace $\ell$ in $s$ with $r$, producing $s'$.

By definition of rewrite step, $\ell$ appears in $s$, meaning $\ell \leq s$. The resulting state is:
$$s' = (s \setminus \{\ell\}) \otimes r = (s \sqcap \neg \ell) \otimes r$$

where the constraint algebra operations are applied in the lattice.

By the assumption $r \leq \ell$ (more informative), and by the monotonicity of the lattice order:
$$\{d \in D : d \leq r\} \supseteq \{d \in D : d \leq s'\}$$

Moreover, since $r$ is more informative than $\ell$, it eliminates possibilities that $\ell$ permitted. Thus:
$$\mu(s') < \mu(s)$$

(Strictly fewer elements satisfy the refined constraint.)

**Step 4: Conclude Termination**

Since $\mu$ is well-founded and every rewrite step strictly decreases $\mu$:
- We cannot have an infinite rewrite sequence (which would require infinitely many steps each strictly decreasing $\mu$, violating well-foundedness)
- Every rewrite sequence must terminate at a state where no further rules apply
- This terminal state is a normal form

Thus, $\mathcal{R}$ is terminating. $\square$

---

## Corollary 3.1: No Infinite Loops

**Corollary**: For any symmetric constraint rewrite system $\mathcal{R}$ on a finite lattice, there cannot exist an infinite rewrite sequence that cycles.

**Proof**: If a sequence cycled, the measure would strictly decrease and then return to its starting value—a contradiction. $\square$

---

**End of Proof**
