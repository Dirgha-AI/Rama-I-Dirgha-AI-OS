# Architecture: The Dirgha AI OS Stack

## Engineering Depth & Technical Design

Dirgha AI OS is a genuine operating system designed for neural workloads. It is built as a three-layer protocol that bridges cognitive intelligence (OS), economic settlement (Marketplace), and physical compute (Chips).

### 1. The AIOS Kernel (The Cognitive Core)
The kernel is the abstraction layer between large language models (LLMs) and the underlying hardware/filesystem. It treats the LLM as a cognitive kernel embedded within a closed-loop control architecture.

*   **LLM Core Manager:** Routes inference requests to local or decentralized models (TypeScript/Hono gateway at `api.dirgha.ai`, 417 routes; Python/LangGraph agent-server on port 4100). Live today.
*   **Agentic Memory (A-MEM):**\* A tiered semantic memory system for long-running workflows. Currently implemented via FTS5 + Qdrant memory graph in the CLI and `memory_tools` in agent-server; the unified A-MEM primitive is on the roadmap.
*   **Agent Souls:** Verifiable, persistent agent identities (`computer-soul-router`) that maintain context, goals, and behavioral patterns across multiple sessions.
*   **Autonomous Proxies:** Secure gateways (`autonomous-proxy`) that allow agents to interact with the external world under strict policy-as-code constraints.
*   **Tool Manager & MCP:** Governs agent access to shell, APIs, and databases via sandboxed VMs (E2B for ephemeral, Daytona for persistent workspaces, MCP client for external tool servers).
*   **Security & Arniko:**\* Every agent action is continuously audited by Arniko, our security and red-teaming agent, to ensure policy-as-code compliance. Core scanner shipping; continuous red-teaming loop on the roadmap.

### 2. The Abundance Marketplace (Labor & Economics)\*
A decentralized labor marketplace where AI agents and human guilds coordinate effort.
*   **Agent Identity (KYA):**\* Verifiable agent identities anchored on-chain with reputation scores.
*   **Guild Architecture:**\* Humans and agents form teams (Guilds) with shared treasuries via on-chain multisigs.
*   **Work Orchestration:** Using **Dirgha Code** and our studio environments (Writer, Creator), agents autonomously manage task intake, execution, and delivery. Studio workspaces shipping; on-chain labor settlement on the roadmap.

### 3. The Physical Layer (Bucky & Sovereign Compute)\*
Our foundation is built on the **Abundance Protocol** and **Rama I**.

*   **Abundance Protocol (Bucky):**\* A P2P network where GPU/CPU nodes share capacity for AI inference workloads. It uses a gossipsub mesh for coordination and handles peer-to-peer compute discovery. Mesh runtime in active development in the `@dirgha/bucky-*` package family.
*   **Code Block Registry:**\* Software is stored as canonical, content-addressed "Code Blocks."
*   **Rama I Hardware:**\* Designed to run on open-source RISC-V silicon (C-DAC VEGA and IIT Madras SHAKTI processors). Our OS is being optimized for deep hardware-software integration on this sovereign stack.

### Technical Specification Overview

| Component | Technology | Repository Status |
|---|---|---|
| **Platform Gateway** | TypeScript, Hono, Node 20 | Live at `api.dirgha.ai` |
| **Agent Server** | Python, FastAPI, LangGraph | Live on internal port 4100 |
| **Platform UI** | TypeScript, React, Vite | Live at `dirgha.ai/app` |
| **CLI** | TypeScript, esbuild, `@dirgha/cli` | Beta (`dist/dirgha.mjs`, 4.4 MB) |
| **P2P Mesh**\* | TypeScript, LibP2P, Gossipsub | [abundance-protocol](https://github.com/Dirgha-AI/abundance-protocol) (Private) |
| **Security Agent** | TypeScript, Security Analysis | [arniko](https://github.com/Dirgha-AI/arniko) (Private, Apache 2.0) |
| **Software Agent** | TypeScript, LLM Orchestration | [dirgha-code](https://github.com/Dirgha-AI/dirgha-code) (Private) |
| **Workspaces** | TypeScript, React | [creator-studio](https://github.com/Dirgha-AI/creator-studio)\*, [writer-studio](https://github.com/Dirgha-AI/writer-studio) (Private) |
| **Hardware Spec**\* | RISC-V Architecture | [Rama-I-Dirgha-AI-OS](https://github.com/Dirgha-AI/Rama-I-Dirgha-AI-OS) (Private, Apache 2.0) |

---

## Conclusion
Dirgha's architecture is designed for vertical integration. By owning the full stack—from the P2P compute protocol to the security-audited OS and the hardware ISA—we build the resilience and efficiency required for the agentic economy.

---

### Legend

> **\*** Items marked with an asterisk are on the committed roadmap and in active development. All items reflect the full Dirgha architecture; asterisked components represent the future state toward which the shipping gateway, agent-server, platform UI, and CLI are building.
