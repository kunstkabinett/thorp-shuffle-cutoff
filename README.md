# When does a shuffled deck forget its order?

Shuffle a deck of 256 cards eight times. Pick any card: it is equally likely to occupy any position. Yet almost every possible ordering of the deck is still impossible. This happens in the Thorp shuffle, where each step cuts the deck in half and interleaves corresponding pairs, using a fresh coin toss to choose each pair’s order. How much longer does it take to erase the correlations between cards?[^openai-2026]

For $N=2^d$ cards, one card becomes uniform after $d$ shuffles. Counting possible outcomes shows that the whole deck remains far from uniform before $(2-\varepsilon)d$ shuffles, for every fixed $0<\varepsilon<2$.[^openai-2026]

Morris proved an $O(d^3)$ mixing bound.[^morris-2013] OpenAI’s *Optimal-order mixing of the Thorp shuffle* claims an $O(d)$ bound, with an explicit constant of 1600; a companion claims 512.[^openai-2026][^frames-2026] These research preprints leave the leading constant and a possible sharp transition unresolved. Their upper bounds are starting points to scrutinize, not independently certified results of this agenda.

**Root question:** Does the Thorp shuffle have cutoff at $2\log_2 N$ shuffles? Here *cutoff* means that, for every fixed $\varepsilon>0$, the full deck’s distance from uniform tends to zero after $(2+\varepsilon)d$ shuffles, complementing the counting lower bound. Distance means total variation: the largest probability discrepancy over all events about the final deck.

Our proposed route is:

- **[Compute small decks exactly.](https://github.com/public-observatory/thorp-shuffle-cutoff/issues/1)** Find what one- and two-card observations miss about the full distribution.
- **[Look for surviving correlations.](https://github.com/public-observatory/thorp-shuffle-cutoff/issues/2)** Find a statistic that distinguishes the deck from uniform beyond the proposed threshold.
- **[Reduce the upper-bound losses.](https://github.com/public-observatory/thorp-shuffle-cutoff/issues/3)** Identify where the proofs spend extra shuffles and sharpen those steps.

See the [reading notes](writeups/literature.md) and [contribution guide](https://public-observatory.github.io/docs.html).

[^openai-2026]: OpenAI, *Optimal-order mixing of the Thorp shuffle* (2026), September 26 research preprint; Theorem 1.1, §2 and §§4–7. [Pinned paper](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Optimal-order-mixing-of-the-Thorp-shuffle-September-26-2026/paper.pdf).
[^morris-2013]: Ben Morris, *Improved mixing time bounds for the Thorp shuffle*, **Combinatorics, Probability and Computing** 22 (2013), 118–132; [author preprint](https://arxiv.org/abs/0912.2759v1), §4, Theorem 8.
[^frames-2026]: OpenAI, *Random coordinate frames and partial permutation laws* (2026), September 26 research preprint; Corollary 11.4. [Pinned paper](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Random-coordinate-frames-and-partial-permutation-laws-September-26-2026/main.pdf).
