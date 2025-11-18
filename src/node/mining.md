# Mining Integration

The reference node includes mining coordination functionality as part of the Bitcoin protocol.

## Mining Components

### Block Template Generation
- Create blocks from mempool transactions
- Select transactions based on fee priority
- Generate coinbase transaction
- Calculate merkle root

### Mining Process
- Block template creation
- Nonce finding and proof-of-work
- Block submission and validation

## Mining Integration

The node provides:
- **Block Template API**: Generate blocks for mining
- **Mining Coordination**: Coordinate with mining hardware/software
- **Stratum Support**: Optional Stratum V2 support (feature-gated)

For implementation details, see the [bllvm-node README](../../modules/bllvm-node/README.md).

