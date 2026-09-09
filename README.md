# Vectorix Pump.fun launchpad

**Vectorix (`vectorix-cross`)** — one repo for a Pump.fun-style Solana launchpad: bonding-curve program, Next.js UI, and indexer API.

Create an SPL mint, trade on the curve, then graduate liquidity to Raydium (AMM or CPMM). Token-2022, fee split, and vesting live in the program. This cut is the public stack. Keys stay in `.env`. No deployer keypair is committed.

| Channel | Link |
|---------|------|
| **Email** | [vanjasretenovic4@gmail.com](mailto:vanjasretenovic4@gmail.com) |
| **Telegram** | [@vectoris_corss](https://t.me/vectoris_corss) |
| **Discord** | [vectorix-cross](https://discord.com/users/775389898794336316) |
| **X** | [@vectorix_cross](https://x.com/vectorix_cross) |
| **GitHub** | [vectorix-cross](https://github.com/vectorix-cross) |
| **Portfolio** | [Featured projects](https://github.com/vectorix-cross/portfolio) |

---

## What ships in this repo

| Path | Role |
| --- | --- |
| [`contract`](contract) | Anchor program: virtual LP, swap, fees, vesting, Raydium migrate |
| [`frontend`](frontend) | Next.js: wallet, IPFS metadata, create-coin, swap, chart, holders |
| [`backend`](backend) | API + sockets: program events, coins, candles, Raydium pool create |

```
Wallet ──► frontend ──► program (contract)
                │
                └──► backend (events, charts, auth)
```

**Program instructions** (`contract/programs/pump`): `initialize` (fee), `add_liquidity`, `remove_liquidity`, `swap`, vesting + migrate helpers. Program id in this tree: `7wUQXRQtBzTmyp9kcrmok9FKcc4RSYXxPYN9FGDLnqxb` (replace on your deploy).

---

## Why teams use this stack

- Bonding curve instead of a raw Raydium pool on day one
- Fee split that can pay the launch desk and a referral side
- Vesting + migrate to AMM or CPMM when the curve completes
- UI that already talks to the same IDL the backend indexes

Devnet examples:

- Remove virtual LP + create Raydium pool: [tx](https://explorer.solana.com/tx/4L6MWmtV1ZsT8NFfbtu68ZYyYVbpvZ4iynJhPdZw8jESi28TxwojjTFs88Q5QRdNUb297aWfkKcoYP9Ya8npx8AV?cluster=devnet)
- Fee distribution: [tx](https://solscan.io/tx/4e25Sv3rDS9rqb9pXyoYwHRtXhnteTGZCGyrchcPwHoKFCNVS2v2aEy6UVXqHQDnVxsCSuBgK2DUcg3NmHizM1b1?cluster=devnet)

---

## Contract

```bash
cd contract
yarn
anchor build
# optional
anchor test
```

Need: Rust, Anchor CLI, Solana CLI. Deploy to a cluster you control. Keep `id.json` / program keypairs out of git.

---

## Frontend

Wallet connect (Phantom / Solflare), Pinata / IPFS metadata, token launch, swap against the curve, holders, chat.

```bash
cd frontend
yarn
cp .env.example .env.local
yarn dev
```

Typical env: RPC URL, program id, backend origin, Pinata JWT (never commit the JWT).

---

## Backend

Program event handler, coin and trade routes, chart candles, JWT auth, sockets, Raydium pool create helper.

```bash
cd backend
yarn
cp .env.example .env
yarn start
```

Mongo (or the URI in `.env`) plus an RPC. Do not commit `id.json`.

---

## Status

Public tree is the launchpad stack. PumpSwap routing and some production guards stay in private cuts. Not audited. Custom brand, fee split, or a mainnet deploy: use the contact table.
