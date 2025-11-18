# Node Configuration

BLLVM node supports flexible configuration for different use cases.

## Protocol Variants

The node supports multiple Bitcoin protocol variants:

- **Regtest** (default): Regression testing network for development
- **Testnet3**: Bitcoin test network
- **BitcoinV1**: Production Bitcoin mainnet

## Configuration File

Create a `bllvm.toml` configuration file:

```toml
[network]
protocol = "regtest"  # or "testnet" or "mainnet"
port = 18444          # P2P port (regtest default)

[storage]
data_dir = "/var/lib/bllvm"
backend = "sled"      # Storage backend

[rpc]
enabled = true
port = 8332
host = "127.0.0.1"    # Bind address

[mining]
enabled = false
```

## Environment Variables

You can also configure via environment variables:

```bash
export BLLVM_NETWORK=testnet
export BLLVM_DATA_DIR=/var/lib/bllvm
export BLLVM_RPC_PORT=8332
```

## Command Line Options

```bash
# Start with specific network
cargo run -- --network testnet

# Use custom config file
cargo run -- --config /path/to/config.toml

# Override data directory
cargo run -- --data-dir /custom/path
```

## Storage Backends

The node supports multiple storage backends:

- **sled**: Default embedded database (recommended)
- **redb**: Alternative embedded database

## Network Configuration

### Transport Options

- **TCP**: Traditional Bitcoin P2P protocol
- **Iroh/QUIC**: Modern transport protocol (experimental)

### Peer Discovery

- Automatic peer discovery on the network
- Manual peer configuration via config file
- DNS seed support for mainnet/testnet

## Security Settings

⚠️ **Important**: Configure security settings for production use:

- RPC authentication
- Network access controls
- Firewall rules
- Rate limiting

