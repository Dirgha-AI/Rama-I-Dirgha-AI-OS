# How Dirgha makes money

Short version: subscriptions on the hosted platform, usage-based
billing for high-volume users, bring-your-own-key for the rest.
Open source stays open; the hosted convenience has a price.

## Plans

Three tiers on [dirgha.ai](https://dirgha.ai). All include chat, IDE,
agents, writer, creator, and the vertical modules (manufacturing,
education, CRM, ATS) as they come online.

| Plan | Price | Monthly credits | Who it's for |
|---|---|---|---|
| Pro | $20/mo | 4,000 | Individuals, side projects |
| Build | $100/mo | 20,000 | Builders shipping in production |
| Scale | $200/mo | 40,000 | Teams running fleet agents + long horizons |

Credits are a neutral unit across models — the gateway normalises
prices so you don't have to think about "is this call running on
Opus or on Llama."

Annual plans and team seats come in a later release. Enterprise
contracts are available for regulated workloads — email
`enterprise@dirgha.ai`.

## BYOK (bring your own key)

Prefer to route through your own provider account? Set
`ANTHROPIC_API_KEY`, `OPENAI_API_KEY`, `OPENROUTER_API_KEY`,
`NVIDIA_API_KEY`, or any of the 16 supported providers.
You keep your provider's rate card; we stay out of the billing.

BYOK works on any tier — Pro, Build, or Scale — and on the free
local CLI (`npm install -g @dirgha/code`).

## Usage billing

High-volume users on Build and Scale tiers can enable metered
billing for traffic above their plan credits. Stripe (global) and
Razorpay (India) are wired in. Per-request metering flows through
the shared `@dirgha/pricing` rate card; a fixed platform markup
settles to Dirgha.

## What's not paid

- **The CLI and SDKs.** FSL-1.1-MIT. Install and run locally with
  your own keys — no Dirgha account needed.
- **Arniko, Writer Studio, Creator Studio, Abundance Protocol** code.
  Apache 2.0. Self-host if you want.
- **Documentation, tutorials, reference MCP servers, symbol-graph
  tooling.** All open.

## Entity

Commercial operations run through **Dirgha LLC (Wyoming, United States)**
— the entity that holds subscriptions, payments, and enterprise
contracts. Team presence is in India (New Delhi + Pune).

## Contribute

If you'd rather skip the subscription and just support the work,
[dirgha.ai/contribute](https://dirgha.ai/contribute) has four
donation rails: Stripe, Razorpay, Lightning, and on-chain Bitcoin.

## Questions

- Pricing: [dirgha.ai](https://dirgha.ai) or `hello@dirgha.ai`
- Enterprise: `enterprise@dirgha.ai`
- Security: `security@dirgha.ai`
