# MVP Implementation Plan

> A staged plan for turning the project concept into a demonstrable, testable prototype. No implementation work is represented as complete here.

## Stage 0 — Define scope

- [ ] Agree on initial sensitive-data categories.
- [ ] Define expected input formats and size limits.
- [ ] Write a small synthetic test corpus with positive and negative cases.
- [ ] Define what the demo explicitly does not support.

## Stage 1 — Deterministic scanner

- [ ] Implement pattern-based detection for a small, documented category set.
- [ ] Return structured findings with offsets and explanations.
- [ ] Add tests for valid matches, non-matches, boundaries, and malformed input.

## Stage 2 — Policy and redaction

- [ ] Implement allow, warn, redact, and block policy actions.
- [ ] Implement redaction with offset and leakage tests.
- [ ] Ensure logs do not contain raw sensitive values.

## Stage 3 — Demo UI

- [ ] Build a local interface for sample text input.
- [ ] Show findings, categories, severity, and reasons.
- [ ] Show a redacted preview and policy outcome.
- [ ] Add a basic event history using synthetic/demo data.

## Stage 4 — Evaluation and hardening

- [ ] Measure precision, recall, and false-positive/false-negative rates on the test corpus.
- [ ] Add adversarial and malformed-input tests.
- [ ] Review privacy, retention, and external-provider settings.
- [ ] Document limitations and run instructions.

## Definition of done

A reviewer can run the prototype locally, submit sample text, see explainable findings, preview the policy action, and run automated tests. The README accurately describes what is implemented and what remains future work.
