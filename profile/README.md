# NORNR

**Spend governance for AI agents.**

When agents start initiating real economic actions — buying API calls, paying vendors, booking resources — it is not enough that money can move. You need to decide which agent can spend, how much, against whom, and have a defensible trail when someone asks why.

NORNR is the control layer between agent intent and real settlement.

```
Agent wants to spend  →  Policy engine evaluates  →  Approved / Queued / Blocked
                                                             |
                                                             v
                                                   Ledger records it
                                                   Receipt is generated
                                                   Audit trail is signed
```

## What we build

- **Policy engine** — limits, approval thresholds, counterparty allowlists, anomaly triggers
- **Approval queue** — human-in-the-loop when it matters, automated when it does not
- **Signed receipts** — every transaction gets a verifiable receipt
- **Audit export** — signed manifests, close bundles, and cost attribution

## SDKs

- [sdk-ts](https://github.com/NORNR/sdk-ts) — TypeScript / JavaScript
- [sdk-py](https://github.com/NORNR/sdk-py) — Python

## Links

[nornr.com](https://nornr.com) · [Control room](https://nornr.com/app)
