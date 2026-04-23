# The Dark Factory: Autonomous Sovereign Manufacturing

## The Vision: Atoms Managed by Bits

The ultimate goal of the Dirgha Manufacturing stack is to enable the **Dark Factory**—a fully autonomous, AI-run manufacturing facility that operates with minimal human intervention. We are building the transition layer for Indian manufacturers to move from manual operations to digital visibility, and finally to full autonomous sovereignty.

In a "Dark Factory," the lights stay off because the agents don't need them to see. They manage the supply chain, quality control, maintenance, and production 24/7.

---

## 🏗️ The 3-Stage Roadmap: From Digital to Dark

### Stage 1: Digital Visibility (Current Scaffolding)
Most Indian SMEs are "offline." Our first step is digitizing the current state of play.
*   **Agentic ERP:** Deploying the **World ERP (Manufacturing Module)** to track inventory, BOM (Bill of Materials), and orders in real-time. Mission Control dashboard, RFQ, Work Orders, Production Schedule, BOM Manager, Inventory, and Quality Control modules are scaffolded today at `/app/factory`.
*   **Supplier Orchestration:**\* Using agents to scout and coordinate with local Indian suppliers through the **Abundance Marketplace**\*.
*   **Hardware BOM Tracking:**\* Digital transparency for every component, enabling the **DVA (Domestic Value Addition)** tracker target for Rama I.

### Stage 2:\* AI-Assisted Orchestration (12-24 Months)
Moving from tracking to active optimization.
*   **Predictive Maintenance:**\* Integrating IoT sensors into legacy machinery. Agents analyze vibration and thermal data to predict failures before they happen.
*   **Agentic QC (Quality Control):**\* Computer vision agents (integrated into the **Dirgha AI OS**) perform real-time visual inspection of PCBs and enclosures on the assembly line.
*   **Dynamic Supply Chain:**\* Agents autonomously renegotiate with suppliers based on real-time price fluctuations and logistics delays.

### Stage 3:\* The Dark Factory (36+ Months)
Full autonomy and sovereign operation.
*   **Lights-Out Production:**\* The **AIOS Kernel** directly controls the robotics and CNC machines on the factory floor.
*   **Autonomous Resource Allocation:**\* The factory autonomously bids for compute on the **Bucky Mesh** to run its own optimization models.
*   **Sovereign Resilience:**\* The entire factory runs on **Rama I** sovereign computers. It is not dependent on foreign cloud providers or proprietary software. If the external internet goes dark, the factory keeps running.

---

## 🛠️ Current Capabilities

Dirgha already has the foundational routes and logic in our gateway to support this transition:

| Capability | Module / Route | Description |
|---|---|---|
| **BOM Management** | `hardware-bom.ts` | Structuring and tracking complex hardware components. |
| **Supplier Scouting** | `supplier-scout-agent.ts` | Autonomous agents identifying and vetting Indian manufacturers. |
| **Manufacturing ERP** | `mcp-erp-gateway.ts` | The bridge between the AIOS Kernel and physical factory operations. |
| **Quality Verification** | `verifier.ts` | Protocols for autonomous and human-in-the-loop quality checks. |
| **Inventory & POS** | `kirana-pos.ts` | Real-time tracking of raw materials and finished goods. |

---

## 🇮🇳 Why India? Why Now?

India's manufacturing sector is at a tipping point. With the **India Semiconductor Mission (ISM 2.0)** and the **C2S Programme**, the government is funding the talent and the fabs. But the "Coordination Gap" remains.

**Dirgha closes this gap by providing:**
1.  **The Brain (Dirgha AI OS):** To manage the complex orchestration of a modern factory.
2.  **The Infrastructure (Bucky/Abundance):** To settle payments and compute without middlemen.
3.  **The Blueprint (Open Source):** To allow any city to replicate a "Dark Factory" locally.

### The Economic Impact: Sovereign Abundance
A network of local, autonomous "Dark Factories" creates a resilient national infrastructure. It lowers the cost of production by eliminating human-intensive overhead and middleman margins. It turns manufacturing from a "labor arbitrage" game into an "intelligence orchestration" game.

**Dirgha — Orchestrating the Atoms.**


---

### Legend

> **\*** Items marked with an asterisk are on the committed roadmap and in active development. All items reflect the full Dirgha vision; asterisked items are not yet shipping in production. What ships today runs at [dirgha.ai/app](https://dirgha.ai/app). Repositories live under the [Dirgha-AI GitHub organization](https://github.com/Dirgha-AI).
