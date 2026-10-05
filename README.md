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
