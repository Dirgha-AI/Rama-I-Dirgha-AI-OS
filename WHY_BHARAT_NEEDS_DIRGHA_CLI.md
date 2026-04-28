# Why Bharat Needs a Sovereign Coding CLI

**Dirgha CLI is the kernel of Dirgha AI OS — the Bharati operating system for the agentic era.** Every other piece of this stack — Abundance Protocol, Arniko, Writer Studio, Creator Studio, the Rama I hardware programme — sprouts from it. The CLI is the seed. It is the smallest, most self-contained, most installable piece of the operating system that a single developer can put in their hands today.

This page makes the case for why that matters — for India, and for the next 100 million software workers worldwide. It is meant to be honest about both the opportunity and the limits.

---

## The kernel framing

In the original Linux story, the kernel was not the most exciting part of the operating system. The exciting parts were the desktop environments, the package managers, the application ecosystems that grew on top. But none of those would have existed without a kernel that was open, hackable, and small enough for one student in Helsinki to start writing.

Dirgha AI OS has the same shape. The hardware (Rama I), the peer-to-peer compute layer (Abundance Protocol), the application studios (Writer, Creator, Code), the security layer (Arniko) — these are the user-facing surfaces of the operating system. **The CLI is the kernel that makes them coherent.** It is what an agent uses to read a file, run a tool, switch a model, persist memory, dispatch parallel work. Every higher layer is a CLI invocation, a tool call, or a skill recipe expressed in CLI primitives.

A user-facing OS without a kernel is a poster. A kernel without applications is a curiosity. Both have to exist, and the kernel has to come first.

That is why `@dirgha/code` ships at 543 KB, with one install command, before anything else in the OS goes mainstream. **Build the seed. Make it small. Make it hackable. Let it grow.**

---

## The structural assumptions hidden in today's AI coding tools

Most of the well-known AI coding tools — Cursor, GitHub Copilot, Anthropic's Claude Code, Replit Agent — are excellent products. They were also built around three assumptions that quietly exclude a large fraction of the global developer population:

1. **A fast, low-latency link to a US datacenter.** Most LLM inference happens in `us-east-1` (Virginia) or `us-west-2` (Oregon).
2. **A monthly subscription priced in US dollars.** The starting tier on most assistants is $20–$30/month. Pro tiers go to $200.
3. **Your code and prompts can leave your machine** and traverse the public internet to a vendor's servers.

Those assumptions hold for most developers in San Francisco, Berlin, or Singapore. They hold less well in Pune, Patna, Coimbatore, Lahore, Lagos, and São Paulo.

### Concrete numbers

- A round-trip from Bengaluru to Anthropic's `us-east-1` is **220–280 ms** on a good day, **400+ ms** on a bad one. An agentic loop that fires 6–12 model calls in a turn pays that latency tax repeatedly. Total user-visible delay before any thinking starts: **2–5 seconds per turn**.
- The same loop hitting a model hosted closer — NVIDIA NIM's India edge, an OpenRouter regional shard, or (cleanest case) Ollama on the developer's laptop — lands in **30–80 ms** total.
- A senior IDE assistant subscription at **₹1,800/month** is real money for a self-taught developer working out of a Tier-2 city. The same developer can run `dirgha` against a free-tier model and pay **₹0**.

These aren't marketing claims. They're physics, geography, and price sheets.

---

## What `@dirgha/code` is

A 543 KB tarball you install with one command:

```
npm install -g @dirgha/code
```

It runs in the terminal. It speaks to **17 LLM providers** out of the box (Anthropic, OpenAI, Google, OpenRouter, NVIDIA NIM, Mistral, Cohere, Cerebras, Together, Perplexity, xAI, Groq, Z.AI, Fireworks, DeepSeek, plus local Ollama and llama.cpp). It can read your files, run shell commands, edit code, run your tests, search the web, and chain those together to finish multi-step tasks. It remembers context across sessions, supports parallel agents in git worktrees, and renders markdown + code with syntax highlighting natively in the terminal.

