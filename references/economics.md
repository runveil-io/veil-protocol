# Veil Token Economics

## Three Phases

**Phase 0 (M0-M3)**: Points + USDC
- Providers earn USDC (80%) + Points
- No token yet
- Genesis Bonus: 5x for first 30 days

**Phase 1 (M4-M6)**: TGE
- Points convert to TOKEN
- Elastic release begins
- Revenue-proportional minting

**Phase 2 (M6+)**: Full tokenomics
- Staking, governance, burn active
- DAO treasury management

## Supply Distribution

```
Total Supply: 1,000,000,000 TOKEN (fixed)

Mining Pool:     35% (350M) - Provider/Relay rewards
Ecosystem Fund:  20% (200M) - Grants, integrations
Team:            15% (150M) - Core contributors
Community:       10% (100M) - Points conversion airdrop
Treasury:        10% (100M) - Market making, reserves
Initial LP:      10% (100M) - LBP liquidity
```

## Revenue Split

Every inference transaction:
- 80% → Provider (who processed the request)
- 10% → Relay (who routed the traffic)
- 10% → Treasury (protocol fund)

## Revenue Flywheel

```
Inference → USDC revenue → Treasury (10%)
    ^                          |
    |                          v
    +-- Better protocol <-- Build rewards
```

Points/TOKEN are claims against Treasury USDC.
The protocol cannot issue more incentives than it generates.
This prevents inflationary death spirals.

## Surge Pricing

Dynamic pricing based on supply/demand:
- Base: 50% of official API rate
- Floor: 30% (minimum)
- Ceiling: 80% (maximum)
- EMA smoothed (alpha=0.8) to prevent manipulation

## Settlement

Optimistic settlement with 24h challenge window:
1. Relay submits witness to Solana
2. 24h challenge period
3. If unchallenged: auto-release funds
4. If challenged: fraud proof arbitration

Escalating slash: 1st=30%, 2nd=50%, 3rd=100%+ban.
Reporter earns 30% of slashed amount.

## Buyback & Burn

Post-TGE Treasury conducts buybacks:
- Phase 1 (M6-M12): Manual
- Phase 2 (M12-M18): TWAP algorithmic
- Phase 3 (M18+): Automated on-chain

Budget: Treasury × 20% annually. All bought tokens burned.
