# PISO Connect

### Security Policy Enforcement for AI Systems

PISO Connect is a lightweight security package that allows developers to
control what an AI agent or AI application is allowed to do.

An AI system can request an action.

PISO checks the policy.

The action is either:

- ALLOW
- DENY

```text
AI System
    │
    │ Action Request
    ▼
┌─────────────────┐
│   PISO Connect  │
│                 │
│  Agent          │
│  Action         │
│  Policy         │
└────────┬────────┘
         │
    ALLOW / DENY
         │
         ▼
      Tool / API
