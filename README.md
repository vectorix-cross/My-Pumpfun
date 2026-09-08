# Vectorix Pump.fun launchpad

**Vectorix (`vectorix-cross`)** — one repo for the Pump.fun-style Solana launchpad: bonding-curve program, Next.js UI, and indexer API.

Create an SPL mint, trade on the curve, then graduate liquidity to Raydium (AMM or CPMM). Token-2022, fee split, and vesting live in the program. This cut is the public stack. Keys stay in `.env`. No deployer keypair is committed.

| Channel | Link |
|---------|------|
| **Email** | [vanjasretenovic4@gmail.com](mailto:vanjasretenovic4@gmail.com) |
| **Telegram** | [@vectoris_corss](https://t.me/vectoris_corss) |
| **Discord** | [vectorix-cross](https://discord.com/users/775389898794336316) |
| **X** | [@vectorix_cross](https://x.com/vectorix_cross) |
| **GitHub** | [vectorix-cross](https://github.com/vectorix-cross) |

---

## Layout

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

---

## Contract

Bonding-curve launchpad with virtual LP add/remove, buy/sell, fee distribution, token vesting, and migrate to Raydium AMM or CPMM.

Devnet examples:

- Remove virtual LP + create Raydium pool: [tx](https://explorer.solana.com/tx/4L6MWmtV1ZsT8NFfbtu68ZYyYVbpvZ4iynJhPdZw8jESi28TxwojjTFs88Q5QRdNUb297aWfkKcoYP9Ya8npx8AV?cluster=devnet)
- Fee distribution: [tx](https://solscan.io/tx/4e25Sv3rDS9rqb9pXyoYwHRtXhnteTGZCGyrchcPwHoKFCNVS2v2aEy6UVXqHQDnVxsCSuBgK2DUcg3NmHizM1b1?cluster=devnet)

```bash
cd contract
yarn
anchor build
```

---

## Frontend

Wallet connect (Phantom / Solflare), Pinata / IPFS metadata, token launch, swap against the curve, holders, and chat.

```bash
cd frontend
yarn
yarn dev
```

Copy `frontend/.env.example` to `.env.local`. Do not put Pinata or RPC secrets in git.

---

## Backend

Program event handler, coin and trade routes, chart candles, JWT auth, sockets.

```bash
cd backend
yarn
# copy .env.example → .env
yarn start
```

---

## Contact

Custom launchpad, PumpSwap path, or production deploy: use the table at the top.