It is open-source. It ships under a [Functional Source License 1.1](https://fsl.software/) that converts to MIT after two years. Contributions are welcomed under a standard CLA.

---

## Why a CLI specifically — not another web app or IDE plugin

Three concrete reasons.

### 1. Lowest-friction surface for a connected agent

A CLI works on a refurbished Dell Latitude in a coworking space on 4 Mbps WiFi. There's no JavaScript engine to load, no WebSocket to keep alive, no Electron app eating 800 MB of RAM. The binary is 543 KB. The agent loop runs over plain HTTPS streaming. It is also the only surface that runs cleanly over SSH on a ₹600/month VPS — which is how a lot of professional Indian software work actually happens (laptop is the editor, VPS is the runtime).

### 2. Composes with what developers already use

`git`, `npm`, `pytest`, `tmux`, `ssh`, `make`, `docker` — every CLI tool a developer already runs in the terminal — combine with Dirgha through shell pipes, scripts, cron jobs, and the agent's own `shell` tool. There is no new IDE to learn, no vendor-locked workflow to adopt, no new mental model.

### 3. The agent layer is contested in a way other layers aren't

The AI stack has at least five layers worth thinking about:

| Layer | Who owns it today |
|---|---|
| 1. Compute (GPUs / clusters) | NVIDIA, AWS, Microsoft, Google. Sovereign Indian capacity is starting to land via MeitY-funded clusters, but is multi-decade work. |
| 2. Frontier models (weights) | US and Chinese labs. India is closing on MoE-style architectures, less so on dense frontier models. |
| 3. Training data | English internet, Wikipedia, GitHub. Indic languages and Indian context are heavily underrepresented. |
| 4. Inference routing (which model your prompt hits) | Cursor, GitHub Copilot, Claude.ai. Each is one company's product. |
| 5. **Agent layer (what AI is allowed to do on your behalf)** | **Open today.** |

India is unlikely to compete on layers 1 and 2 in the next five years — those are infrastructure plays. Layer 5 is open right now, and a CLI is the cleanest expression of it. **Whoever builds a good agent layer gets to shape how a generation of developers experience AI for the next two decades.** If that layer is exclusively foreign products, the developer culture downstream gets shaped by their product decisions. If the layer is open-source and locally extensible, the culture is shaped by everyone using it.

That is the strategic argument. Not nationalism — substrate ownership.

---

## What `@dirgha/code` actually buys for a developer in Bharat today

A few specific scenarios.

### A student in a Tier-2 college

Has a laptop, no recurring tooling budget. Installs `dirgha` in 8 seconds. Sets `DIRGHA_PROVIDER=openrouter` and uses the free `:free` tier (Tencent HY3, Inclusion AI Ling, Google Gemma 4, NVIDIA Nemotron). Builds an entire portfolio of working software at zero cost. Learns by watching what the agent does to their codebase.

### A solo developer in Indore

Runs `dirgha` against Ollama on their own laptop. Spends ₹0/month. No internet required after model download. No prompt or file content leaves their machine. Ships paid client work to local businesses with full data sovereignty.

### A startup in Bengaluru

Prototypes on the free tier. Graduates to Anthropic's Claude Sonnet only on commits that go to production. The same `dirgha` binary handles both — switching is `dirgha keys add ANTHROPIC_API_KEY ...` plus a `/models` swap. Cost discipline is built into the tool.

### A research team at IIT

Uses `dirgha audit-codebase` to run a structured audit on a 500k-LOC codebase. Spawns a fleet of parallel agents in git worktrees, each with a different model. Compares outputs. Picks the one that flagged the most real issues. The whole orchestration is open-source, auditable, and reproducible.

### An OSS contributor in Kerala

Wants to add support for a new local Indic-tuned model. Forks the repo. Uses the built-in `add-provider` skill (the agent reads the skill and follows the 6-step recipe). Submits a PR. Their model is now routable from any Dirgha install on the planet.

---

## What `@dirgha/code` does NOT solve — to stay honest

- **It does not make models cheaper.** Frontier models from US labs cost what they cost regardless of which CLI calls them. Dirgha does cost arbitrage by routing intelligently to free or cheap providers, but the underlying tokens are not free magic.
- **It does not fix latency to frontier US-only models.** Calling Claude Opus from Bengaluru is still ~250 ms RTT. The local-first path (Ollama + smaller open models) is a real alternative for many tasks, but not all.
- **It does not replace the need for an Indic-tuned model.** Dirgha routes; it does not pretrain. A genuinely Bharat-aware coding agent eventually needs models that understand Indic scripts, English-Hindi code-mixing, and the cultural context of Indian software work. Those are upstream training problems.
- **It is English-first today.** The TUI, help text, and slash commands are all in English. Indic-language UI is a known gap.
- **It does not fix the broadband or device gap.** A 4 Mbps connection still struggles with frontier models. A laptop with 4 GB RAM cannot run Llama 70B locally. Hardware and connectivity remain real constraints.

These are honest limits. Naming them is the only way the case for the tool is taken seriously.

---

## The compounding argument

The most interesting argument for a sovereign coding CLI is not anything in the list above. It is **compounding**.

A CLI that 10,000 Indian developers use every day generates:

- **A growing skill library.** Today the built-in skill is `add-provider`. In a year there will be `deploy-to-render`, `scrape-mca-filing`, `translate-to-hindi-with-context`, `wrap-in-tally-erp`. None of these exist in foreign products. They will exist in Dirgha because the people writing them are the people using it.
- **A growing model catalogue tuned for Bharat workloads.** Real demand signal — which models work, which fail, which are over-priced — feeds back into the open-source repo and into provider negotiations.
- **A growing audit corpus.** With user consent (telemetry is opt-in and OFF by default), an honest dataset of what tools succeed, what stalls, what models hallucinate. Used to improve the tool. Not sold.
- **A growing pool of contributors** who learned the codebase by using it. The CLI is a teacher in a way a hosted web app rarely is. Every PR from a student in Coimbatore is one more developer who can shape it.

This compounding does not happen if the agent layer is owned by foreign products. It happens if the agent layer is open and the substrate is local.

---

## The long arc — from seed to operating system

`@dirgha/code` today (v1.12.2) is the kernel layer of a larger operating system being built at Dirgha:

| Layer | What it does | Repository |
|---|---|---|
| **Kernel** | Agent loop, tool dispatch, model routing, memory, skills | [`dirgha-code`](https://github.com/Dirgha-AI/dirgha-code) ← *you are here* |
| **Compute settlement** | Peer-to-peer GPU/CPU sharing, gossipsub mesh, value settlement | [`abundance-protocol`](https://github.com/Dirgha-AI/abundance-protocol) |
| **Security** | Red-teaming agent, supply-chain audit, jailbreak defence | [`arniko`](https://github.com/Dirgha-AI/arniko) |
| **Document studio** | AI-native long-form writing — books, papers, screenplays | [`writer-studio`](https://github.com/Dirgha-AI/writer-studio) |
| **Media studio** | AI-native creative production — audio, video, image | [`creator-studio`](https://github.com/Dirgha-AI/creator-studio) |
| **Hardware** | Sovereign assembled-in-India computer, refurbished AI laptops | [`Rama-I-Dirgha-AI-OS`](https://github.com/Dirgha-AI/Rama-I-Dirgha-AI-OS) |

Every studio above runs *on top of* the CLI's kernel primitives — agent loops, tool calls, provider routing, memory, skills. When Writer Studio composes a chapter, it is calling into the same agent loop that powers `dirgha ask`. When Creator Studio renders a video, it is dispatching tools the CLI exposes. When Arniko audits a codebase, it is using the CLI's audit subcommand.

This is not modularity for its own sake. It is the deliberate design of an operating system where one well-formed kernel makes every higher layer cheaper to build, easier to audit, and impossible to lock in.

> The CLI is the seed. The OS is what grows.

It does not ask the user to trust a brand on day one. It does not ask for a subscription. It does not ask anyone to commit to a vision of the world before they have used it. It just makes the next thing a developer builds a little easier — and over time, the substrate it runs on belongs to them.

That is what a Bharati operating system looks like. Not a flag. A 543 KB tarball that meets developers where they actually are, and a kernel small enough to read in a weekend, hack in a week, and shape over a decade.

---

## Get involved

- **Try it:** `npm install -g @dirgha/code`
- **Source:** [github.com/Dirgha-AI/dirgha-code](https://github.com/Dirgha-AI/dirgha-code)
- **Contribute:** [CONTRIBUTING.md](https://github.com/Dirgha-AI/dirgha-code/blob/main/CONTRIBUTING.md) — beginner's guide, supported providers, glossary
- **Discuss:** [github.com/Dirgha-AI/dirgha-code/issues](https://github.com/Dirgha-AI/dirgha-code/issues)
- **Reach out:** team@dirgha.ai

The CLI is one of the most accessible places to make a contribution to the agentic OS. Pick a typo, add a theme, integrate a new provider, or write a skill. The barrier to a first PR is intentionally low.
