# Fast and Fair Randomized Wait-Free Locks

> **Project status:** Frozen research artifact. Active development is closed for the current cycle.

This repository preserves the referenced paper and the scope notes used to study **Fast and Fair Randomized Wait-Free Locks** by Naama Ben-David and Guy E. Blelloch.

It does **not** currently contain a validated executable implementation, benchmark suite, formal proof artifact, or production synchronization primitive.

## Reference

- Paper: *Fast and Fair Randomized Wait-Free Locks*
- Authors: Naama Ben-David and Guy E. Blelloch
- arXiv: https://arxiv.org/abs/2108.04520

## Research questions

If this work is resumed, the implementation should make these points explicit:

- the modeled contention level;
- how many locks an attempt may request;
- which events are randomized;
- what causes an acquisition attempt to fail;
- which assumptions come from the algorithm and which come from the runtime;
- how fairness is measured.

## Requirements for a reproducible implementation

A future implementation should include:

1. deterministic random seeds;
2. clearly defined worker and contention models;
3. mutual-exclusion and cleanup tests;
4. per-worker wait-time/completion measurements;
5. a simple baseline lock strategy;
6. repeated runs across several contention levels;
7. runtime, operating-system, and hardware details;
8. raw machine-readable results alongside any summary charts.

Passing program-level tests would improve implementation confidence, but would not reproduce or replace the paper's formal proof.

## Current boundary

This repository is intentionally frozen at its current scope. No wait-free, fairness, performance, or production-suitability claim should be inferred from it.

If development resumes, the first meaningful milestone should be a small executable implementation with correctness tests and fully reproducible benchmark inputs/results.

## License and attribution

Review the repository license before reuse. The paper and any third-party material retain their own licenses and attribution requirements.
