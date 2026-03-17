# NORNR

**Spend governance for AI agents.**

When agents start initiating real economic actions - buying API calls, paying vendors, booking resources - it is not enough that money can move. You need to decide which agent can spend, how much, against whom, and have a defensible trail when someone asks why.

NORNR is the control layer between agent intent and real settlement.

---

![NORNR Control Room](https://raw.githubusercontent.com/NORNR/.github/main/profile/control-room.png)

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
- **Signed receipts** - every transaction gets a verifiable receipt
- **Audit export** - signed manifests, close bundles, and cost attribution ready for review
- **Budget tags** - attribute spend by team, project, customer, or cost center
- **Anomaly detection** - velocity patterns, split-purchase detection, and auto-pause

---

## Quickstart

**TypeScript**

```ts
import { Wallet } from "@nornr/sdk";

const wallet = await Wallet.create({
  owner: "my-agent",
  dailyLimit: 50,
  requireApprovalAbove: 20,
  baseUrl: "https://nornr.com",
});

const payment = await wallet.pay({
  amount: 12.5,
  to: "stripe-api",
  purpose: "process customer invoice",
});

if (payment.requiresApproval) {
  await wallet.approveIfNeeded(payment);
}
```

**Python**

```python
from agentpay import Wallet

wallet = Wallet.create(
    owner="my-agent",
    daily_limit=50,
    require_approval_above=20,
    base_url="https://nornr.com",
)

payment = wallet.pay(
    amount=12.50,
    to="stripe-api",
    purpose="process customer invoice",
)

if payment.get("requiresApproval"):
    wallet.approve_if_needed(payment)
```

---

## SDKs

- [sdk-ts](https://github.com/NORNR/sdk-ts) — `npm install @nornr/sdk`
- [sdk-py](https://github.com/NORNR/sdk-py) — `pip install agentpay`

---

## Works with your agent framework

NORNR is framework-agnostic:

- [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/)
- [LangChain / LangGraph](https://langchain.com)
- [CrewAI](https://crewai.com)
- [AutoGen](https://microsoft.github.io/autogen/)
- any HTTP client

---

## Why not X?

| | NORNR | AgentKit (Coinbase) | Stripe Treasury | Build it yourself |
|---|---|---|---|---|
| **Primary focus** | Spend governance + audit | Crypto wallet rails | Bank-grade money movement | Whatever you wire up |
| **Policy engine** | ✓ Built-in | ✗ | ✗ | You build it |
| **Approval queue** | ✓ Slack + API | ✗ | ✗ | You build it |
| **Anomaly detection** | ✓ | ✗ | ✗ | You build it |
| **Signed audit export** | ✓ | ✗ | ✗ | You build it |
| **Requires crypto** | ✗ Optional | ✓ Required | ✗ | — |
| **Works with any agent framework** | ✓ | Partial | ✗ | — |
| **Enterprise control plane** | ✓ | ✗ | Partial | You build it |

---

## Pricing

|  | Free | Builder | Growth | Enterprise |
|---|---|---|---|---|
| Governed spend | $500/mo | $10k/mo | $100k/mo | Custom |
| Agents | 3 | 25 | 100 | Unlimited |
| Settlement fee | 1.00% | 0.50% | 0.30% | Negotiated |
| Price | $0 | $79/mo | $299/mo | Contact us |

Free tier is free forever. No credit card required.

---

## Get started

[Create a free workspace ->](https://nornr.com)

---

## Philosophy

Autonomy without accountability is not freedom. It is unowned liability.

NORNR is built on the premise that the companies that will actually deploy autonomous agents at scale are the ones who can answer: what did my agents spend, why was it allowed, and who approved it?

---

## License

MIT - SDKs are open source. The hosted control plane is a commercial product.
