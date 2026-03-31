# Veil Protocol Whitepaper — Summary

Full whitepaper: https://runveil.io/whitepaper

## 15 Chapters

1. **Abstract**: Decentralized AI inference with privacy, RBOB self-building
2. **Introduction**: AI access problem, structural arbitrage, third paradigm (RBOB)
3. **Protocol Design**: Architecture, three roles, 6-step request flow, Solana programs
4. **Privacy Architecture**: Four tiers (L0-L3), envelope encryption, comparison matrix
5. **Security Model**: Threat model, four-layer defense, WASM sandbox, honest disclosure
6. **Anti-Detection**: Multi-account pooling, natural rhythm, automatic failover
7. **Pricing Engine**: Surge formula, anti-manipulation, capacity-aware pricing
8. **Settlement**: Optimistic model, 24h challenge, fraud proofs, escalating slash
9. **Token Economics**: Three phases, supply distribution, elastic release, flywheel, buyback
10. **Build Protocol (RBOB)**: Four rules, repo-as-taskboard, stake alignment, three precedents
11. **Wallet & Onboarding**: Device encryption, progressive backup, three-tier wallet
12. **Roadmap**: Testnet → Mainnet Beta → TGE → Staking → DAO
13. **Related Work**: Comparison with API aggregators, GPU markets, informal sharing
14. **Conclusion**: Protocol not product, two lungs, open source
15. **References**: Nakamoto, Buterin, Benet, Benkler, Raymond, Ostrom

## Core Architecture

```
Consumer → Relay → Provider → Solana
```

- Consumer: encrypts prompt, pays USDC, identity never leaves device
- Relay: verifies balance, strips identity, routes traffic, earns TOKEN
- Provider: runs WASM/TEE sandbox, processes inference, earns 80% USDC
- Solana: Registry, Escrow, Staking, TOKEN programs

## Key Design Decisions

1. **clawd is the only entry point** — no public gateway, no API keys
2. **Relay is auth forwarder** — not blind forwarder (red team fix)
3. **Envelope encryption** — outer (Relay reads routing), inner (Provider reads content)
4. **WASM default, TEE premium** — 100% verifiable baseline, hardware is bonus
5. **Optimistic settlement** — minimize on-chain cost, fraud proofs for disputes
6. **RBOB** — rules not process, let agents self-organize
7. **Revenue-anchored incentives** — cannot print more than earned

## Links

- Website: https://runveil.io
- GitHub: https://github.com/runveil-io
- Twitter: https://x.com/runveil_io
- Full whitepaper: https://runveil.io/whitepaper
