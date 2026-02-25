<p align="center">
  <img src="https://mythic.sh/brand/mythic-logo.svg" alt="Mythic L2" width="120" />
</p>

<h1 align="center">Mythic L2</h1>

<p align="center">
  <strong>The AI-Native Layer 2 on Solana</strong>
</p>

<p align="center">
  <a href="https://github.com/MythicFoundation/mythic-mainnet-beta/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-39FF14?style=flat-square" alt="License" /></a>
  <a href="https://github.com/MythicFoundation/mythic-mainnet-beta/actions"><img src="https://img.shields.io/badge/Build-Passing-39FF14?style=flat-square" alt="Build" /></a>
  <a href="https://solana.com"><img src="https://img.shields.io/badge/Solana-v2.0-7B2FFF?style=flat-square" alt="Solana" /></a>
  <a href="https://mythic.sh"><img src="https://img.shields.io/badge/Network-Live-39FF14?style=flat-square" alt="Network" /></a>
</p>

<p align="center">
  <a href="https://mythic.sh">Website</a> &nbsp;|&nbsp;
  <a href="https://mythic.sh/docs">Docs</a> &nbsp;|&nbsp;
  <a href="https://mythicswap.app">DEX</a> &nbsp;|&nbsp;
  <a href="https://mythic.money">Launchpad</a> &nbsp;|&nbsp;
  <a href="https://mythic.foundation">Governance</a> &nbsp;|&nbsp;
  <a href="https://mythiclabs.io">Labs</a>
</p>

---

## Overview

Mythic L2 is a high-performance Layer 2 network built on Solana, purpose-built for AI workloads. It extends the Solana Virtual Machine with native AI inference precompiles, a decentralized compute marketplace, and a full DeFi stack -- all settled back to Solana L1 for security.

Every on-chain program is written in native `solana_program` Rust (no Anchor) for maximum performance and minimal runtime overhead. The protocol implements real `spl_token::burn` mechanics with a 50/10/40 validator/foundation/burn fee split across all transaction types.

## Architecture

Mythic L2 comprises 11 core on-chain programs, a cross-chain bridge, and a suite of off-chain services:

### Core Programs

| Program | Description | Program ID |
|---------|-------------|------------|
| **Bridge (L1)** | Lock-and-mint escrow on Solana mainnet | `MythBrdg11111111111111111111111111111111111` |
| **Bridge (L2)** | L2-side mint/burn for wrapped assets | `MythBrdgL2111111111111111111111111111111111` |
| **Settlement** | State root settlement to Solana L1 | `MythSett1ement11111111111111111111111111111` |
| **MYTH Token** | Native token with fee distribution and burn | `MythToken1111111111111111111111111111111111` |
| **Swap** | Constant-product AMM DEX | `MythSwap11111111111111111111111111111111111` |
| **Staking** | Synthetix-style reward accumulator staking | `MythStak11111111111111111111111111111111111` |
| **Governance** | On-chain DAO governance | `MythGov111111111111111111111111111111111111` |
| **Launchpad** | Bonding curve token launchpad | `MythPad111111111111111111111111111111111111` |
| **Airdrop** | Merkle-based token distribution | `MythDrop11111111111111111111111111111111111` |
| **AI Precompiles** | Native AI inference and verification in the SVM | `CT1yUSX8n5uid5PyrPYnoG5H6Pp2GoqYGEKmMehq3uWJ` |
| **Compute Market** | Decentralized GPU/CPU/storage marketplace | `AVWSp12ji5yoiLeC9whJv5i34RGF5LZozQin6T58vaEh` |

### Off-Chain Services

| Service | Description |
|---------|-------------|
| **Relayer** | Cross-chain message relayer between L1 and L2 |
| **Settlement Service** | Batches and submits state roots to L1 |
| **Supply Oracle** | Real-time token supply and burn tracking |
| **AI Gateway** | Routes inference requests to compute providers |
| **Inference Server** | Executes AI model inference on GPU nodes |
| **Reward Distributor** | Distributes validator and staker rewards |

## Network Stats

| Metric | Value |
|--------|-------|
| Block Time | ~400ms |
| Theoretical TPS | 10,000+ |
| Active Programs | 11 |
| Bridge Challenge Period | ~42 hours |
| Fee Burn Rate | 40% of all fees |

