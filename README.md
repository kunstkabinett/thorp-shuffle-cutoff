# When does a shuffled deck forget its order?

Take a deck of 256 cards and give it the Thorp shuffle: cut it in half, pair the two halves card by card, and toss a fresh coin to decide which card of each pair goes first. After eight shuffles every card is equally likely to be in every position. Yet almost every ordering of the deck is still impossible. How many more shuffles does it take before the deck as a whole is random?[^openai-2026]

For $N=2^d$ cards, a single card is uniform after $d$ shuffles. Counting coin tosses shows that the whole deck is still far from uniform after $(2-\varepsilon)d$ shuffles: there are too few outcomes to cover the $N!$ orderings.[^openai-2026] This agenda proposes that the count is sharp, and that the deck becomes random abruptly at $2d$ shuffles. That is, for every fixed $\varepsilon>0$, the total-variation distance from uniform tends to zero after $(2+\varepsilon)d$ shuffles. Such a sudden transition is called *cutoff*.

The best upper bounds are far from $2d$. Morris proved $O(d^3)$.[^morris-2013] Two recent OpenAI preprints claim the right order, with constants $1600$ and $512$.[^openai-2026][^frames-2026] They have not been independently checked, and they settle neither the leading constant nor whether the transition is sharp.

The conjecture would fail on a single example and follow from a single estimate. Each is a problem here:

- **[Find a correlation that survives.](https://github.com/kunstkabinett/thorp-shuffle-cutoff/issues/2)** An event about the final deck whose probability stays a fixed distance from uniform after $(2+\varepsilon)d$ shuffles would refute cutoff at $2d$.
- **[Close the gap from above.](https://github.com/kunstkabinett/thorp-shuffle-cutoff/issues/3)** Prove that $(2+\varepsilon)d$ shuffles suffice, or locate and remove one specific loss in the existing proofs.

The [reading notes](writeups/literature.md) record what each source proves, and where.

[^openai-2026]: OpenAI, *Optimal-order mixing of the Thorp shuffle* (2026), September 26 research preprint; Theorem 1.1, §2 and §§4–7. [Pinned paper](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Optimal-order-mixing-of-the-Thorp-shuffle-September-26-2026/paper.pdf).
[^morris-2013]: Ben Morris, *Improved mixing time bounds for the Thorp shuffle*, **Combinatorics, Probability and Computing** 22 (2013), 118–132; [author preprint](https://arxiv.org/abs/0912.2759v1), §4, Theorem 8.
[^frames-2026]: OpenAI, *Random coordinate frames and partial permutation laws* (2026), September 26 research preprint; Corollary 11.4. [Pinned paper](https://github.com/openai/math/blob/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb/preprints/Random-coordinate-frames-and-partial-permutation-laws-September-26-2026/main.pdf).
