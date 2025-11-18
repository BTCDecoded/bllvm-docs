# Quick Start

Get up and running with BLLVM in minutes.

## Running Your First Node

### Regtest Mode (Recommended for Development)

Regtest mode is safe for development - it creates an isolated network:

```bash
cd bllvm-node
cargo run
```

This starts a node in regtest mode (default), which:
- Creates an isolated network
- Allows instant block generation
- Perfect for testing and development

### Testnet Mode

Connect to Bitcoin testnet:

```bash
cargo run -- --network testnet
```

### Mainnet Mode

⚠️ **Warning**: Only use mainnet if you understand the risks.

```bash
cargo run -- --network mainnet
```

## Basic Node Operations

### Creating a Node Programmatically

```rust
use bllvm_node::{Node, ProtocolVersion};

// Default: Regtest for safe development
let node = Node::new(None)?;

// Explicit testnet
let testnet_node = Node::new(Some(ProtocolVersion::Testnet3))?;

// Mainnet (use with caution)
let mainnet_node = Node::new(Some(ProtocolVersion::BitcoinV1))?;
```

### Running the Node

The node will:
- Connect to the P2P network
- Sync blockchain state
- Accept RPC commands
- Mine blocks (if configured)

## Using the SDK

### Generate a Governance Keypair

```bash
bllvm-keygen --output my-key.key
```

### Sign a Message

```bash
bllvm-sign release \
  --version v1.0.0 \
  --commit abc123 \
  --key my-key.key \
  --output signature.txt
```

### Verify Signatures

```bash
bllvm-verify release \
  --version v1.0.0 \
  --commit abc123 \
  --signatures sig1.txt,sig2.txt,sig3.txt \
  --threshold 3-of-5 \
  --pubkeys keys.json
```

## Next Steps

- [First Node Setup](first-node.md) - Detailed configuration guide
- [Node Configuration](../node/configuration.md) - Full configuration options
- [RPC API Reference](../node/rpc-api.md) - Interact with your node

