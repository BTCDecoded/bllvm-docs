# First Node Setup

Complete guide for setting up and configuring your first BLLVM node.

## Configuration

See [Node Configuration](../node/configuration.md) for complete configuration options.

### Basic Configuration

Create a configuration file `bllvm.toml`:

```toml
[network]
protocol = "regtest"  # or "testnet" or "mainnet"

[storage]
data_dir = "/var/lib/bllvm"

[rpc]
enabled = true
port = 8332
```

### Running with Configuration

```bash
bllvm --config bllvm.toml
```

## Storage

The node stores blockchain data in the configured data directory:

- **Blocks**: Blockchain data
- **UTXO Set**: Unspent transaction outputs
- **Chain State**: Chain metadata and indexes

## Network Connection

The node automatically:
- Discovers peers on the network
- Connects to other nodes
- Syncs blockchain state
- Relays transactions and blocks

## RPC Interface

Once running, interact with the node via JSON-RPC:

```bash
# Get blockchain info
curl -X POST http://localhost:8332 \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "method": "getblockchaininfo", "params": [], "id": 1}'
```

See [RPC API Reference](../node/rpc-api.md) for complete API documentation.

## Security Considerations

⚠️ **Important**: This implementation is designed for pre-production testing and development. Additional hardening is required for production mainnet use.

- Use regtest or testnet for development
- Never expose RPC to untrusted networks
- Use proper authentication for RPC access
- Keep software updated

## Troubleshooting

See [Troubleshooting](../appendices/troubleshooting.md) for common issues and solutions.

