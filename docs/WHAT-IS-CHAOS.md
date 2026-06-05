# What is CHAOS?

CHAOS is a **local-first AI infrastructure layer for software work**.

The simplest way to explain it is:

> **The LLM is the brain. CHAOS is the nervous system that helps the brain sense, remember, coordinate, and act.**

<p align="center">
  <img src="../assets/chaos-infographic.jpeg" alt="CHAOS nervous system concept diagram" width="560">
</p>

An LLM can reason, write, plan, and explain. But by itself, it often has weak continuity. It forgets the working context between sessions, needs the same project details repeated, struggles to coordinate several workstreams at once, and leaves users with limited visibility into what happened and why.

CHAOS is designed around the missing operating layer around that intelligence: persistent context, orchestration, automation, auditability, and local-first control.

## The Core Idea

Most AI tools focus on the model conversation. CHAOS focuses on the system around the conversation.

It asks a different question:

> What infrastructure would make AI assistance more consistent, less wasteful, and easier to trust across real development work?

The answer is a runtime environment that gives AI work stronger continuity and clearer operating structure.

At a public-safe level, CHAOS brings together:

- persistent context memory,
- tiered context injection,
- multi-agent and multi-repository orchestration,
- coordination across local machines,
- automated workflows,
- auditable development history,
- provider-aware execution,
- and local-first user ownership.

## Deployment Strategy

CHAOS is intended to run locally, with a deployment model that fits existing developer workflows.

At a public-safe level, the product shape is:

- **Docker container deployment** for local platform services.
- **Local MCP server** for exposing CHAOS capabilities to compatible AI tools.
- **Localhost web interface** for operating and inspecting the runtime in a browser, including the Codex browser.
- **Existing provider interface integration** so users can keep working through their preferred AI development tools, IDEs, and CLIs.
- **Cross-platform MCP compatibility** across Windows, macOS, and Linux.

The goal is not to force a new isolated workspace. CHAOS is meant to plug into the AI development surfaces people already use and give those surfaces stronger memory, orchestration, automation, and auditability.

## Brain And Nervous System

The brain metaphor is useful because it separates intelligence from coordination.

| Role | What it provides |
|------|------------------|
| **LLM as brain** | Reasoning, language, coding, planning, synthesis, critique. |
| **CHAOS as nervous system** | Memory, signal routing, task coordination, workflow automation, state tracking, and feedback loops. |

The brain is more effective when it receives the right signals at the right time. CHAOS is built around that principle.

Instead of making every AI session reload an entire project or rely on whatever the user can remember to paste into the prompt, CHAOS treats context as an operational resource. It can be stored, ranked, budgeted, injected, refreshed, and audited.

## What CHAOS Gives The AI

CHAOS is intended to help an AI assistant work with better conditions:

- **Better memory:** useful project facts can persist beyond a single chat.
- **Better context:** relevant material can be selected and injected instead of dumping everything into the model.
- **Better coordination:** work can be routed across agents, repositories, sessions, and machines.
- **Better process:** planning, implementation, testing, review, documentation, and handoff can become repeatable workflows.
- **Better feedback:** events, decisions, and state transitions can be visible instead of hidden inside a chat transcript.

This makes the AI less dependent on fragile prompt memory and more supported by a durable runtime around it.

## What CHAOS Gives The User

For users, CHAOS is about turning AI-assisted development from scattered conversations into an operated system.

It is designed to support:

- fewer repeated explanations,
- cleaner continuity between sessions,
- clearer work ownership across parallel tasks,
- more disciplined development records,
- more automatable workflows,
- and stronger local control over project data.

The goal is not just to make the AI "smarter." The goal is to make the whole working environment more reliable.

## What CHAOS Gives Providers

CHAOS can also be a win for AI providers.

When context is handled carelessly, models receive too much irrelevant input, users burn through subscription allotments, and providers absorb unnecessary compute pressure. Better infrastructure can reduce that waste.

CHAOS is built around the idea that efficient AI use should benefit both sides:

- users get more useful work per session,
- providers see less avoidable token strain,
- hardware resources are used more intentionally,
- and higher-quality context can improve output without simply increasing prompt size.

In other words: better AI infrastructure can help the brain perform at a higher level while conserving the resources needed to run it.

## Major Public-Safe Components

The private implementation is not reproduced in this showcase, but the major concept areas are safe to describe.

| Component Area | Public-Safe Role |
|----------------|------------------|
| **Context memory** | Stores and retrieves durable project knowledge across sessions. |
| **Context injection** | Selects relevant context under a budget so the AI receives useful signal instead of raw noise. |
| **Orchestration runtime** | Coordinates work across agents, tasks, repositories, and execution states. |
| **MCP server** | Exposes local capabilities through an AI-tool-compatible protocol boundary. |
| **Local web interface** | Gives users an operational surface for the runtime through localhost, including Codex browser use. |
| **Provider and CLI integration** | Connects CHAOS into existing AI provider development interfaces, IDE flows, and command-line tools. |
| **Automation layer** | Turns repeatable development activities into structured workflows. |
| **Sync and clone coordination** | Supports parallel work across related local repositories and machines. |
| **Audit and history layer** | Preserves what happened, when it happened, and why it mattered. |
| **Dockerized local platform** | Keeps the operating center on the user's machine with portable local deployment across major operating systems. |

## What CHAOS Is Not

CHAOS is not just:

- a prompt library,
- a chatbot wrapper,
- a single-model interface,
- a cloud-only SaaS dashboard,
- or a collection of disconnected scripts.

It is better understood as an operating layer for AI-assisted software work.

## Short Version

CHAOS is a local-first nervous system for AI-assisted development: it gives the LLM persistent memory, structured context, orchestration, automation, and auditability so AI work becomes more efficient, repeatable, and trustworthy.
