# Installation

This guide covers installing and building BLLVM components.

## Prerequisites

- **Rust 1.70+**: Required for all BLLVM components
- **Git**: For cloning repositories
- **Cargo**: Comes with Rust installation

## Installing bllvm-node

The reference node is the main entry point for running a BLLVM node.

### Quick Start

```bash
git clone https://github.com/BTCDecoded/bllvm-node
cd bllvm-node
cargo build --release
```

The build automatically fetches dependencies (bllvm-consensus, bllvm-protocol) from GitHub.

### Local Development Setup

If you're developing multiple BLLVM components together:

1. Clone all repositories:
   ```bash
   git clone https://github.com/BTCDecoded/bllvm-consensus
   git clone https://github.com/BTCDecoded/bllvm-protocol
   git clone https://github.com/BTCDecoded/bllvm-node
   ```

2. Set up local path dependencies in `bllvm-node/.cargo/config.toml`:
   ```toml
   [patch."https://github.com/BTCDecoded/bllvm-consensus"]
   bllvm-consensus = { path = "../bllvm-consensus" }
   
   [patch."https://github.com/BTCDecoded/bllvm-protocol"]
   bllvm-protocol = { path = "../bllvm-protocol" }
   ```

3. Build:
   ```bash
   cd bllvm-node
   cargo build
   ```

Changes to dependencies are now immediately reflected without git push.

## Installing bllvm-sdk

The developer SDK provides governance cryptographic primitives and CLI tools.

```bash
git clone https://github.com/BTCDecoded/bllvm-sdk
cd bllvm-sdk
cargo build --release
```

This builds the CLI tools:
- `bllvm-keygen` - Generate governance keypairs
- `bllvm-sign` - Sign governance messages
- `bllvm-verify` - Verify signatures and multisig thresholds

## Installing bllvm-consensus

The consensus layer is typically used as a library dependency, but can be built standalone:

```bash
git clone https://github.com/BTCDecoded/bllvm-consensus
cd bllvm-consensus
cargo build --release
```

## Testing Installation

After building, verify the installation:

```bash
# Test bllvm-node
cd bllvm-node
cargo test

# Test bllvm-sdk
cd bllvm-sdk
cargo test

# Test bllvm-consensus
cd bllvm-consensus
cargo test --all-features
```

## Next Steps

- See [Quick Start](quick-start.md) for running your first node
- See [First Node Setup](first-node.md) for detailed configuration

