# Network Protocol

The protocol layer abstracts Bitcoin's P2P network protocol, enabling support for multiple network variants.

## Protocol Abstraction

The bllvm-protocol provides abstraction for:

- **P2P Message Formats**: Standard Bitcoin wire protocol messages
- **Connection Management**: Network connection handling
- **Peer Discovery**: Finding and connecting to peers
- **Block Synchronization**: Downloading and validating blocks
- **Transaction Relay**: Broadcasting transactions

## Network Variants

### Mainnet (BitcoinV1)
- Production Bitcoin network
- Full consensus rules
- Real economic value

### Testnet3
- Bitcoin test network
- Same consensus rules as mainnet
- Different network parameters
- No real economic value

### Regtest
- Regression testing network
- Configurable difficulty
- Isolated from other networks
- Fast block generation for testing

For implementation details, see the [bllvm-protocol README](../../modules/bllvm-protocol/README.md).

