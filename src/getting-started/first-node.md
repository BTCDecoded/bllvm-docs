# First Node Setup

Complete guide for setting up and configuring your first BLLVM node.

## Configuration

### Protocol Variants

BLLVM supports multiple Bitcoin protocol variants:

- **Regtest** (default): Regression testing network for development
- **Testnet3**: Bitcoin test network
- **BitcoinV1**: Production Bitcoin mainnet

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
cargo run -- --config bllvm.toml
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

### Node Won't Start

- Check Rust version: `rustc --version` (requires 1.70+)
- Verify all dependencies are available
- Check configuration file syntax

### Can't Connect to Network

- Verify network settings match your intended network
- Check firewall settings
- Ensure ports are accessible

### Sync Issues

- Check network connectivity
- Verify you're on the correct network (testnet vs mainnet)
- Review logs for specific errors

See [Troubleshooting](../appendices/troubleshooting.md) for more help.

