# NORNR

**Mandates, approvals and evidence for autonomous agents.**

Give your agent a budget, approval rules, and an audit trail.

When agents start initiating real economic actions - buying API calls, paying vendors, booking resources - it is not enough that money can move. You need to decide which agent can spend, how much, against whom, and have a defensible trail when someone asks why.

NORNR is the control layer between agent intent and real settlement. Today the primary commercial model is subscription software. Optional settlement fees only apply when NORNR itself executes the settlement rail.

## Start here

- [Try the 5-minute quickstart](https://nornr.com/quickstart)
- [Open the control room](https://nornr.com/app)
- [Apply as a design partner](https://nornr.com/#design-partner)
- [TypeScript SDK](https://github.com/NORNR/sdk-ts)
- [Python SDK](https://github.com/NORNR/sdk-py)

Free tier is free forever. No credit card required.

---

![NORNR Control Room](https://raw.githubusercontent.com/NORNR/.github/main/profile/control-room.png)

## What to expect in 5 minutes

1. Create one governed wallet for an agent.
2. Submit one spend intent against the hosted control plane.
3. See whether policy returns `approved`, `queued`, or `rejected`.
4. Open the control room to inspect approvals and evidence.

## What NORNR does

```text
Agent wants to spend  ->  Policy engine evaluates  ->  Approved / Queued / Blocked
                                                             |
                                                             v
                                                   Ledger records it
                                                   Receipt is generated
                                                   Audit trail is signed
```

- **Policy engine** - set limits, approval thresholds, counterparty allowlists, and anomaly triggers
- **Approval queue** - human-in-the-loop when it matters, automated when it does not
- **Signed receipts** - every governed action gets a verifiable receipt
- **Audit export** - signed manifests, close bundles, and cost attribution ready for review
- **Budget tags** - attribute spend by team, project, customer, or cost center
- **Anomaly detection** - velocity patterns, split-purchase detection, and auto-pause

---

## Quickstart

**TypeScript**

```ts
import { Wallet } from "@nornr/sdk";

const wallet = await Wallet.create({
  owner: "research-agent",
  dailyLimit: 100,
  requireApprovalAbove: 25,
  baseUrl: "https://nornr.com",
});

const decision = await wallet.pay({
  amount: 12.5,
  to: "openai",
  purpose: "model inference",
});

if (decision.requiresApproval) {
  await wallet.approveIfNeeded(decision);
}
```

**Python**

```python
from agentpay import Wallet

wallet = Wallet.create(
    owner="research-agent",
    daily_limit=100,
    require_approval_above=25,
    base_url="https://nornr.com",
)

decision = wallet.pay(
    amount=12.50,
    to="openai",
    purpose="model inference",
)

if decision.get("requiresApproval"):
    wallet.approve_if_needed(decision)
```

Need the shortest path instead?

- [Hosted quickstart](https://nornr.com/quickstart)

---

## SDKs

- [sdk-ts](https://github.com/NORNR/sdk-ts) - `npm install @nornr/sdk`
- [sdk-py](https://github.com/NORNR/sdk-py) - `pip install agentpay`

---

## Works with your agent framework

NORNR is framework-agnostic:

- [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/)
- [LangChain / LangGraph](https://langchain.com)
- [CrewAI](https://crewai.com)
- [AutoGen](https://microsoft.github.io/autogen/)
- any HTTP client

---

## Why NORNR

| | NORNR | AgentKit (Coinbase) | Stripe Treasury | Build it yourself |
|---|---|---|---|---|
| **Primary focus** | Spend governance + audit | Crypto wallet rails | Bank-grade money movement | Whatever you wire up |
| **Policy engine** | ✓ Built-in | ✗ | ✗ | You build it |
| **Approval queue** | ✓ Slack + API | ✗ | ✗ | You build it |
| **Anomaly detection** | ✓ | ✗ | ✗ | You build it |
| **Signed audit export** | ✓ | ✗ | ✗ | You build it |
| **Requires crypto** | Optional | Required | No | — |
| **Works with any agent framework** | ✓ | Partial | ✗ | — |
| **Enterprise control plane** | ✓ | ✗ | Partial | You build it |

---

## Pricing

Subscriptions carry the product today. Governed spend is mainly the upgrade trigger; optional settlement fees only apply when NORNR itself executes a configured rail adapter.

|  | Free | Builder | Growth | Enterprise |
|---|---|---|---|---|
| Governed spend | $500/mo | $10k/mo | $100k/mo | Custom |
| Agents | 3 | 25 | 100 | Unlimited |
| Price | $0 | $79/mo | $299/mo | Contact us |

Free tier is free forever. No credit card required.

---

## Get started

[Create a free workspace ->](https://nornr.com)

Need help or want to tell us where the quickstart broke?

- Support: [support@nornr.com](mailto:support@nornr.com)

---

## License

MIT - SDKs are open source. The hosted control plane is a commercial product.
