# PRIVASENTINEL

AI-assisted sensitive-data leakage prevention — project concept and MVP workspace.

> **Status: planning / MVP not yet published.** This repository is currently an empty project workspace. The capabilities below describe the intended product, not features that are already implemented.

## Problem

Sensitive information can be exposed when people paste, upload, or transmit data through digital tools. Teams need a way to identify risky content before it leaves a trusted environment, apply an appropriate policy, and retain an understandable record of decisions.

## Intended MVP

1. **Detection** — identify candidate sensitive data such as personal identifiers, credentials, and financial information.
2. **Classification** — assign categories and risk levels to detected content.
3. **Protection** — redact or block content according to configurable rules.
4. **Explainability** — show what was detected, why it was flagged, and which policy action was taken.
5. **Monitoring** — provide a dashboard for events and policy outcomes.
6. **Audit trail** — record decisions and outcomes without unnecessarily retaining raw sensitive content.

## Proposed engineering principles

- Default to data minimisation; avoid storing raw sensitive content unless strictly necessary.
- Keep detection, policy evaluation, redaction, and user-interface layers separate.
- Make policy actions explainable and testable.
- Treat model output as advisory until validated by deterministic checks and policy rules.
- Never send user content to an external AI provider without clear disclosure and consent.
- Add tests for false positives, false negatives, redaction correctness, and policy edge cases.

## Suggested first milestone

Build a local demonstration that accepts sample text, detects a small set of sensitive-data patterns, displays classifications, and previews redaction. Add unit tests and clearly label the limitations before expanding to model-assisted detection or integrations.

## Suggested stack

A Python-first prototype is a reasonable starting point. The exact framework, model provider, deployment model, and storage design are intentionally left open until the MVP requirements and threat model are agreed.

## Roadmap

- [ ] Define threat model, data categories, and abuse cases.
- [ ] Implement local sample-text scanning.
- [ ] Add classification and deterministic redaction policies.
- [ ] Build an explainable event dashboard.
- [ ] Add tests and security review.
- [ ] Document limitations, privacy controls, and deployment steps.

## Repository note

The repository's current GitHub name is PRIVASENTINAL (spelling retained to avoid an unapproved repository rename). The intended project name in this README is **PRIVASENTINEL**.
