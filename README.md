# Fast and Fair Randomized Wait-Free Locks

This repository is an exploratory Python implementation inspired by the paper **Fast and Fair Randomized Wait-Free Locks** by Naama Ben-David and Guy E. Blelloch ([arXiv:2108.04520](https://arxiv.org/abs/2108.04520)).

The goal is to study the paper's lock-acquisition ideas, fairness model, randomized progress argument, and contention assumptions through readable code and small experiments.

## Scope

This repository should be treated as an educational implementation, not as a drop-in synchronization primitive for production Python applications.

It is intended to help explore:

- randomized lock acquisition;
- fairness under contention;
- bounded-attempt reasoning;
- multi-lock acquisition;
- the distinction between algorithmic progress guarantees and runtime behavior.

## Important Limitations

- A Python implementation does not by itself reproduce the paper's formal machine model or prove the same wait-free guarantees.
- Python interpreter scheduling, operating-system scheduling, blocking I/O, and implementation details can affect observed progress and fairness.
- No maintained benchmark report is currently included.
- No formal verification or proof artifact is included.
- Experimental results should not be generalized beyond the documented workload, runtime, hardware, and random seed.

## Evaluation Requirements

A reproducible evaluation should include:

1. deterministic random seeds;
2. clearly defined worker and contention models;
3. success and failure counts for acquisition attempts;
4. per-worker wait-time and completion distributions;
5. comparison with a simple baseline lock strategy;
6. repeated runs across several contention levels;
7. Python, operating-system, and hardware details;
8. raw machine-readable results in addition to summary charts.

## Correctness Tests

The implementation should be tested for properties that can be observed at the program level, including:

- protected critical sections do not overlap when mutual exclusion is expected;
- multi-lock acquisition uses a consistent ownership model;
- failed attempts do not leave locks partially owned;
- repeated acquisition and release returns the system to a reusable state;
- invalid inputs fail clearly;
- seeded experiments are reproducible.

These tests support implementation confidence but do not replace the paper's proof.

## Suggested Experiment Structure

```text
benchmarks/
  compare_baselines.py
  workloads.py

results/
  raw/
  summaries/

tests/
  test_mutual_exclusion.py
  test_failed_attempt_cleanup.py
  test_seed_reproducibility.py
```

Results and charts should be committed only with the exact command, configuration, and environment needed to reproduce them.

## Research Notes

When comparing the code with the paper, keep the following questions explicit:

- What is the modeled point contention?
- How many locks can a single attempt request?
- Which events are randomized?
- What causes an attempt to fail?
- Which assumptions belong to the algorithm and which belong to the Python runtime?
- Is fairness measured as probability of success, waiting time, or observed completion order?

## Status

Exploratory research implementation. The next meaningful milestone is a reproducible correctness-test and benchmark suite with documented baselines and raw results.

## License and Attribution

Review the repository license before reuse. The paper, third-party code, and any referenced datasets or tools retain their own licenses and attribution requirements.
