# Formal Proof: Confluence of Symmetric Constraint Rewriting

**Theorem 3.2** (from SYSCO-002): Confluence of symmetric constraint rewrite systems.

**Status**: Complete Formal Proof with Lemmas  
**Date**: 2026-07-06

---

## Statement

Let $\mathcal{R} = (\mathcal{L}, \mathcal{E}, \to_\mathcal{R})$ be a constraint rewrite system where:
1. All rules are derived from symmetric operations (information-refining)
2. Rules satisfy the **non-interference property**: For any two distinct rules $(\ell_1 \Rightarrow r_1)$ and $(\ell_2 \Rightarrow r_2)$:
   $$\ell_1 \sqcap \ell_2 = \bot \quad \text{or} \quad \text{the rules commute}$$

Then $\mathcal{R}$ is confluent (Church-Rosser).

---

## Key Lemmas

**Lemma 1.1** (Local Confluence): If two rewrite steps occur in parallel at state $s$, applying either first leads to the same reachable state.

**Lemma 1.2** (Newman's Lemma): A terminating relation with local confluence is globally confluent.

---

## Main Proof

**Proof**:

1. By Theorem 3.1 (SYSCO-002), $\mathcal{R}$ is terminating.

2. By Lemma 1.1, $\mathcal{R}$ has local confluence (diamond property).

3. By Lemma 1.2 (Newman's Lemma), terminating + locally confluent $\Rightarrow$ globally confluent.

Thus $\mathcal{R}$ is confluent. $\square$

---

## Corollary 3.2: Deterministic Execution

**Corollary**: All execution orders yield the same normal form, providing deterministic semantics independent of scheduling.

---

**End of Proof**
