# LastVault Standalone Claim

**Recover your vault inheritance without LastVault servers. Zero dependency.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## What Is This?

This is a **self-contained HTML file** that allows an heir to claim their digital inheritance directly from the blockchain, even if LastVault's servers no longer exist. It requires only:

1. A web browser
2. An Ethereum RPC endpoint (any provider: Infura, Alchemy, or a local node)
3. The heir's private key (from their MetaMask, seed phrase, or raw key)
4. The smart contract address (provided by the vault owner)

## Why Does This Exist?

LastVault's core promise is **20+ year durability**. We cannot guarantee our company will exist in 20 years, but we CAN guarantee that:

- The blockchain will persist (Ethereum, Base, etc.)
- This HTML file works with nothing but a browser and an RPC endpoint
- The heir can decrypt the payload with standard cryptographic libraries

**No server. No API. No LastVault account needed.**

## How It Works

```
1. Heir opens index.html in any browser
2. Enters the smart contract address
3. Selects the blockchain network (Base, Ethereum, etc.)
4. Connects wallet or enters private key
5. HTML reads encryptedPayload from the on-chain contract (gas-free)
6. Performs ECIES decryption locally in the browser:
   - ECDH key agreement (secp256k1)
   - HKDF-SHA256 key derivation
   - AES-256-GCM decryption
7. Displays the recovered vault master key
```

## Supported Networks

| Network | Chain ID | RPC |
|---------|----------|-----|
| Base Mainnet | 8453 | https://mainnet.base.org |
| Base Sepolia | 84532 | https://sepolia.base.org |
| Ethereum Mainnet | 1 | https://eth.llamarpc.com |
| Ethereum Sepolia | 11155111 | https://rpc.sepolia.org |

## Security

- **All cryptography runs locally in your browser** — no data is sent anywhere
- **No external dependencies loaded at runtime** — ethers.js is embedded
- **Works offline** after the contract data is fetched (can cache the encrypted payload)
- **Standard algorithms** — secp256k1, HKDF-SHA256, AES-256-GCM (Web Crypto API)

## Usage

### Option 1: Open directly

Just double-click `index.html` in your browser.

### Option 2: Host on IPFS

```bash
ipfs add index.html
```

Pin it for permanent availability.

### Option 3: GitHub Pages

Fork this repo and enable GitHub Pages — the claim page will be available at `https://yourusername.github.io/lastvault-claim/`

## Part of the LastVault Ecosystem

- **Smart Contract** — [lastvault-contracts](https://github.com/lastvault-io/lastvault-contracts)
- **Desktop App** — .NET 9 MAUI Blazor Hybrid
- **Mobile App** — Android (push approval, BLE, PIN lock)
- **Hardware Key** — Custom USB security key with secure element + NFC
- **Heir Portal** — [heir.lastvault.io](https://heir.lastvault.io)
- **Website** — [lastvault.io](https://lastvault.io)

## License

MIT License. See [LICENSE](LICENSE).

---

**Built by [Divara Technology Inc.](https://lastvault.io)** | Your digital legacy, secured forever.
