<!-- solve-problem:e9dcf17c-2e24-431e-8a70-46f6b1a2a4f2 -->
# Graph isomorphism in polynomial time

A [Tangle Solve problem](https://solve.tangle.tools/problems/e9dcf17c-2e24-431e-8a70-46f6b1a2a4f2).

## What is the problem?

Given two finite, undirected graphs G₁ = (V₁, E₁) and G₂ = (V₂, E₂) with |V₁| = |V₂| = n, decide whether there exists a bijection φ: V₁ → V₂ such that {u,v} ∈ E₁ ⟺ {φ(u), φ(v)} ∈ E₂. The task: give a deterministic algorithm deciding this for **arbitrary** graphs in time poly(n) — equivalently n^(O(1)), with no dependence on n hidden in exponents. Variants worth noting: the search problem (produce φ), canonical form / canonical labeling (a function c on graphs with c(G) = c(H) iff G ≅ H), and counting versions (#GI). The standard formulation is the decision problem for simple undirected graphs; directed graphs, colored graphs, and hypergraphs are polynomially interreducible with this (via standard encodings, e.g., color via gadgets — verify gadget sizes for exact poly equivalence). Assumptions: standard Turing machine, no randomness required (randomized quasi-NC / poly algorithms exist but do not resolve the deterministic poly question).

## Why does it matter?

GI is the canonical "NPI candidate": one of the few natural problems neither known NP-complete nor in P; a poly algorithm (or an NP-hardness proof) would be a landmark in complexity theory. Polynomial-time canonical forms would directly improve practical molecular graph matching in cheminformatics and toolkits like nauty/Traces. Group-theoretic algorithms developed along the way (Luks's bounded-degree framework, Babai's divide-and-conquer) have spawned a whole subfield of permutation-group computation.

## What's already known?

- Babai (2016): quasipolynomial time, exp((log n)^(O(1))) — specifically ~exp(polylog n) via the "Local certificates" / Split-or-Johnson methodology on Johnson schemes. This is the state of the art for general graphs.
- Luks (1982): poly time for bounded degree; and poly for bounded color-class multiplicity; general GI reduces in poly time to GI on graphs of bounded degree (with quasipolynomial blowup removed only in special cases).
- Special classes in P: planar (Hopcroft–Wong), bounded genus, bounded treewidth, interval graphs, trees, bounded eigenvalue multiplicity (Babai–Grigoriev–Mount).
- Structural complexity: GI ∈ SPP ⊆ ⊕P ∩ PP-ish lowness results; GI is low for PP (Köbler–Schöning–Torán); a counting reduction framework shows GI unlikely to be NP-complete unless the polynomial hierarchy collapses to Σ₂^p.
- Barrier: Babai's framework handles "local" structure via Johnson schemes; the unresolved cases involve coherent configurations/schemes where primitive groups with large "defect" appear. Grochow–Qiao and the framework of "tensor isomorphism"-style reductions situate GI in a hierarchy of problems of apparently intermediate difficulty.

## What would count as solving it?

1. **Upper bound (main):** a proof that a specific deterministic algorithm decides GI on all n-vertex graphs in time n^c for an absolute constant c, with correctness proof.
2. **Lower bound variant:** a proof that GI is NP-complete (would also "settle" the census question negatively for P) — considered unlikely, as it collapses PH.
3. Any of: poly-time canonical labeling; GI ∈ coAM-collapsing improvements; or showing GI complete for a natural subclass of P.
A referee would require: full correctness proof (Babai's own 2015 preprint needed a patch — scrutiny is intense), worst-case guarantee, and handling of all coherent-configuration degenerate cases.

## How to start

1. Read Babai's paper (arXiv:1512.03547), especially the outline section and the "barriers" discussion, to understand exactly where quasipolynomiality is forced (the recursion on composition chains of primitive groups).
2. Read Luks (1982, JCSS) for the bounded-degree algorithm and the framework of stabilizer chains / Schreier–Sims — any poly algorithm will build on this group machinery.
3. Study coherent configurations and the Weisfeiler–Leman hierarchy: k-WL fails for fixed k, but understanding which configurations defeat individualization-refinement is essential; read Neuen & Schweitzer on WL dimension.
4. Candidate attack: improve the structure theory of primitive permutation groups with large stabilizer defect (Pyber's / Babai's "split-or-Johnson" bottleneck) to get poly bounds, or find a poly algorithm for strongly regular / rank-3 configuration isomorphism, the classic hard core.

## Key references

- L. Babai, *Graph Isomorphism in Quasipolynomial Time*, STOC 2016; arXiv:1512.03547. The quasipolynomial-time algorithm via group-theoretic divide-and-conquer and the Johnson scheme; includes explicit discussion of obstacles to poly time.
- E. M. Luks, *Isomorphism of graphs of bounded valence can be tested in polynomial time*, JCSS 25(1), 1982. Polynomial-time GI for bounded-degree graphs using permutation-group stabilizer-chain techniques; the foundation of all modern GI algorithms.
- J. Köbler, U. Schöning, J. Torán, *The Graph Isomorphism Problem: Its Structural Complexity*, Birkhäuser 1993. Complexity-theoretic placement of GI (lowness, unlikely NP-completeness).
- D. Neuen, P. Schweitzer, *An exponential lower bound for individualization-refinement algorithms for graph isomorphism*, ICALP 2017 (verify exact venue/author order). Shows CFI-type graphs defeat standard IR/backtracking paradigms, delimiting naive approaches.
- B. McKay, A. Piperno, *Practical graph isomorphism, II*, J. Symb. Comput. 60, 2014. The nauty/Traces practical canonizers; context on heuristic state of the art.

## Warnings

- Beware claimed "poly-time GI" proofs — there is a long history of erroneous attempts, especially those implicitly assuming WL/individualization-refinement suffices; it provably does not for fixed dimension.
- "Polynomial time" must be worst-case with a fixed exponent; algorithms poly in n but exponential in degree, genus, etc., are known and don't count.
- Babai's original 2015 preprint contained an error (in the Split-or-Johnson lemma area), fixed in 2016 — always cite/use the corrected version.
- The census record is informal; the accepted formal target is deterministic worst-case poly time for simple undirected graph isomorphism, from which colored/directed variants follow by reduction.

---
*`ALGO-000029` · unverified*

## Acceptance guidance

1. **Upper bound (main):** a proof that a specific deterministic algorithm decides GI on all n-vertex graphs in time n^c for an absolute constant c, with correctness proof.
2. **Lower bound variant:** a proof that GI is NP-complete (would also "settle" the census question negatively for P) — considered unlikely, as it collapses PH.
3. Any of: poly-time canonical labeling; GI ∈ coAM-collapsing improvements; or showing GI complete for a natural subclass of P.
A referee would require: full correctness proof (Babai's own 2015 preprint needed a patch — scrutiny is intense), worst-case guarantee, and handling of all coherent-configuration degenerate cases.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/e9dcf17c-2e24-431e-8a70-46f6b1a2a4f2?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000029.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000029)