## Quick Start

### Prerequisites

- Rust 1.75+ with the `nightly` toolchain
- Solana CLI 3.0.x (`cargo install solana-cli`)
- Node.js 20+

### Build All Programs

```bash
git clone https://github.com/MythicFoundation/mythic-mainnet-beta.git
cd mythic-mainnet-beta
cargo build-sbf
```

### Build a Specific Program

```bash
cargo build-sbf --manifest-path programs/bridge/Cargo.toml
```

### Run Tests

```bash
cargo test --workspace
```

## Directory Structure

```
mythic-mainnet-beta/
├── programs/
│   ├── bridge/              # L1 lock-and-mint bridge escrow
│   ├── bridge-l2/           # L2 wrapped asset mint/burn
│   ├── settlement/          # State root settlement to L1
│   ├── myth-token/          # MYTH token fee logic and burn
│   ├── swap/                # Constant-product AMM
│   ├── staking/             # Synthetix-style staking
│   ├── governance/          # DAO governance
│   ├── launchpad/           # Bonding curve launchpad
│   ├── airdrop/             # Merkle airdrop distribution
│   ├── ai-precompiles/      # Native AI inference precompiles
│   └── compute-market/      # Decentralized compute marketplace
├── genesis/                 # Genesis block configuration
├── relayer/                 # Cross-chain message relayer
├── sdk/                     # Rust SDK for client integration
├── services/
│   ├── ai-gateway/          # AI inference routing
│   ├── inference-server/    # GPU inference execution
│   ├── reward-distributor/  # Validator reward distribution
│   └── supply-oracle/       # Token supply tracking
├── keys/                    # Deterministic keypairs
├── scripts/                 # Deployment and init scripts
└── website/                 # mythic.sh frontend
```

## Token Economics

The MYTH token powers the entire Mythic L2 ecosystem:

- **Gas fees** -- paid in MYTH for all L2 transactions
- **Compute fees** -- paid to GPU providers for AI inference
- **Bridge fees** -- charged on cross-chain transfers
- **Staking rewards** -- earned by validators and delegators
- **Burn mechanism** -- 40% of all protocol fees are permanently burned

Fee distribution: **50% validators / 10% foundation / 40% burn**

## Ecosystem

| Project | Repository | Live URL |
|---------|------------|----------|
| Mythic L2 | [mythic-mainnet-beta](https://github.com/MythicFoundation/mythic-mainnet-beta) | [mythic.sh](https://mythic.sh) |
| MythicSwap | [mythic-swap](https://github.com/MythicFoundation/mythic-swap) | [mythicswap.app](https://mythicswap.app) |
| MythicPad | [mythic-money](https://github.com/MythicFoundation/mythic-money) | [mythic.money](https://mythic.money) |
| Block Explorer | [mythic-explorer](https://github.com/MythicFoundation/mythic-explorer) | [explorer.mythic.sh](https://explorer.mythic.sh) |
| Mythic Wallet | [mythic-wallet](https://github.com/MythicFoundation/mythic-wallet) | [wallet.mythic.sh](https://wallet.mythic.sh) |
| Explorer API | [mythic-explorer-api](https://github.com/MythicFoundation/mythic-explorer-api) | [api.mythic.sh](https://api.mythic.sh) |
| Foundation | -- | [mythic.foundation](https://mythic.foundation) |
| MythicLabs | -- | [mythiclabs.io](https://mythiclabs.io) |

## Security

The security of Mythic L2 is a top priority. If you discover a vulnerability, please report it responsibly.

**Responsible Disclosure:**
- Email: security@mythic.sh
- Do NOT open public issues for security vulnerabilities
- We will acknowledge receipt within 24 hours
- We aim to provide a fix within 72 hours for critical issues

### Audits

All on-chain programs undergo internal security review before deployment. Third-party audit reports will be published as they are completed.

## Contributing

We welcome contributions from the community. To get started:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Write tests for your changes
4. Ensure all tests pass (`cargo test --workspace`)
5. Submit a pull request

Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting a PR.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<p align="center">
  Built by <a href="https://mythiclabs.io">MythicLabs</a>
</p>
