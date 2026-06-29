<div align="center">

# 🧠 BlockchainAi — Cortex: AI on Blockchain (Go)

### Official Golang implementation of the Cortex full node — a decentralized blockchain that runs AI/ML model inference on‑chain.

<p>
  <img src="https://img.shields.io/github/license/morpheusadam/BlockchainAi?style=for-the-badge&color=4c1" alt="License" />
  <img src="https://img.shields.io/github/stars/morpheusadam/BlockchainAi?style=for-the-badge&color=ffca28" alt="Stars" />
  <img src="https://img.shields.io/github/forks/morpheusadam/BlockchainAi?style=for-the-badge&color=42a5f5" alt="Forks" />
  <img src="https://img.shields.io/github/last-commit/morpheusadam/BlockchainAi?style=for-the-badge&color=8e44ad" alt="Last commit" />
  <img src="https://img.shields.io/github/repo-size/morpheusadam/BlockchainAi?style=for-the-badge&color=e67e22" alt="Repo size" />
</p>

<p>
  <img src="https://img.shields.io/badge/Go-1.22-00ADD8?style=for-the-badge&logo=go&logoColor=white" alt="Go" />
  <img src="https://img.shields.io/badge/Blockchain-Cortex-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white" alt="Blockchain" />
  <img src="https://img.shields.io/badge/AI%2FML-On--Chain%20Inference-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" alt="AI/ML" />
  <img src="https://img.shields.io/badge/Consensus-PoW%20Cuckoo-512BD4?style=for-the-badge&logo=bitcoinsv&logoColor=white" alt="PoW" />
  <img src="https://img.shields.io/badge/CUDA-GPU-76B900?style=for-the-badge&logo=nvidia&logoColor=white" alt="CUDA" />
  <img src="https://img.shields.io/badge/Build-Make-A42E2B?style=for-the-badge&logo=gnu&logoColor=white" alt="Make" />
</p>

<p>
  <img src="https://skillicons.dev/icons?i=go,cmake,linux,nvidia,docker" alt="Tech" />
</p>

</div>

---

## 📖 Overview

**BlockchainAi** is the **official Golang implementation of Cortex** — a public blockchain that brings **artificial intelligence and machine‑learning inference on‑chain**. Cortex lets smart contracts call AI/ML models directly through the **Cortex Virtual Machine (CVM)**, enabling decentralized AI DApps where model execution is verifiable and reproducible across every node.

The node (Go module `github.com/CortexFoundation/CortexTheseus`) implements the full Cortex protocol: networking, transaction processing, the EVM‑compatible **CVM** runtime, state storage, mining, RPC/console tooling, and a **Proof‑of‑Work** consensus based on the **Cortex Cuckoo cycle**. AI models and input data are distributed via a content‑addressed storage layer, and inference results are computed deterministically (with optional **CUDA/GPU** acceleration) so that on‑chain AI is trustless.

This repository is for **blockchain engineers, AI/ML researchers, miners, and DApp developers** who want to run a Cortex full node, build AI‑powered smart contracts, or experiment with decentralized machine learning.

> 🔎 **Keywords:** AI on blockchain, decentralized AI, Cortex blockchain, on‑chain machine learning, Cortex Virtual Machine (CVM), Golang blockchain node, smart contract AI inference, proof‑of‑work Cuckoo cycle, GPU mining, Web3 AI.

---

## ✨ Features

- 🧠 **On‑chain AI/ML inference** — execute machine‑learning models directly from smart contracts via the **CVM**.
- 🔗 **Full Cortex node** — networking (p2p), state, transactions, consensus, RPC, and console in one binary.
- ⛏️ **Proof‑of‑Work mining** — Cortex **Cuckoo cycle** PoW with optional **CUDA/GPU** acceleration.
- 🤖 **Deterministic CVM** — EVM‑compatible virtual machine extended for verifiable AI model execution.
- 🗂️ **Decentralized model & data storage** — AI models/inputs distributed via content‑addressed (TorrentFS) storage.
- 🧪 **Developer tooling** — CLIs under `cmd/` (`cortex`, `bootnode`, `abigen`, `devp2p`, `keytools`, …).
- 🌐 **Testnet support** — run the **Bernard** testnet for development.
- 🐧 **Cross‑platform builds** — Linux‑first (Ubuntu/CentOS), x64 with `Makefile`‑driven builds.

---

