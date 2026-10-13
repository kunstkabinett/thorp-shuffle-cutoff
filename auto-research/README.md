# Research attempts

Read [the agent guide](../auto-research.md) for this agenda's research tracks and evidence requirements. Search the relevant track, question issues, claims and open pull requests before starting a new attempt.

Use one directory per attempt, creating the track directory when its first contribution is ready:

```text
auto-research/<track>/<YYYY-MM-DD>-<handle>-<slug>/
  README.md
  verify.py or verify.sh    # for computational results
  code/                    # as needed
  data/                    # as needed
  evidence/                # as needed
```

Use a track named in the agent guide. Propose a new track only when the agenda's scope permits it and explain which question it serves. Use a unique slug for each attempt; preserve earlier results and link follow-ups to them.

Each attempt's README should state:

- **Question and outcome:** link the question and claim issues, summarize the finding, and say whether it is proved, conditional, computational, a failed approach or incomplete.
- **Method and scope:** what was tried, the assumptions, parameter ranges, seeds, stopping rule and completed coverage.
- **Evidence:** a command run from the repository root, dependencies and expected output for computations; a complete argument or a link to its exact version for proofs. Include relevant error bounds and checks that catch incorrect results.
- **Provenance:** base commit, source and dependency versions, contributor credits, agent and model used, and time or compute cost when available.
- **Limits and next step:** what remains unchecked, why an approach failed or stopped, and what would justify revisiting it.

A failed search rules out only what it actually checked. Do not describe sampled cases as a proof or incomplete work as a negative result. Commit the evidence needed for review, with pinned references for large external artifacts. Keep credentials and private session transcripts out of submissions.

Questions and claims remain in GitHub issues; code and evidence arrive through pull requests. Link longer exposition in `writeups/` when present, or other existing proof files, rather than copying it into several places. A folder's existence does not mean its result has been accepted or independently reproduced.
