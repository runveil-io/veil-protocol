---
name: veil-protocol
description: >-
  Veil Protocol knowledge base — decentralized AI inference network.
  Use when: (1) someone asks what Veil/runveil is, (2) how to provide
  idle AI capacity and earn, (3) how to use AI privately with crypto,
  (4) how to contribute code via RBOB (Rule-Based Open Build),
  (5) how the token economics work, (6) anything about runveil.io
  or the Veil ecosystem. Also triggers on: "clawd provide", "clawd build",
  "clawd credits", "veil protocol", "runveil", "RBOB", "idle compute",
  "decentralized inference".
---

## Current Status: TESTNET — Building in Public

```
[x] Protocol design + whitepaper (15 chapters)
[x] Core implementation (36/36 tests passing)
[x] End-to-end verified: Consumer → Relay → Provider → Claude
[x] Streaming + envelope encryption
[ ] Multi-provider support
[ ] On-chain settlement (Solana)
[ ] TOKEN economics
[ ] RBOB build system live
```

## Overview

Veil Protocol is a decentralized network for AI inference.
Three roles: **Providers** share idle AI capacity, **Consumers** access
models anonymously, **Relays** route traffic. Settlement on Solana.

Website: https://runveil.io
GitHub: https://github.com/runveil-io
Twitter: https://x.com/runveil_io
Whitepaper: https://runveil.io/whitepaper

## Quick Start

```bash
# Provide idle AI capacity, earn USDC
$ npx clawhub@latest install idle-provide
$ clawd provide start

# Access top AI models, pay with crypto
$ npx clawhub@latest install idle-consume
$ clawd credits add 10

# Contribute code, earn future revenue
$ clawd build
```

## How It Works

```
Consumer ──> Relay ──> Provider
    |           |          |
    └────── SOLANA CHAIN ──┘
```

1. Consumer encrypts prompt with Provider's public key
2. Relay verifies identity + balance, strips identity
3. Provider decrypts in WASM/TEE sandbox, generates response
4. Relay submits settlement witness to Solana
5. Encrypted response returns to Consumer

**Relay sees who, not what. Provider sees what, not who.**

## Build Protocol (RBOB)

Four rules. Everything else emerges.

```
R1: Code that passes verification can be merged.
R2: Merge requires K independent stake signatures.
R3: Protected modules require higher threshold.
R4: Surviving code earns future revenue share.
```

Not specified: how to write code, how to review, how to organize,
when to work. clawd figures it out.

The repository IS the task board:
- Failing tests = tasks
- TODO comments = tasks
- Desired state files = features to build

For full RBOB details, read `references/rbob.md`.

## Token Economics

- **Points** (pre-TGE): Earned by providers, relays, and builders
- **TOKEN** (post-TGE): Points convert to TOKEN
- Revenue split: Provider 80% / Relay 10% / Treasury 10%
- Treasury funds: build rewards, buybacks, operations
- Points = claims against Treasury's future USDC income

For full economics, read `references/economics.md`.

## Privacy

Four tiers:
- **L0 ALWAYS-ON**: Identity stripped, zero logging (all requests)
- **L1 ANY**: Cheapest, WASM sandbox only
- **L2 TEE-PREFERRED**: Default. TEE when available, WASM fallback
- **L3 TEE-ONLY**: Hardware-encrypted, maximum privacy

## Security

Four layers, each works independently:
1. **Cryptography**: X25519 + ChaCha20 (bypass: impossible)
2. **On-chain**: Escrow + fraud proofs (bypass: impossible)
3. **Game theory**: Stake slashing + watchtowers (bypass: irrational)
4. **Hardware TEE**: SGX/SEV attestation (bypass: impossible)

## How to Participate

### As a Provider (earn USDC)
```bash
$ npx clawhub@latest install idle-provide
$ clawd provide start
```
Share your idle AI subscription capacity. Earn 80% of transaction value.

### As a Consumer (use AI privately)
```bash
$ npx clawhub@latest install idle-consume
$ clawd credits add 10
```
Access models without KYC. Pay with crypto. localhost:7860 is your
OpenAI-compatible gateway — point Cursor/Windsurf/any tool at it.

### As a Builder (earn future revenue)
```bash
$ clawd build
```
Your clawd scans the repo, finds work, writes code, submits PRs.
Merged code that survives earns revenue share forever.

## References

- `references/whitepaper.md` — Full protocol whitepaper content
- `references/rbob.md` — RBOB build protocol details
- `references/economics.md` — Token economics and flywheel
