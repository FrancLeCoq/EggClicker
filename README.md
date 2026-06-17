# 🥚 Egg Clicker — Francis the Rooster Farm

A single-file incremental/idle clicker game built in vanilla HTML, CSS and JavaScript. No build step, no dependencies — open `game.html` and play.

---

## Table of Contents

1. [Overview](#overview)
2. [File Structure](#file-structure)
3. [How to Play](#how-to-play)
4. [Farm — Producers](#farm--producers)
5. [Upgrades](#upgrades)
6. [Trophies](#trophies)
7. [Prestige System](#prestige-system)
8. [Events — Fox Attack](#events--fox-attack)
9. [Day / Night & Weather](#day--night--weather)
10. [Saving (Local Only)](#saving-local-only)
11. [Trial vs Holder Mode](#trial-vs-holder-mode)
12. [Configuration](#configuration)
13. [Assets](#assets)
14. [Technical Notes](#technical-notes)

---

## Overview

Egg Clicker is a French-rooster-themed idle clicker where you tap Francis Le Coq to collect eggs, reinvest into a growing farm empire, unlock upgrades, earn trophies, and prestige to climb further. The game evolves through 9 named stages, a living day/night sky, weather events, and blockchain-flavored end-game content.

---

## File Structure

```
game.html          ← entire game (HTML + CSS + JS, ~1 700 lines)
assets/
  chick.png        ← Curious Chick sprite
  hen.png          ← Laying Hen sprite
  coop.png         ← Chicken Coop sprite
  farm.png         ← Farm Cooperative sprite
  auto.png         ← Automated Farm sprite
  factory.png      ← Egg Factory sprite
  lab.png          ← Genetic Lab sprite
  station.png      ← Orbital Station sprite
  franc.png        ← $FRANC Dimension sprite
  paradox.png      ← Rooster Paradox sprite
  coq.png          ← Main rooster click target
  besace.png       ← Storage Satchel icon
  gants_caoutchouc.png
  botte_caoutchouc.png
  gants_or.png
  botte_or.png
  soleil.png       ← Sun (celestial)
  lune.png         ← Moon (celestial)
  nuage1.png       ← Cloud variant 1
  nuage2.png       ← Cloud variant 2
  chasseur.png     ← Hunter (fox event)
  ferme.mp3        ← Default background music
  ferme apaisante.mp3 ← Soothing Music upgrade track
  rain.mp3         ← Rain ambiance loop
```

---

## How to Play

The game opens on a **start screen** with:

- **Resume game** — loads your local save and credits offline production
- **New game** — wipes the save and starts fresh (asks for confirmation)
- **Connect wallet** — opens the wallet-connect page; the icon shows a **closed padlock 🔒** when no wallet is linked and an **open padlock 🔓** when connected (Holder mode)
- **Language flags** 🇫🇷 / 🇬🇧 — choose French or English; the choice is remembered

Once in game:

1. **Click Francis** (the rooster) to collect eggs manually.
2. **Buy Farm items** in the Farm tab to produce eggs automatically every second.
3. **Buy Upgrades** when they become available (green egg 🥚 icon = affordable) to multiply production.
4. **Earn Trophies** by hitting milestones — each one gives +1% global production bonus.
5. **Prestige** once you reach 1 B eggs lifetime — trade your run for Golden Feathers that give +2% permanent bonus per feather.

**Tabs:**

| Tab | Content |
|---|---|
| Farm | All 10 producers — grayed if unaffordable |
| Upgrades | All 17 upgrades — grayed if locked or unaffordable |
| Trophies | 15 achievements + bonus tracker |
| Stats | Full session statistics |

---

## Farm — Producers

All 10 producers are visible from the start. A green egg icon appears next to the price when you can afford one.

| # | Name | Base cost | Eggs/sec |
|---|---|---|---|
| 1 | Curious Chick | 15 | 0.1 |
| 2 | Laying Hen | 100 | 1 |
| 3 | Chicken Coop | 1 000 | 5 |
| 4 | Farm Cooperative | 10 000 | 25 |
| 5 | Automated Farm | 100 000 | 100 |
| 6 | Egg Factory | 1 000 000 | 500 |
| 7 | Genetic Lab | 10 000 000 | 1 000 |
| 8 | Orbital Station | 100 000 000 | 10 000 |
| 9 | $FRANC Dimension | 1 000 000 000 | 100 000 |
| 10 | Rooster Paradox | 100 000 000 000 | 1 000 000 |

Each subsequent purchase of the same producer increases its cost by ×1.15.

---

## Upgrades

Upgrades are hidden until their requirement is met, then appear in the list grayed until affordable, then highlighted in green when ready to buy. A floating upgrade icon also appears in the center of the playfield.

### Click multipliers

| Name | Cost | Effect | Requirement |
|---|---|---|---|
| Storage Satchel | 10 | Unlocks upgrade system | — |
| Farmer Gloves | 100 | Click ×2 | 10 clicks |
| Rubber Boots | 1 000 | Click ×2 | 5 Laying Hens |
| Golden Gloves | 50 000 | Click ×3 | 10 Chicken Coops |
| Golden Boots | 5 000 000 | Click ×4 | 25 Farm Cooperatives |
| Rooster Meditation | 500 000 000 | Click ×5 | 25 Egg Factories |

### Producer multipliers

| Name | Cost | Effect | Requirement |
|---|---|---|---|
| Premium Organic Grain | 500 | Curious Chick ×2 | 10 Curious Chicks |
| Soothing Music | 5 000 | Laying Hen ×2 | 10 Laying Hens |
| Comfortable Nests | 25 000 | Chicken Coop ×2 | 10 Chicken Coops |
| Cooperative Charter | 250 000 | Farm Cooperative ×2 | 10 Farm Cooperatives |
| Laying AI | 3 000 000 | Automated Farm ×2 | 10 Automated Farms |
| Ultra-Conductor Belt | 30 000 000 | Egg Factory ×2 | 10 Egg Factories |
| CRISPR-CockaDoodle | 400 000 000 | Genetic Lab ×2 | 10 Genetic Labs |
| Orbital Thrusters | 6 000 000 000 | Orbital Station ×2 | 10 Orbital Stations |
| Golden Smart Contracts 💎 | 100 000 000 000 | $FRANC Dimension ×2 | 10 $FRANC Dimensions |

### Global multipliers

| Name | Cost | Effect | Requirement |
|---|---|---|---|
| Celestial Layers ☀️🌙 | 10 000 000 000 | Global ×1.75 | 25 Chicken Coops |
| Golden Rooster Trophy 🏆 | 20 000 000 000 | Global ×2 | 50 Automated Farms |

**Purchase animations** — key upgrades trigger a full-screen splash animation (grain swirl, chain shake, diamond rain for Golden Smart Contracts, etc.).

---

## Trophies

15 achievements — each unlocked trophy grants **+1% global production**. Unlocking a trophy triggers a large pulsing emoji display for 5 seconds.

| Icon | Name | Condition |
|---|---|---|
| 🥚 | First Egg | 1 click |
| ✋ | Hundred Cock-a-doodles | 100 clicks |
| 💪 | Iron Finger | 1 000 clicks |
| 🌾 | First Farm Purchase | 1 farm item |
| 🏡 | Small Hamlet | 10 farm items |
| 💰 | Farm Tycoon | 100 farm items |
| 🏰 | Farm Empire | 1 000 farm items |
| 🥬 | A Thousand Eggs | 1 000 eggs lifetime |
| 🌽 | Million Eggs | 1 000 000 eggs lifetime |
| 🌟 | Billion Eggs | 1 000 000 000 eggs lifetime |
| 🧺 | Farm Collector | 1 of every farm item |
| 🛒 | Upgrader | 5 upgrades purchased |
| ✨ | All Upgrades | All upgrades purchased |
| 🪶 | First Prestige | 1 prestige |
| 👑 | The Legendary Rooster | 10 prestiges |

---

## Prestige System

Once you have accumulated **1 billion eggs lifetime**, the Prestige button activates.

- Converts your run into **Golden Feathers** (formula: `floor(√(lifetime_eggs / 1B))`)
- Resets: eggs, buildings, upgrades, clicks — everything except feathers and trophies
- Each feather gives a **permanent +2% global multiplier**
- Feathers stack across all prestiges

The prestige card in the Upgrades tab shows current feathers, current bonus, projected bonus after next prestige, and the egg threshold for the next feather.

---

## Events — Fox Attack

On session close, there is a **1-in-3 chance** of flagging a fox attack for the next session.

If you return after **8+ hours offline** and the flag is set:

- **If you have ≥ 10 000 eggs** — you can pay the hunter to save your farm. Production resumes normally.
- **If you have < 10 000 eggs** — you lose 50% of your egg stash automatically.

The fox attack modal blocks all input until resolved.

---

## Day / Night & Weather

Time flows from the game clock (real wall-clock seconds, accumulated in `ST.gameClock`). One full game day = **24 real minutes**.

### Celestial cycle

| Time | Sky |
|---|---|
| 06:00 – 20:00 | Daytime — sun visible, blue sky |
| 20:00 – 06:00 | Night — moon visible, dark sky |

### Weather events

| Event | Game time | Effect |
|---|---|---|
| 🌧️ Rain | 15:00–16:00 and 03:00–04:00 | Rain layer fades in fast, stays dense, fades out slowly. Screen darkens. |
| 🌫️ Fog | 08:00–09:00 and 20:00–21:00 | Gray veil covers the full screen (playfield + UI). |

Rain intensity follows a custom curve: **15% ramp-up → 65% sustained peak → 20% slow fadeout**.

**Rain sound** (`rain.mp3`) fades in and out with the rain intensity — volume tracks the visual layer smoothly.

### Music

The default background track is `ferme.mp3`. When the player purchases the **Soothing Music** upgrade, it swaps to `ferme apaisante.mp3` seamlessly.

### Cloud behavior

- **Normal weather**: 3 cloud slots, slow drift (40–65s per pass)
- **Rain / Fog**: 12 cloud slots, mass deployment at weather start, auto-relaunch on exit, slow dark clouds (35–60s per pass), continuous — no gap

---

## Saving (Local Only)

The game uses **local save only** — there is no cloud sync and no Supabase communication for game data.

| Trigger | Local save |
|---|---|
| Auto (timer) | Every **15 seconds** (only once a game has started) |
| Purchase / prestige | Immediate |
| Tab hidden / app backgrounded | Immediate |
| Page unload | Immediate |

**Local save** uses `localStorage` (key: `francCoq`). Language preference is stored separately (`francCoqLang`), and the fox-attack flag in its own key.

On **Resume**, offline production is credited at **50% efficiency** for the time away (capped at 8h). A **New game** wipes all local save data and starts fresh.

> **Note:** Cloud save/load (previously two Supabase Edge Function calls, `game-save` and `game-load`) has been fully removed. The only external dependency that remains is the wallet-connect page and $FRANC holder detection.

---

## Trial vs Holder Mode

| Mode | Session limit | How to activate |
|---|---|---|
| Trial | 10 minutes | Default |
| Holder 🪙 | Unlimited | URL param `?mode=unlimited` or connected wallet |

When the trial ends, a modal prompts wallet connection. Progress is preserved in localStorage regardless.

---

## Configuration

All runtime constants live in the `CFG` object at the top of the `<script>`:

```js
const CFG = {
  wallet: 'https://franclecoq.github.io/Wallet/connect-wallet.html', // wallet connect URL
  home:   './index.html',          // back-to-home URL
  trial:  600,                     // trial duration in seconds (10 min)
  ap:     'assets/'                // assets folder path
};
```

---

## Assets

All assets are loaded with graceful fallback — if a PNG is missing, the game substitutes a CSS-drawn shape or emoji. No asset is strictly required for the game to run.

---

## Languages (FR / EN)

The game is fully bilingual. All text — producers, upgrades, trophies, stages, UI labels, modals, toasts, and fox events — is stored in an `I18N` dictionary with `en` and `fr` entries. A `t(key)` helper plus `pName/pDesc/uName/aName/aDesc/stageName/prodReqName` helpers pull the right language at render time.

- Switching language re-renders everything instantly, no reload needed.
- The choice persists in `localStorage` (`francCoqLang`).
- To add a new language, add a third key to `I18N` with the same structure.

---

## Technical Notes

- **Single file** — no bundler, no framework, no external CDN
- **Egg production** uses `Date.now()` delta (`dt`), capped at 0.5s per tick to prevent browser-throttle bursts
- **Tick rate**: ~100ms (via `setInterval`)
- **Slow loop**: every 800ms — renders producer/upgrade lists, checks achievements, refreshes floating upgrade
- **Sprites** rendered as absolutely-positioned `<img>` elements over the playfield canvas area; positions defined per-producer in `PROD[].sp`
- **Number formatting**: k / M / B / T / exponential
- **Locale**: English (`en-US`)

## LICENCE
© 2026 [$FRANC by FRANCIS LE COQ]. Tous droits réservés.

Ce jeu et son code source sont une création originale dans le cadre du projet $FRANC.
Le code est fourni à titre de consultation. Toute reproduction, redistribution,
modification ou réutilisation, totale ou partielle, sans autorisation écrite
préalable de l'auteur est interdite.

$FRANC / Le Coq Francis et leurs visuels sont des marques du projet.


© 2026 [$FRANC by FRANCIS LE COQ]. All rights reserved.

This game and its source code are proprietary works created for the $FRANC project.
The source code is made available for inspection purposes only. No part of this game, its source code, assets, or related materials may be copied, reproduced, distributed, modified, published, or otherwise reused without the prior written consent of the copyright holder.

$FRANC, Francis Le Coq, and all related names, logos, characters, and visual identities are trademarks and intellectual property of the project.
