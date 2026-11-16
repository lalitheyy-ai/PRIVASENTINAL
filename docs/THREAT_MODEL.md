# Initial Threat Model

> Initial working notes for MVP planning. Validate and expand these assumptions before any real-world deployment.

## Assets to protect

- User-provided text and documents.
- Detected personal identifiers, credentials, and financial data.
- Policy configuration and allow/block decisions.
- Audit events and operational metadata.

## Trust boundaries

- User input into the application.
- Browser/UI to backend processing (if a backend is introduced).
- Application to any external AI/model provider.
- Application to logs, analytics, and persistent storage.

## Threats and mitigations

| Threat | Example | Initial mitigation |
|---|---|---|
| Sensitive data exposure | Raw text appears in logs | Redact or omit raw content from logs by default |
| Unsafe external processing | Text is sent to a third-party model without awareness | Disable external calls by default; require explicit opt-in and clear disclosure |
| Incorrect detection | A secret is missed | Combine pattern checks with measured evaluation; state limitations |
| False positive | Harmless text is blocked | Explain findings and support controlled review/override |
| Redaction bypass | Offsets or encodings evade matching | Normalize carefully, validate offsets, test adversarial samples |
| Malformed input | Oversized or malformed payload | Enforce size/type limits and robust parsing |
| Policy confusion | Model output directly authorizes a send | Keep policy decisions deterministic and independently testable |
| Audit leakage | Audit event stores sensitive spans | Store category, rule, and outcome rather than raw values |

## Out of scope for the first demo

- Production endpoint monitoring or network interception.
- Claims of comprehensive detection across all languages, encodings, or file types.
- Automatic blocking of third-party applications.
- Compliance certification or legal assurance.

## Release gate

Before using real sensitive information, complete a privacy review, threat-model review, access-control design, retention policy, secure logging review, and documented evaluation on representative test data.
