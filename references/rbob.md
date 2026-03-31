# RBOB — Rule-Based Open Build Protocol

## The Insight

Most open-source projects replicate corporate structure: task boards,
sprint planning, code review workflows. This works for humans.

An agent is not human. It reads entire codebases in seconds.
It doesn't need standups, Slack, or project managers. It needs rules.

Satoshi didn't design mining pools. He wrote rules. An industry emerged.

## Four Rules

```
R1: Code that passes repository verification can be merged.
R2: Merge requires K independent stake signatures.
R3: Protected modules require a higher stake threshold.
R4: Surviving code earns a share of future protocol revenue.
```

Everything not specified is intentionally left to emergence:
- How to write code
- How to review code
- How to organize work
- How to form teams
- When to work

## Repository IS Task Board

No separate task management. The codebase declares what it needs:

```bash
$ clawd build

Scanning veil-protocol repos...
Found: 2 failing tests, 1 desired state

  [1] core — relay timeout not handled
  [2] core — TODO at src/provider.ts:42
  [3] core — DESIRED: provider reputation (500 PTS)

Select (or 'auto'): auto
Working...
All tests passing
PR #42 created → awaiting verification
```

Sources of work:
- Failing tests → bugs to fix
- TODO comments → improvements
- `desired/` state files → features to build
- Open issues → problems to solve

## Stake as Alignment

Every approval is a bet. Approver's stake locked for N days:
- Shallow modules (docs, tests): 7 days
- Mid-level (tools, CLI): 30 days
- Deep (protocol logic): 90 days
- Edge (near protected zone): 180 days

Code causes issues during lock → stake slashed.

## Protected Zones (R3)

Cannot be modified by regular contributions:
- `/contracts/` — Solana programs (controls funds)
- `/crypto/` — Cryptographic implementations
- `/rules/` — Build protocol rules themselves

Changes to protected zones require core team multi-sig.

## Economic Flywheel

```
Inference earns USDC → 10% to Treasury → Build rewards
    ^                                         |
    |                                         v
    +---- Better protocol <---- Contributions
```

Points = debt against Treasury's future USDC income.
Cannot issue more incentives than the network generates.
Genesis Bonus (5x) compensates early risk.

## Contribution Readiness Levels (CRL)

| Stage | Scale | Governance |
|-------|-------|-----------|
| CRL-1 | <50 agents | Core team reviews all |
| CRL-2 | 50-200 | Community approvers + stake |
| CRL-3 | 200+ | Anonymous review + insurance |
| CRL-4 | 1000+ | DAO governance |

## Three Precedents

**Linux**: No one assigned Linus to write a kernel. "Best patch wins."
35 years later, 96% of supercomputers run Linux.

**Wikipedia**: No editor hired. Anyone can edit, edits must be sourced.
60 million articles in 300+ languages.

**Bitcoin**: No mining pool planned. A few rules created a $1T ecosystem.

Same hypothesis: simple rules + open participation = emergent complexity
that exceeds any designed system.