## 🛠️ Tech Stack

| Component | Technology |
| --- | --- |
| Language | Go 1.22 |
| Module | `github.com/CortexFoundation/CortexTheseus` |
| Virtual machine | Cortex Virtual Machine (CVM), EVM‑compatible |
| Consensus | Proof‑of‑Work (Cortex Cuckoo cycle) |
| AI runtime | CVM runtime (`libcvm_runtime.so`), optional CUDA/GPU |
| Storage | Content‑addressed model/data storage (TorrentFS) |
| Build | Make, CMake, GCC/G++ |

---

## 🚀 Getting Started

### Prerequisites

- **Go 1.20+** (built/tested with Go 1.22)
- **CMake 3.11.0+**, **GCC/G++ 5.4+**, **make**
- **8 GB+ RAM** recommended for compilation
- x64 CPU (AVX2 recommended)
- *(Optional, for GPU mining)* **CUDA 9.2+** and a compatible **NVIDIA driver (396.37+)**
- Linux (Ubuntu 18.04+ recommended; CentOS 7.6 supported but not recommended)

### Build from source

```bash
git clone --recursive https://github.com/CortexFoundation/CortexTheseus.git
cd CortexTheseus
make clean && make -j$(nproc)
```

Verify the CVM runtime library links correctly:

```bash
ldd plugins/libcvm_runtime.so
```

> If it fails, run `rm -rf cvm-runtime && git submodule init && git submodule update`, then rebuild.

### Run a full node

```bash
cd CortexTheseus
export LD_LIBRARY_PATH=$PWD:$PWD/plugins:$LD_LIBRARY_PATH
./build/bin/cortex
```

View all available options:

```bash
./build/bin/cortex --help
```

### Run the developer testnet (Bernard)

```bash
./cortex --bernard
```

---

## 🔗 Related Projects

| Project | Description |
| --- | --- |
| [cvm-runtime](https://github.com/CortexFoundation/cvm-runtime) | CVM runtime — the AI inference container |
| [torrentfs](https://github.com/CortexFoundation/torrentfs) | Decentralized file/model storage layer |
| [inference](https://github.com/CortexFoundation/inference) | AI wrapper — fixed API for inference & storage |
| [solution](https://github.com/CortexFoundation/solution) | PoW — Cortex Cuckoo cycle |
| [rosetta-cortex](https://github.com/CortexFoundation/rosetta-cortex) | Rosetta API integration |
| [docker](https://github.com/CortexFoundation/docker) | Docker images & deployment |

---

## 🗂️ Project Structure

```text
BlockchainAi/
├── cmd/            # CLIs: cortex, bootnode, abigen, devp2p, keytools, …
├── consensus/      # Proof-of-Work consensus (Cuckoo cycle)
├── core/           # Blockchain core, state & transaction processing
├── ctxc/           # Cortex protocol & full-node service
├── miner/          # Mining
├── p2p/            # Peer-to-peer networking
├── rpc/            # JSON-RPC layer
├── console/        # Interactive JS console
├── crypto/         # Cryptography primitives
├── pow/            # Proof-of-Work
├── params/         # Network & chain parameters
├── genesis.json    # Genesis configuration
├── go.mod          # Go module definition
└── Makefile        # Build automation
```

---

## 🤝 Contributing

Contributions are welcome! Please review [`CODINGSTYLE.md`](CODINGSTYLE.md), then open an
[issue](https://github.com/morpheusadam/BlockchainAi/issues) or submit a pull request.

## 📜 License

The library packages are licensed under **GNU LGPL‑3.0** (`COPYING.LESSER`); the
command‑line binaries are licensed under **GNU GPL‑3.0** (`COPYING`). See
[`LICENSE`](LICENSE), [`COPYING`](COPYING), and [`COPYING.LESSER`](COPYING.LESSER) for details.

---

<div align="center">

### 👤 Author — Morpheus Adam

Web developer & cheerful hacker · PHP · Laravel · Go

<p>
  <a href="https://github.com/morpheusadam"><img src="https://img.shields.io/badge/GitHub-morpheusadam-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>
  <a href="https://sam.zeonic.me"><img src="https://img.shields.io/badge/Website-sam.zeonic.me-4c1?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Website" /></a>
  <a href="mailto:morpheusadam95@gmail.com"><img src="https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

⭐ **If this decentralized‑AI node interests you, consider giving it a star!** ⭐

</div>
