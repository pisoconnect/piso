# PISO Connect

### Security Policy Enforcement for AI Systems

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Version](https://img.shields.io/badge/version-0.1.0-green.svg)](https://github.com/pisoconnect/piso)

PISO Connect is a lightweight open-source security policy layer for AI systems and AI agents.

It allows developers to define what an AI agent is allowed to do and enforce a security decision before the requested action reaches a tool, API, database, or other external system.

> **AI can request. Policy decides. PISO enforces.**

---

## Why PISO?

AI systems are increasingly capable of using tools, accessing data, calling APIs, and performing actions on behalf of users.

A typical AI system setup often looks like this:

```text
User
  ↓
AI Application
  ↓
AI Agent
  ↓
Tool / API / Database

AI Agent
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

pip install piso-connect

git clone [https://github.com/pisoconnect/piso.git](https://github.com/pisoconnect/piso.git)
cd piso
pip install -e .

from piso import authorize

decision = authorize(
    agent="research-agent",
    action="search_repository"
)

print(decision)
# Output: {"decision": "ALLOW"}

from piso import authorize

decision = authorize(
    agent="research-agent",
    action="delete_repository"
)

print(decision)
# Output: {"decision": "DENY", "reason": "Action is not authorized"}

AI SYSTEM
                     │
                     │ Action Request
                     ▼
              ┌─────────────┐
              │ PISO Connect│
              │             │
              │ Agent       │
              │ Action      │
              │ Policy      │
              └──────┬──────┘
                     │
              ┌──────┴──────┐
              │             │
            ALLOW          DENY
              │             │
              ▼             X
          Tool / API     Blocked

Agent + Action + Policy
          │
          ▼
   PISO Security Decision
          │
      ┌───┴───┐
      ▼       ▼
    ALLOW    DENY

agents:
  research-agent:
    allow:
      - search_repository
      - read_file
    deny:
      - delete_repository
      - delete_database
      - modify_production

AI Agent ───> Database API ───> DELETE

AI Agent ───> PISO Connect ───> Policy Check ───> DENY (Blocked)
                                                     X
                                         Production Database

v0.1 (Current)
Agent + Action + Policy
        │
        ▼
v0.2
Resource Scoping
        │
        ▼
v0.3
Identity + Authority Engine
        │
        ▼
v0.4
Risk Scoring
        │
        ▼
v0.5
Human-in-the-Loop Approval
        │
        ▼
v0.6
Audit Logging & Observability
        │
        ▼
v1.0
Native MCP / API / RAG / Agent Connectors

AI Agent
    │
    │ (MCP Tool Call)
    ▼
PISO Connect
    │
    │ (Policy Decision: ALLOW)
    ▼
MCP Server
    │
    ▼
Tool / API / Database

AI Intent ───> Policy ───> PISO ───> Secure Action
