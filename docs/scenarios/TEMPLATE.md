# Scenario ID: Short name

> **Template only.** Copy this page when a specific scenario is selected. Replace every placeholder with evidence. Do not mark unimplemented work as complete.

**Category:** Category name  
**GitHub issue:** Link to canonical ticket  
**Status:** Planned / In progress / Verified  
**Prerequisites:** Dependencies and environment

## 1. Requirement and invariant

Describe the business operation and the condition the system must preserve. State explicitly what counts as a correct outcome.

## 2. Bad case

Describe the smallest intentionally unsafe or inefficient implementation. Explain how to run the controlled experiment locally and what output should show the failure. Keep unsafe routes disabled in normal operation.

## 3. Root cause

Explain the actual database, networking, concurrency, or runtime behavior that caused the problem. Separate observed outcomes from hypotheses.

## 4. Good case

Link the implemented fix, explain its mechanism, and state the guarantees it provides. Include cases the solution does **not** handle.

## 5. Alternatives and trade-offs

| Approach | Benefits | Costs or limitations | When appropriate |
| --- | --- | --- | --- |
| Bad approach | | | |
| Chosen approach | | | |
| Alternative | | | |

## 6. Verification and reproduction

- **Environment:** OS, relevant versions, PostgreSQL isolation level, worker counts, hardware where material.
- **Test command:** The exact command that was run.
- **Experiment:** Dataset size, request rate or concurrency, duration, fixtures, and failure injection.
- **Expected result:** The business invariant or metric being verified.
- **Observed result:** Actual test output or recorded data. Do not invent numbers.
- **Limitations:** Cases not covered by the experiment.

## 7. Evidence

Link test files, relevant source paths, benchmark outputs, related commits, and the GitHub issue. Add trace or dashboard links only when they exist.

## 8. Follow-up

Document unresolved trade-offs or the next related scenario, without implementing unrelated functionality in this issue.
