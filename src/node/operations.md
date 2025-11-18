# Node Operations

Operational guide for running and maintaining a BLLVM node.

## Starting the Node

### Basic Startup

```bash
# Regtest mode (default, safe for development)
cargo run

# Testnet mode
cargo run -- --network testnet

# Mainnet mode (use with caution)
cargo run -- --network mainnet
```

### With Configuration

```bash
cargo run -- --config bllvm.toml
```

## Node Lifecycle

### Initial Sync

When starting for the first time, the node will:

1. Connect to the P2P network
2. Discover peers
3. Download and validate blockchain history
4. Build UTXO set
5. Sync to current block height

### Running State

Once synced, the node:

- Maintains connections to peers
- Relays transactions and blocks
- Validates new blocks
- Updates chain state
- Serves RPC requests

## Monitoring

### Health Checks

```bash
# Check if node is running
curl http://localhost:8332/health

# Get blockchain info via RPC
curl -X POST http://localhost:8332 \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "method": "getblockchaininfo", "params": [], "id": 1}'
```

### Logging

The node uses structured logging:

```bash
# Set log level
RUST_LOG=info cargo run

# Debug mode
RUST_LOG=debug cargo run

# Trace all operations
RUST_LOG=trace cargo run
```

## Maintenance

### Database Maintenance

The node automatically maintains:

- Block storage
- UTXO set
- Chain indexes
- Transaction indexes

### Backup

Regular backups recommended:

```bash
# Backup data directory
tar -czf bllvm-backup-$(date +%Y%m%d).tar.gz /var/lib/bllvm
```

### Updates

When updating the node:

1. Stop the node gracefully
2. Backup data directory
3. Update code
4. Rebuild: `cargo build --release`
5. Restart node

## Troubleshooting

### Node Won't Sync

- Check network connectivity
- Verify you're on correct network
- Check firewall settings
- Review logs for errors

### High Memory Usage

- Consider pruning old blocks
- Adjust cache sizes in config
- Monitor UTXO set size

### Connection Issues

- Verify ports are accessible
- Check peer discovery
- Review network configuration

