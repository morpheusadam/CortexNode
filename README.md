# Cortex Node

A Go implementation of the Cortex full node, a blockchain whose virtual machine can run AI and machine-learning model inference on-chain, intended for blockchain engineers, miners, and developers building AI-powered smart contracts.

[![License](https://img.shields.io/github/license/morpheusadam/CortexNode?style=flat-square)](LICENSE)
[![Go](https://img.shields.io/badge/Go-1.22-00ADD8?style=flat-square&logo=go&logoColor=white)](https://go.dev)
[![Last commit](https://img.shields.io/github/last-commit/morpheusadam/CortexNode?style=flat-square)](https://github.com/morpheusadam/CortexNode/commits)

## Overview

Cortex is a public blockchain that lets smart contracts call AI and machine-learning models directly through the Cortex Virtual Machine (CVM), so model execution is verifiable and reproducible across every node.

This node (Go module `github.com/CortexFoundation/CortexTheseus`) implements the full Cortex protocol: peer-to-peer networking, transaction processing, the EVM-compatible CVM runtime, state storage, mining, and RPC and console tooling. Consensus is proof-of-work based on the Cortex Cuckoo cycle. AI models and input data are distributed through a content-addressed storage layer, and inference results are computed deterministically, with optional CUDA and GPU acceleration.

### What it provides

- On-chain AI and ML inference: machine-learning models executed from smart contracts via the CVM.
- A full node in one binary: p2p networking, state, transactions, consensus, RPC and console.
- Proof-of-work mining using the Cortex Cuckoo cycle, with optional CUDA and GPU acceleration.
- An EVM-compatible virtual machine extended for verifiable AI model execution.
- Decentralized model and data storage over content-addressed storage (TorrentFS).
- Command-line tools under `cmd/`: `cortex`, `bootnode`, `abigen`, `devp2p`, `keytools` and others.
- The Bernard testnet for development.
- Linux-first builds (Ubuntu and CentOS) on x64, driven by a `Makefile`.

### Components

| Component | Technology |
| --- | --- |
| Language | Go 1.22 |
| Module | `github.com/CortexFoundation/CortexTheseus` |
| Virtual machine | Cortex Virtual Machine (CVM), EVM-compatible |
| Consensus | Proof-of-work (Cortex Cuckoo cycle) |
| AI runtime | CVM runtime (`libcvm_runtime.so`), optional CUDA and GPU |
| Storage | Content-addressed model and data storage (TorrentFS) |
| Build | Make, CMake, GCC/G++ |

## Requirements

- Go 1.20 or newer (built and tested with Go 1.22)
- CMake 3.11.0 or newer, GCC/G++ 5.4 or newer, and make
- 8 GB or more of RAM for compilation
- An x64 CPU; AVX2 recommended
- Linux. Ubuntu 18.04 or newer is recommended; CentOS 7.6 is supported but not recommended
- For GPU mining only: CUDA 9.2 or newer and an NVIDIA driver 396.37 or newer

## Install

Build from source:

```bash
git clone --recursive https://github.com/CortexFoundation/CortexTheseus.git
cd CortexTheseus
make clean && make -j$(nproc)
```

Verify that the CVM runtime library links correctly:

```bash
ldd plugins/libcvm_runtime.so
```

If that fails, run `rm -rf cvm-runtime && git submodule init && git submodule update`, then rebuild.

## Usage

Run a full node:

```bash
cd CortexTheseus
export LD_LIBRARY_PATH=$PWD:$PWD/plugins:$LD_LIBRARY_PATH
./build/bin/cortex
```

List all available options:

```bash
./build/bin/cortex --help
```

Run the developer testnet (Bernard):

```bash
./cortex --bernard
```

## Project structure

```text
├── cmd/            CLIs: cortex, bootnode, abigen, devp2p, keytools and others
├── consensus/      Proof-of-work consensus (Cuckoo cycle)
├── core/           Blockchain core, state and transaction processing
├── ctxc/           Cortex protocol and full-node service
├── miner/          Mining
├── p2p/            Peer-to-peer networking
├── rpc/            JSON-RPC layer
├── console/        Interactive JS console
├── crypto/         Cryptography primitives
├── pow/            Proof-of-work
├── params/         Network and chain parameters
├── genesis.json    Genesis configuration
├── go.mod          Go module definition
└── Makefile        Build automation
```

## Related projects

| Project | Description |
| --- | --- |
| [cvm-runtime](https://github.com/CortexFoundation/cvm-runtime) | CVM runtime, the AI inference container |
| [torrentfs](https://github.com/CortexFoundation/torrentfs) | Decentralized file and model storage layer |
| [inference](https://github.com/CortexFoundation/inference) | AI wrapper with a fixed API for inference and storage |
| [solution](https://github.com/CortexFoundation/solution) | Proof-of-work, Cortex Cuckoo cycle |
| [rosetta-cortex](https://github.com/CortexFoundation/rosetta-cortex) | Rosetta API integration |
| [docker](https://github.com/CortexFoundation/docker) | Docker images and deployment |

## Contributing

Review [`CODINGSTYLE.md`](CODINGSTYLE.md), then open an [issue](https://github.com/morpheusadam/CortexNode/issues) or submit a pull request.

## Author

Morpheus Adam — [GitHub](https://github.com/morpheusadam) · [sam.zeonic.me](https://sam.zeonic.me) · morpheusadam95@gmail.com

## License

The library packages are licensed under GNU LGPL-3.0 (`COPYING.LESSER`); the command-line binaries are licensed under GNU GPL-3.0 (`COPYING`). See [`LICENSE`](LICENSE), [`COPYING`](COPYING), and [`COPYING.LESSER`](COPYING.LESSER) for details.
