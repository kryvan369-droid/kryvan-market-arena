# KRYVAN

**Competitive experiences. One connected economy. Built on Solana.**

KRYVAN is a competitive ecosystem bringing games, markets and live participation together through a shared economic layer.

Instead of launching a token first and searching for utility afterwards, KRYVAN is being built product-first: create experiences people want to use, then connect those experiences through KRVN.

🌐 KRYVAN: https://kryvan.xyz  
♟️ Play Arena: https://kryvan.xyz/play  
📈 Market Arena: https://kryvan.xyz/market-arena  
🎥 Live Arena: https://kryvan.xyz/live  

---

## The Idea

Crypto has already shown that people will trade, play, compete and participate in markets onchain.

KRYVAN asks a different question:

**What if different forms of competition could exist inside one ecosystem and share one underlying economy?**

We are starting with competitive gaming, market-based competition and live spectator experiences.

---

## ♟️ Play Arena

Play Arena is KRYVAN's competitive gaming layer.

Players can create or join Arenas, connect through their Solana wallets and compete directly against another player.

Chess is the first game because its deterministic rules and results give us a strong environment for building and testing the underlying competition, custody and settlement architecture.

Current functionality includes:

- Arena creation and joining
- Solana wallet-connected identities
- Competitive chess
- Player stake flows using TEST KRVN
- Spectator participation
- Chess move and rule validation
- Game result handling
- Settlement and refund architecture

The wider architecture is designed so additional competitive games can eventually use the same KRYVAN ecosystem.

---

## 📈 Market Arena

Market Arena turns market movement into a competitive experience.

Participants take opposing positions such as **ABOVE** or **BELOW** for a defined market window and compete against participants on the other side.

The idea is participant-versus-participant competition rather than simply playing against a traditional house.

Market Arena is already part of the KRYVAN product experience.

Its dedicated on-chain custody, oracle and settlement architecture will follow the Play Arena Solana implementation.

---

## 🎥 Live Arena

Live Arena is KRYVAN's spectator layer.

It allows people to follow competitive Arenas and creates the foundation for spectators to participate in the wider ecosystem rather than every experience being limited to the two competitors.

---

## KRVN

**KRVN** is designed as the economic layer connecting KRYVAN experiences.

Intended total supply:

**1,000,000,000 KRVN**

During development, KRYVAN uses **TEST KRVN** so gameplay and economic infrastructure can be tested without representing test assets as production tokens.

Our approach is:

**Build the experiences → create genuine usage → connect them through one economy.**

Future tokenomics and economic mechanisms remain under development and should not be considered implemented unless explicitly stated.

---

## Why Solana?

KRYVAN experiences can involve frequent, relatively small economic interactions.

That makes transaction speed, low costs and wallet-native participation important.

Solana gives us the infrastructure to bring custody and settlement onchain without making blockchain complexity the centre of the user experience.

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

## Play Arena — Onchain Architecture

For stake-based Play Arenas, the economic result should not depend solely on the website or frontend.

At a high level:

**Player Wallet → Arena → Match Custody → Game Result → Settlement / Refund**

The Solana architecture is designed around:

- wallet-authorised participation
- SPL TEST KRVN
- match-specific PDA custody
- exact player stakes
- both-player confirmation before matching
- authoritative game results
- deterministic settlement
- draw refunds
- unmatched-player refunds
- duplicate-settlement protection
- recovery from interrupted transaction attempts

The application manages the game experience while Solana provides the custody and settlement layer.

---

## Development Progress

KRYVAN is a working product under active development, not simply a concept or landing page.

### Localnet

The latest Play Arena Solana implementation completed its full Localnet acceptance gate:

**42 / 42 live acceptance cases passed**  
**0 failures**

Testing covered:

- deposits
- match-specific custody
- settlement
- draw refunds
- unmatched-player refunds
- simultaneous settlement attempts
- duplicate terminal protection
- failed-response reconciliation
- expired-attempt recovery
- backend record recovery
- token balance verification
- protection against reopening completed matches

The goal was to test failure and recovery paths as well as the successful flow.

### Public Devnet

The next stage is public Solana Devnet validation using real Phantom wallets and TEST KRVN.

**This milestone is currently in progress.**

We do not describe Devnet or Mainnet functionality as complete until the corresponding validation has actually passed.

---

## Market Arena — Next Onchain Stage

Market competition introduces a different set of problems from deterministic games such as chess.

Its Solana architecture will therefore address:

- round-specific custody
- entry cutoffs
- authoritative market prices
- oracle integrity
- start and end prices
- stale price handling
- oracle outages
- cancelled rounds
- settlement
- refunds and recovery

This work follows the Play Arena onchain implementation rather than treating both systems as identical.

---

## Architecture

At a high level:

**User**

↓

**KRYVAN Web Application**

↓

**Phantom / Solana Wallet**

↓

**Play / Market / Live Experience**

↓

**KRYVAN Backend + Cloudflare D1**

↓

**Solana Programs + SPL Token**

↓

**Custody + Settlement**

Not every interaction needs to happen onchain.

KRYVAN uses Solana where it provides meaningful value, particularly for user-authorised economic actions, custody and settlement, while keeping normal product interactions responsive.

---

## Roadmap

**Working KRYVAN Arenas**

↓

**Play Arena Solana validation**

↓

**Public Devnet**

↓

**Market Arena onchain architecture**

↓

**Public beta**

↓

**Production / Mainnet readiness**

The longer-term goal is to add more competitive experiences around the same connected ecosystem.

---

## Colosseum

KRYVAN is being developed as a product and startup rather than solely as a hackathon prototype.

The current development phase has focused heavily on moving the competitive economy deeper into Solana infrastructure, particularly player custody, settlement, refunds, transaction recovery and public Devnet readiness.

Our thesis is simple:

**Build experiences people actually want to use first. If those experiences create real activity, the connected onchain economy has a reason to exist.**

---

## Security

No private keys, seed phrases, private RPC credentials, treasury keypairs, oracle secrets or production credentials belong in this public repository.

TEST KRVN and development assets have no monetary value.

---

## Links

🌐 **Website:** https://kryvan.xyz  
♟️ **Play Arena:** https://kryvan.xyz/play  
📈 **Market Arena:** https://kryvan.xyz/market-arena  
🎥 **Live Arena:** https://kryvan.xyz/live  
𝕏 **Founder:** https://x.com/shams_eth

---

## Status

KRYVAN is under active development.

Some functionality described here is experimental, test-only or under development. TEST KRVN has no monetary value, and future economic designs should not be interpreted as guarantees of production functionality or financial returns.
