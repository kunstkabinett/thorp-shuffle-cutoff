# Reading notes and scope

Reviewed October 11, 2026. This is a brief review supporting an agenda, not an exhaustive novelty check. The selected paper’s full text was read, including its figure and references. No formal proof verification or mixing experiment was run.

## The selected paper

OpenAI, *Optimal-order mixing of the Thorp shuffle*, September 26, 2026, OpenAI Math Release preprint, result family 238. [Pinned manuscript](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Optimal-order-mixing-of-the-Thorp-shuffle-September-26-2026/paper.pdf), 14 pages. All seven sections and Figure 1 (page 5) were inspected; there are no appendices. Repository revision: `fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb`.

Theorem 1.1 claims full-permutation total-variation convergence after 1600d physical shuffles on N = 2^d cards, as d tends to infinity. It also gives the support lower bound 1 − 2^(tN/2)/N!. Section 2 proves exact one-card uniformity after d shuffles and explains the rotating binary-coordinate frame. A complete sweep takes d physical shuffles. Translation of the starting deck leaves distance from uniform unchanged.

The proof tracks a hidden card conditional on revealed trajectories (§3), contracts its centered squared mass (§4), and bounds the average error of large ordered-card marginals at 200d (Proposition 4.2). Representation-degree estimates (§5) and a common trimming of complementary marginal laws (§6) feed a Fourier bound. Eight independent time blocks, with parity handled separately, yield the full law (§7). Figure 1 distinguishes an unrevealed switch with two free positions from a switch whose outcome an exposed trajectory fixes.

The introduction explicitly leaves the leading constant and cutoff unresolved. It also excludes arbitrary even deck sizes from its cube argument. Our agenda keeps the power-of-two assumption and proposes the candidate constant two from the support obstruction; the paper does not assert this candidate is correct. Counting histories bounds the support but does not show that the history-to-permutation map distributes its mass evenly.

For the opening example, eight steps on 256 cards use 1024 fair bits, so at most 2^1024 permutations can occur, far fewer than 256!. This is a consequence of the elementary counting argument, not a numerical experiment. Single-card uniformity does not imply independent card positions (even a uniform permutation has the constraint that positions are distinct).

## Literature reviewed

- Ravi Montenegro and Prasad Tetali, *Mathematical aspects of mixing times in Markov chains*, **Foundations and Trends in Theoretical Computer Science** 1(3) (2006), 237–354, [doi:10.1561/0400000003](https://doi.org/10.1561/0400000003). Read the Thorp discussion in §6.4 of the [published survey reprint](https://www.stat.berkeley.edu/~aldous/260-FMIE/Papers/montenegro_tetali.pdf), especially §6.4.1. This supplies the cube model and explains the difficulties for standard spectral methods. An earlier draft uses different section numbering. Its polynomial-in-d bounds are historical, not the current target.
- Ben Morris, *Improved mixing time bounds for the Thorp shuffle*, **Combinatorics, Probability and Computing** 22(1) (2013), 118–132, [doi:10.1017/S0963548312000478](https://doi.org/10.1017/S0963548312000478). Inspected §§1–4 of the [December 14, 2009 preprint, arXiv:0912.2759v1](https://arxiv.org/abs/0912.2759v1), especially Lemma 7 and Theorem 8: an entropy contraction for the reverse shuffle gives O(d³) mixing. Its reverse-step convention differs from the selected paper’s forward convention; both concern complete physical shuffles. Locators refer to the preprint.
- OpenAI, *Random coordinate frames and partial permutation laws*, September 26, 2026 research preprint, [pinned manuscript](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Random-coordinate-frames-and-partial-permutation-laws-September-26-2026/main.pdf). Inspected the introduction, the discussion at the end of the first proof, and Corollary 11.4 with its proof (pages 36–37). It claims 512d full-deck mixing by combining a fixed-list estimate with a companion isotypic Fourier estimate. The selected paper’s 1600 is therefore not the smallest explicit constant claimed by these inspected manuscripts. The companion also explicitly disclaims a sharp leading constant or cutoff. Its full proof has not been reviewed here.

## What remains a proposal

Targeted searches for Thorp-shuffle cutoff and leading constants did not identify a full-deck theorem giving the proposed 2d threshold. Claims about one-card or two-card cutoff do not settle this question. This search is not a claim that no such result exists; contributors should check for subsequent work before claiming novelty.

The small-deck enumeration task, formerly [question 1](https://github.com/kunstkabinett/thorp-shuffle-cutoff/issues/1), is now a preparatory method within question 2, rather than a separate research problem. [Question 2](https://github.com/kunstkabinett/thorp-shuffle-cutoff/issues/2)’s binary-block statistic is our suggested starting point, not an observable supplied by the papers. [Question 3](https://github.com/kunstkabinett/thorp-shuffle-cutoff/issues/3) tests the authors’ explicit unresolved leading-constant question at our proposed threshold. None of the tasks requires treating the recent preprints as established theorems without checking the parts used.

## Source references

[^openai-2026]: OpenAI, *Optimal-order mixing of the Thorp shuffle* (2026), September 26 research preprint; Theorem 1.1, §2 and §§4–7. [Pinned paper](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Optimal-order-mixing-of-the-Thorp-shuffle-September-26-2026/paper.pdf).
[^morris-2013]: Ben Morris, *Improved mixing time bounds for the Thorp shuffle*, **Combinatorics, Probability and Computing** 22 (2013), 118–132; [author preprint](https://arxiv.org/abs/0912.2759v1), §4, Theorem 8.
[^frames-2026]: OpenAI, *Random coordinate frames and partial permutation laws* (2026), September 26 research preprint; Corollary 11.4. [Pinned paper](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Random-coordinate-frames-and-partial-permutation-laws-September-26-2026/main.pdf).
