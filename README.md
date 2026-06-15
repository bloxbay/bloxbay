<div align="center">

<img src="https://github.com/bloxbay/bloxbay/blob/main/BLOXBAY-logo.png" alt="BLOXBAY" width="120" />

# 🌴 BLOXBAY

### The voxel beach club that never closes. The party is the product.

A multiplayer voxel beach club, live in any browser. One shared dancefloor, a live DJ taking requests, islands for sale. No wallet, no download, no signup. Walk in, request a song, dance with the holders, right now.

[![Chain](https://img.shields.io/badge/chain-Solana-14F195?logo=solana&logoColor=white)](https://solana.com)
[![Launch](https://img.shields.io/badge/launch-PumpFun%20Fair-FF6B35)](https://pump.fun)
[![Supply](https://img.shields.io/badge/supply-1B%20%24BLOXBAY-blue)](#token-at-a-glance)
[![Team](https://img.shields.io/badge/team%20alloc-0%25-success)](#token-at-a-glance)
[![Play](https://img.shields.io/badge/play-bloxbay.fun-14F195)](https://bloxbay.fun)

**[▶ Play the bay](https://bloxbay.fun)** · **[X / @bloxbay_sol](https://x.com/bloxbay_sol)** · **[Telegram](https://t.me/bloxbay)** · **[Medium](https://medium.com/@bloxbay)**

</div>

---

## What is BLOXBAY

BLOXBAY is a living voxel beach club rendered in any browser, multiplayer from the first second. Everyone hears the same DJ set. Everyone dances on the same floor. The product is the party, and the party is live at launch, not a roadmap promise. `$BLOXBAY` never gates the flagship island; it buys you the next one, so holders mint and own their own party islands on the Bay Map.

- **Live, not roadmap.** The flagship club is built and partying before any token sale.
- **Zero friction.** A URL, a name, five seconds to the dancefloor. No wallet for guests, ever.
- **Server-authoritative.** One DJ state, one truth, every client in sync on the same beat.
- **No copyright surface.** Every track is synthesized live in the browser. No files, no samples.
- **Ownership over access.** Spend `$BLOXBAY` to mint an island; 50% of every mint burns forever.

---

## Core Mechanics

| Mechanic | What it does |
|---|---|
| Shared DJ state | Every client follows one current track; the DJ flips the deck and every screen switches on the same beat |
| Request queue | Guests add tracks, the DJ accepts or dismisses; a toast announces each request to the whole room |
| Procedural music | A 16-step WebAudio sequencer synthesizes 5 original tracks; the beat drives speakers, floor, and lasers |
| Island ownership | Hold `$BLOXBAY`, mint an island on the Bay Map, run your own booth (Phase 2); 50% of spend burns |
| Day/night cycle | Sunset to night rave every ~2.5 minutes; lasers, torches, and string lights ignite at night |
| Free flagship | The town square of the bay stays free for everyone, forever |

---

## The Core Loop

```
   Open bloxbay.fun ──► enter a name ──► spawn on the beach (no wallet)
        │
        ▼
   Hear the live set instantly ──► walk to the club ──► dance (B) with real players
        │
        ▼
   Request the next track (🎵) ──► DJ flips the deck ──► every screen switches on the beat
        │
        ▼
   Night falls ──► lasers + torches ignite ──► the drop ──► screenshot ──► post on X
        │
        └──────────────► come back tomorrow: new crowd, new set, same bay
```

---

## Repository Layout

This workspace bundles four repositories plus the marketing collateral. Each sub-repo carries its own `README.md` and `tags.md`.

| Repository | Role | Contains |
|---|---|---|
| [bloxbay-engine](bloxbay-engine) | Core engine | Server-authoritative party relay (`server/relay.js`), procedural music core, tokenomics scripts, `SYSTEM_DESIGN.md` (C4), CI |
| [bloxbay-codex](bloxbay-codex) | Documentation | `MANIFESTO.md` (the full thesis) and `THREAT_MODEL.md` (STRIDE + Web3-game abuse patterns) |
| [bloxbay-gateway](bloxbay-gateway) | API & SDK | Bay REST reference (`ENDPOINTS.md`) and a TypeScript SDK (`clients/ts`) for islands, the Bay Map, and mint verification |
| [bloxbay-arena](bloxbay-arena) | Web client | The playable voxel club: Three.js renderer, WebAudio engine, relay sync (Vite + React) |

### Marketing Collateral

| Folder | Contains |
|---|---|
| [Article/](../Article) | Long-form articles for Medium and X Articles |
| [Caption/](../Caption) | Social captions for X / Telegram |

---

## Tech Stack

| Layer | Technology |
|---|---|
| Renderer | Three.js (voxel, ortho-iso + first-person) |
| Audio | WebAudio API (procedural synthesis, 5 tracks) |
| Client build | Vite + React + TypeScript |
| Transport | WebSocket (`ws`) over same-origin `/ws` |
| Relay | Node.js (in-memory party state) |
| Persistence (Phase 2) | Encrypted PostgreSQL |
| Chain (Phase 2) | Solana, SPL token, on-chain memo indexer |
| Launch | PumpFun fair launch (bonding curve → AMM) |

---

## Token at a Glance

| Field | Value |
|---|---|
| Ticker | `$BLOXBAY` |
| Chain | Solana |
| Total supply | 1,000,000,000 |
| Team allocation | 0 (team buys on the curve like everyone else) |
| Presale / private | None |
| Launch | PumpFun bonding curve → graduates (~85 SOL) → AMM listing |
| Primary sink | Island mints (50% burned, 50% treasury) |
| Burns | 50% per island mint · 25% per cosmetic · 20% of treasury inflows quarterly |

**Holder tiers (all additive, nothing gated):** GUEST (0) · LOCAL (0.05%) · ISLANDER (0.25%) · BAY LORD (1%).

---

## Roadmap

| Phase | Focus | State |
|---|---|---|
| **1 — Flagship Party** | Voxel island, club, multiplayer presence, shared DJ + queue, seats, football, first-person cam, fair launch + 24/7 livestream | ✅ shipped / 🔜 deploy |
| **2 — The Archipelago** | Island mint (spend + 50% burn), customization, owner DJ authority, Bay Map, cosmetics, wallet connect for owners only | Planned (month 1–3) |
| **3 — The Venue Layer** | Scheduled raves, B2B branded islands, market-reactive bay, request battles, spectator mode | Planned (month 3–6) |
| **4 — The Bay Economy** | Island marketplace, creator tools, community pattern packs, regional relay scaling | Planned (month 6–12) |

---

## Quick Start

```bash
# clone the workspace
git clone https://github.com/bloxbay/bloxbay.git
cd bloxbay

# run the party relay (core engine)
cd bloxbay-engine && npm install && ADMIN_PIN=set-a-pin npm run relay

# in another terminal, run the web client
cd ../bloxbay-arena && npm install
echo 'VITE_RELAY_URL=ws://localhost:8787/ws' > .env.local
npm run dev   # open http://localhost:5173 and ENTER THE BAY 🌴
```

---

## ⚠️ Scam Warning

`$BLOXBAY` launches **only** on PumpFun as a 100% fair launch. Protect yourself:

- **There is no presale and no private round.** Anyone offering "early access," an allocation, or a whitelist is scamming you.
- **The team never DMs first.** Anything sent to you by a stranger is a scam, every time.
- **Verify the contract address** only from the official channels below. Do not trust a CA from a reply, a DM, or a lookalike site.
- **Official channels are the only source of truth:** [bloxbay.fun](https://bloxbay.fun) · [@bloxbay_sol](https://x.com/bloxbay_sol) · [t.me/bloxbay](https://t.me/bloxbay). Beware lookalike domains and impersonator handles.
- **Guests never need a wallet** to play. If a "BLOXBAY" page asks you to connect a wallet just to walk in, it is fake.

---

## Reference Links

| Resource | Link |
|---|---|
| Play | https://bloxbay.fun |
| X / Twitter | https://x.com/bloxbay_sol |
| Telegram | https://t.me/bloxbay |
| Medium | https://medium.com/@bloxbay |
| Launch | PumpFun (fair launch) |

---

<div align="center">
<sub>

`$BLOXBAY` is a meme token with game utility. It is not an investment product, security, or financial instrument. Nothing here is financial advice. Buying memecoins is extremely high risk; assume any amount spent can go to zero. Island mints and cosmetics are entertainment purchases, and burns are a game mechanic, not a promise of price appreciation. Do your own research. Never spend more than you can afford to lose. Have fun at the party.

</sub>
</div>
