# 🏟 Private Stadium Access Credential

A privacy-preserving smart contract built on Midnight that allows fans to prove they hold a valid Season Pass or VIP credential using Zero-Knowledge (ZK) proofs — without revealing their identity or linking attendance records.

---

## 🔐 Problem

Traditional stadium access systems:
- Collect personal identity data
- Track attendance per person
- Risk data leaks
- Link physical identity to event history

This project solves that using Zero-Knowledge Proofs on Midnight.

---

## 💡 Solution

Fans prove they:
- ✅ Hold a valid season pass  
- ✅ Have a valid VIP credential  

Without revealing:
- ❌ Name  
- ❌ Physical identity  
- ❌ Wallet history  
- ❌ Credential serial number  

Only proof validity is verified on-chain.

---

## 🏗 Built With

- Midnight Compact Language
- Zero-Knowledge Proof Verification
- TypeScript Deployment Scripts

---

## 📁 Project Structure

```
private-stadium-access-credential/
│
├── contracts/
│   ├── wallet.compact
│   └── managed/
│
├── src/
│   └── deploy.ts
│
├── package.json
├── tsconfig.json
└── README.md
```

---

## 📜 Smart Contract (wallet.compact)

```rust
pragma language_version >= 0.20;

import CompactStandardLibrary;

// Public state
export ledger attendance_count: Counter;

// Verifier for ZK proof
export ledger pass_verifier: Verifier;

// Circuit to verify season pass proof
export circuit attend_event(proof: Proof): [] {

  assert(pass_verifier.verify(proof));

  attendance_count.increment(1);
}
```

---

## 🚀 Getting Started

### 1️⃣ Requirements

- Node.js v22+
- Docker
- Midnight CLI
- Lace Wallet (Chrome Extension)

---

### 2️⃣ Install Dependencies

```bash
yarn install
```

---

### 3️⃣ Compile Contract

```bash
compact compile contracts/wallet.compact contracts/managed/wallet
```

---

### 4️⃣ Set Private Key

Linux / macOS:
```bash
export PRIVATE_KEY=0xYOUR_PRIVATE_KEY
```

Windows PowerShell:
```powershell
setx
