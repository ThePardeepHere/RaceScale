# Testing, failure reproduction, and benchmarks

[Documentation home](README.md) | [Scenario catalogue](scenarios/README.md) | [Scenario template](scenarios/TEMPLATE.md)

A scenario is complete only when it demonstrates the failure in a controlled environment, verifies the fix, and explains the limit of the evidence. The names **bad** and **good** are contextual, not performance guarantees.

## 1. Test layers

| Layer | Purpose | Example |
| --- | --- | --- |
| Unit | Confirm a bounded rule or pure function | Reservation transition rules |
| PostgreSQL integration | Verify database semantics | Uniqueness, transaction isolation, row locking |
| API integration | Verify HTTP behavior and persistence | Idempotent POST status and response replay |
| Concurrency | Force deterministic overlap | Two transactions competing for final seat |
| Queue/failure | Check retries and partial failure | Worker exits after commit but before ACK |
| Load/benchmark | Measure bottleneck under controlled workload | p95 and throughput at fixed arrival rate |
| Security | Verify authorization boundaries | Other user's booking ID rejected |

Concurrency and locking claims must be tested against **PostgreSQL**, not inferred from SQLite or a mock database. Tests must explicitly force overlap where applicable rather than hope that a race occurs by chance.

## 2. Bad-case evidence

- Describe the invariant and the exact condition that violates it.
- Run bad behavior only on isolated, synthetic, disposable data.
- Preserve a failing assertion, recorded output, or trace that demonstrates the observed problem.
- Mark the unsafe implementation clearly and ensure it cannot be mistaken for the normal booking path.
- Explain the root cause using the actual transaction, event, or call sequence.

## 3. Good-case evidence

- Use the **same business requirement** as the bad case.
- Test both success and conflict/failure outcomes, including concurrent retries when relevant.
- State what is guaranteed and what is not. For example, at-least-once queue delivery may require idempotent consumers rather than implying exactly-once task execution.
- Describe new failure modes or costs introduced by the fix.

## 4. Benchmark record

For each performance experiment, record a machine-readable result and a readable summary containing:

| Field | Examples of required context |
| --- | --- |
| Environment | OS, CPU, memory, Python/DB versions, container limits |
| Version | Git commit SHA and active configuration |
| Dataset | Event/seat counts, indexes, data distribution |
| Workload | Arrival rate, concurrency, request mix, duration, warmup |
| Metrics | Throughput, p50/p95/p99 latency, errors, DB/worker load |
| Before and after | Same hardware, dataset, workload and measurement method |
| Confidence | Repeats, variability, bottleneck notes, limits of interpretation |

Never label example or illustrative numbers as measured results. A throughput increase does not prove correctness, and one high-load local benchmark does not prove production scalability.

## 5. Documentation update checklist

- [ ] Link the selected GitHub issue and actual code paths.
- [ ] Explain the bad case, root cause, good case and why the fix works.
- [ ] Include exact verified reproduction and test commands.
- [ ] Include outputs or stored results, not invented examples presented as evidence.
- [ ] Document trade-offs, alternatives and known edge cases.
- [ ] Update category page and dashboard metadata to verified only after evidence exists.

Use the [scenario template](scenarios/TEMPLATE.md) for each implemented lesson.
