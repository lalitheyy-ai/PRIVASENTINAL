# Proposed MVP Architecture

> This is a design proposal, not a description of implemented code. The repository currently contains only the project README.

## Data flow

1. **Input adapter** receives a user-provided text sample.
2. **Detector** identifies candidate sensitive spans using deterministic patterns and optional future model-assisted signals.
3. **Classifier** assigns a category, confidence, and severity to each finding.
4. **Policy engine** decides whether to allow, warn, redact, or block.
5. **Redactor** produces a protected preview while preserving the original input only for the minimum time required by the active session.
6. **Audit event builder** records the policy decision and non-sensitive metadata.
7. **Dashboard** presents findings, explanations, and aggregate events.

## Suggested module boundaries

```text
src/
  app.py
  detection/
    patterns.py
    detector.py
  classification/
    taxonomy.py
    classifier.py
  policy/
    rules.py
    evaluator.py
  protection/
    redactor.py
  audit/
    events.py
  ui/
    dashboard.py
 tests/
```

## MVP interface contracts

A finding should include a category, start/end offsets, severity, confidence, and a short explanation. A policy decision should include an action, rule identifier, and human-readable reason. Keep raw matched values out of logs by default.

## Security boundaries

- Treat uploaded or pasted text as untrusted input.
- Validate offsets before redaction and ensure the protected output does not accidentally retain matched values.
- Keep model-assisted classification separate from deterministic policy enforcement.
- Do not execute or interpret scanned content.
- Avoid logging raw input, credentials, or full sensitive spans.
- Make external processing opt-in and disclose what is sent, to whom, and why.

## Evaluation

Create a synthetic test corpus with positive and negative examples. Track precision, recall, false-positive rate, false-negative rate, and redaction leakage. Do not claim production-grade DLP performance from a small demo corpus.
