# Proposed issues — unpublished

These are local drafts using the inherited Problem form. Each has label `question` and the fields Statement, Why it matters, and Further details. Letters identify drafts, not GitHub issue numbers. No proposed task is marked solved.

## Shared setting

Take $N:=2^d$ distinct cards, initially in a fixed order. One **physical shuffle** cuts the deck into equal halves, pairs corresponding positions, and interleaves each pair in a uniformly random order. All $N/2$ coins are independent, with fresh coins at each step. A **sweep** is $d$ physical shuffles, not one shuffle.

Let $q_d$ be the one-step permutation law and $U_N$ the uniform law on the symmetric group $S_N$. Define

$$D_d(t):=\frac12\sum_{\pi\in S_N}\left|q_d^{*t}(\pi)-\frac1{N!}\right|.$$

Composition of independent steps is denoted by convolution. The distance is the same from every deterministic starting order. The proposed cutoff location is $2d$: for each fixed $0<\varepsilon<2$, ask whether

$$D_d(\lfloor(2-\varepsilon)d\rfloor)\longrightarrow1,\qquad D_d(\lceil(2+\varepsilon)d\rceil)\longrightarrow0.$$

The first limit follows from the selected paper’s elementary support bound $D_d(t)\ge1-2^{tN/2}/N!$. The second is the research target, not a consequence of counting random bits. If it holds for these positive ε, monotonicity gives it for all larger ε as well. No claim about the distance exactly at $2d$ or the width of a smaller window is built into this formulation.

References are in the [README](README.md) and [reading notes](writeups/literature.md). The leading-constant and cutoff questions are explicit in OpenAI’s introduction; the particular candidate $2d$ and this decomposition are proposed here.

## Draft A: Find what small-deck marginals fail to detect

### Statement

For four- and eight-card Thorp shuffles, how much total-variation distance is missed by observing only one card or a pair of cards instead of the whole deck?

### Why it matters

Exact finite examples make the gap between marginal randomness and a random permutation visible. They can identify statistics worth studying near the proposed cutoff and provide a reference for later simulations.

### Further details

Use the shared setting above. Start at the identity permutation and enumerate the $2^{N/2}$ possible physical steps. For each time $0\le t\le4d$, propagate integer counts of coin histories, with common denominator $2^{tN/2}$, to compute the full permutation law. Do not assign equal probabilities to reachable permutations: different histories may produce the same permutation.

Compute exact rational values of $D_d(t)$ and the corresponding distances of every one-card and unordered choice of two labels (retaining the ordered pair of their positions). Compare a pair’s law with the uniform injection law on $N(N-1)$ distinct-position pairs. Report the largest two-card distance and which initial pairs attain it. All one-card distances must vanish at $t=d$; parity must already be balanced after one physical step. These are model checks, not evidence of full mixing.

For an independent implementation check, represent positions as binary strings and use $(x_1,u)\mapsto(u,x_1\mathbin\oplus\xi_u)$ with one shared coin for the two endpoints of each pair. Compare this physical update with the cut-and-interleave implementation on all coin choices. Coordinate sweeps agree only after accounting for the deterministic rotation described in OpenAI §2.

Deliver the transition rule, reproducible code, exact distances, and a concrete event witnessing some discrepancy that pairs miss. At eight cards there are $8!=40320$ full states; do not extend this enumeration to sixteen cards without a justified reduction. Small decks can suggest a mechanism but cannot establish an asymptotic cutoff constant.

## Draft B: Detect correlations beyond the counting threshold

### Statement

Is there an explicit event about the final deck whose probability differs from uniform by a fixed positive amount after $\lceil(2+\varepsilon)d\rceil$ shuffles for some fixed $\varepsilon>0$ as $d\to\infty$?

### Why it matters

Such an event would refute cutoff at $2d$. The support count stops being useful there, so any obstruction must capture dependence that survives after enough random bits have been supplied.

### Further details

Use the shared setting above. Start with the block-incidence matrix obtained by dividing both the initial labels and final positions into binary-prefix blocks. For a chosen prefix length $r=r(d)$, define $M_{ab}$ as the number of labels from input block $a$ ending in output block $b$. Derive its uniform-permutation baseline before using a statistic such as $\sum_{a,b}M_{ab}^2$. Explore fixed $r$ first, then a growing $r$ if the fixed-size observation loses its signal too early. Binary coordinates refer to the physical positions at the observation time; account for the rotation when using the cube frame.

A useful witness is a sequence of final-deck events $A_d$ and a constant $c>0$ for which

$$\liminf_{d\to\infty}\left|q_d^{*\lceil(2+\varepsilon)d\rceil}(A_d)-U_N(A_d)\right|\ge c.$$

A difference of expectations alone is insufficient without boundedness or fluctuation control. A statistic depending on hidden coin histories is not an observable event of the final permutation unless it can be recovered from that permutation. Parity and single-card locations cannot work: they become exactly uniform much earlier.

Draft A may suggest better observables; it is not a prerequisite. For exploratory sampling, use independent shuffled decks and independently uniform permutations, keep a separate set of samples for checking a selected statistic, and report sampling uncertainty. A rigorous negative result for a candidate statistic is useful: it explains which correlations a lower-bound proof must go beyond. Failure to find a witness does not prove cutoff.

## Draft C: Bring a full-deck upper bound toward two sweeps

### Statement

Can one prove $D_d(\lceil(2+\varepsilon)d\rceil)\to0$ for every fixed $\varepsilon>0$, or identify and reduce a specific loss that prevents the existing proof from approaching this threshold?

### Why it matters

Together with the support lower bound, the target estimate would settle the root question. Intermediate improvements are valuable when they explain how information about groups of cards controls the full permutation.

### Further details

OpenAI’s selected paper obtains a marginal estimate for a uniformly sampled list of $7N/8$ cards after $200d$ shuffles (Proposition 4.2), then uses eight independent time blocks to obtain its $1600d$ conclusion (§§6–7). The companion *Random coordinate frames and partial permutation laws*, Corollary 11.4, already claims $512d$ using two blocks and a different Fourier estimate. Read that comparison before presenting a constant below 1600 as new.

First produce an explicit accounting of the losses in the selected proof: the conditional energy recurrence (3.2), the contraction estimate (4.3), the sequential total-variation comparison (4.5), the passage to large-card marginals, and the final number of convolution blocks. Identify which losses are numerical slack and which arise from requiring more information or a stronger norm than total variation. The first deliverable is a proved improvement of one stated estimate, or an example showing why a proposed sharpening fails under its stated hypotheses.

An average over randomly chosen input lists is not a bound for every fixed list. Nor do nearly uniform marginals by themselves imply a nearly uniform permutation. Any transfer must state its assumptions, handle the sign representation, and count its additional physical shuffles. Do not assume that the shuffle is reversible or that its Fourier matrices are scalar.

Draft B can reveal an obstruction to the proposed threshold. A full upper-bound proof must be accompanied by a check of every imported lemma; these preprints have been read for agenda design, not independently certified here. Improving a local estimate or obtaining a larger constant than two is partial progress, not a proof of the proposed cutoff.
