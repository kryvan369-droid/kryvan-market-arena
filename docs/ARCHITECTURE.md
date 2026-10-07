# KRYVAN Architecture

KRYVAN is a competitive ecosystem built around games, markets and live participation connected through a shared economic layer.

The architecture follows a simple principle:

**Keep normal product interactions fast and familiar, while using Solana where on-chain custody, ownership and settlement provide meaningful value.**

---

## High-Level Architecture

User

↓

KRYVAN Web Application

↓

Phantom / Solana Wallet

↓

Play Arena / Market Arena / Live Arena

↓

KRYVAN Backend + Cloudflare D1

↓

Solana Programs + SPL Token

↓

Custody / Settlement / Refund

KRYVAN does not attempt to put every application interaction on-chain.

Gameplay, user experience and supporting application state can remain responsive off-chain, while economic actions that benefit from verifiable execution are progressively moved to Solana.

---

# Play Arena

Play Arena is KRYVAN's competitive gaming layer.

Chess is the first implementation because it provides deterministic rules and results while allowing the underlying competitive economic architecture to be developed and tested.

A typical Play Arena lifecycle is:

1. Player A creates an Arena.
2. Player A confirms the required TEST KRVN stake.
3. Player B joins the Arena.
4. Player B confirms the same stake.
5. Both confirmed stakes are placed into match-specific custody.
6. The Arena becomes matched.
7. Players compete.
8. The application determines the authoritative game result.
9. The corresponding settlement or refund path is executed.
10. The terminal economic state is recorded and cannot be executed twice.

Conceptually:

**Player A + Player B**

↓

**Wallet-authorised stakes**

↓

**Match-specific Solana custody**

↓

**Competitive game**

↓

**Authoritative result**

↓

**Settlement / Refund**

---

# Match-Specific Custody

Play Arena is designed around per-match Solana Program Derived Address (PDA) custody.

This prevents player stakes from simply being represented as entries inside one central application balance.

Each match has an economic lifecycle associated with that specific competition.

The architecture separates:

- game state
- stake state
- custody
- result evidence
- settlement state
- backend records

This separation is intended to make economic actions easier to verify and safer to recover when failures occur.

---

# Settlement

The settlement path depends on the authoritative result of the competition.

For the current test architecture:

### Decisive Result

When one player wins, the match can settle according to the configured economic policy.

During the current zero-fee TEST KRVN validation model, the combined player stakes are paid to the winner.

### Draw

A valid draw returns each player's confirmed stake.

### Unmatched Arena

If one player confirms a stake but the opposing player never completes the required participation, the confirmed player has a defined refund path.

### Unresolved / No-Show Scenario

The test architecture includes refund handling so assets do not need to remain permanently trapped when a competition cannot reach a valid result.

---

# Terminal-State Protection

A financial settlement system must protect against the same match being settled more than once.

The Play Arena architecture therefore includes terminal-state guards.

Once a match reaches a valid terminal economic state, competing settlement/refund attempts must not be able to create another payout.

This has been tested against race and duplicate-settlement scenarios during Localnet acceptance.

---

# Recovery

Blockchain transactions and web applications can fail at different points.

A transaction may succeed on Solana while the application fails to receive or record the response.

For this reason, KRYVAN does not treat a missing browser response as proof that an economic action failed.

The architecture includes reconciliation and recovery paths for scenarios such as:

- lost transaction responses
- expired attempts
- duplicate requests
- backend record inconsistencies
- transaction retry races

Solana transaction evidence and token balances can be used to reconcile application state.

---

# Backend and D1

Cloudflare Workers and D1 support the application and coordination layer.

D1 records supporting information such as:

- Arena state
- player participation
- economic intents
- transaction receipts
- results
- settlement attempts
- payout plans
- audit/recovery information

The backend does not replace Solana custody.

Its role is to coordinate the application experience and maintain the supporting records required to operate and reconcile the product.

---

# TEST KRVN

KRYVAN currently uses SPL **TEST KRVN** during development.

TEST KRVN allows the complete user and economic flow to be tested without representing development assets as production tokens.

TEST KRVN has no monetary value.

The intended production KRVN supply is:

**1,000,000,000 KRVN**

Production economic configuration and future tokenomics remain separate from the current testing architecture.

---

# Market Arena

Market Arena uses the same broader KRYVAN philosophy but presents a different technical problem from chess.

A chess result can be determined from deterministic game rules.

A market competition depends on external market data.

The future Market Arena Solana architecture therefore requires additional controls around:

- contest-specific custody
- entry deadlines
- authoritative price sources
- oracle integrity
- locked start prices
- locked end prices
- stale data
- oracle outages
- cancelled contests
- settlement
- refunds
- dispute and recovery scenarios

The existing Market Arena product is being preserved while this dedicated on-chain architecture is developed separately.

---

# Live Arena

Live Arena provides KRYVAN's spectator layer.

The purpose is to allow competitive experiences to extend beyond the players directly participating in a match.

Spectator functionality can therefore become another participant layer around Play Arena, Market Arena and future KRYVAN experiences.

---

# Solana Development

The current Play Arena architecture has completed its Localnet acceptance milestone.

**42 / 42 live acceptance cases passed**

**0 failures**

The acceptance matrix covered successful flows as well as custody, settlement, refunds, race conditions, interrupted responses, recovery and terminal-state protection.

The next stage is public Solana Devnet validation using real Phantom wallets and TEST KRVN.

Devnet validation is currently in progress and should not be interpreted as completed Mainnet functionality.

---

# Technology

KRYVAN currently uses or integrates:

- Solana
- Anchor
- SPL Token
- Phantom
- Helius
- Cloudflare Workers
- Cloudflare D1
- chess.js
- JavaScript / TypeScript

---

# Security Boundary

Private infrastructure and credentials are intentionally excluded from this public repository.

The repository must never contain:

- private keys
- seed phrases
- treasury keypairs
- oracle private keys
- private RPC URLs
- API keys
- environment secrets
- production credentials

Public architecture documentation describes how KRYVAN works without exposing the credentials controlling development infrastructure.

---

# Direction

The current architecture path is:

**Play Arena product**

↓

**Solana custody + settlement**

↓

**Localnet acceptance**

↓

**Public Devnet validation**

↓

**Market Arena on-chain architecture**

↓

**Public beta**

↓

**Production / Mainnet readiness**

The objective is not to move everything on-chain.

The objective is to use Solana where it can make competitive economic interactions more transparent, verifiable and resilient while keeping KRYVAN usable as a consumer product.
