---
name: handoff
description: Compact the current conversation into a handoff document so another agent can continue the work without re-reading the entire session history.
---

# Handoff

## Purpose

When spawning sub-agents, the main session history is often bloated with tool calls, errors, and irrelevant context. A handoff document captures only what matters — current state, what's been done, what's pending, and key decisions — so the sub-agent starts cold but informed.

## When to Use

- **Before spawning a sub-agent** — compress context into a handoff
- **Switching projects mid-session** — save state for later
- **Long-running tasks** — checkpoint progress periodically

## Handoff Template

Keep it to one screen. Max 20 lines.

```
## Handoff: [Task Name]

### State
- [x] Done: [what was completed]
- [ ] Pending: [what's left]
- ⚠️ Blocked: [if anything is stuck]

### Key Context
- Project: [name + path]
- Files touched: [paths]
- Decision: [key choice made]
- Gotcha: [hard-learned lesson]

### Next Step
[The very next action someone should take]
```

## Usage

When spawning a sub-agent, include the handoff in the task description:

```
Task: "Continue implementing X. Here's the handoff:
[HANDOFF TEXT]
Write your output to: [path]"
```

## Example

```
## Handoff: CIRCLE Token Deposit Page

### State
- [x] Deposit page HTML built (bridgewell-site/deposit.html)
- [x] Presale V2 deployed ($10 min, 0xE301...9549EA)
- [-] Safe multisig setup: 1/2 signatures done, waiting for Badrun

### Key Context
- Project: bridgewell-site/ (Vercel)
- Token: 0x0136...9e41b (BSC, upgradeable)
- Presale: 0xE301...49EA, accepts USDC/USDT
- Website: bridgewell-site.vercel.app
- Deposit page accepts USDC/USDT (BEP-20), min $10
- After deposit: funds go to contract, user can claim CIRCLE after June 6

### Next Step
Deploy deposit.html to Vercel, test with $10 USDT deposit
```

## Cross-reference

- **shared-language** — include relevant domain terms in context
- **zoom-out** — handoff should capture enough context that zoom-out isn't needed
