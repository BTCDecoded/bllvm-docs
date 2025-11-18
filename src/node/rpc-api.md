# RPC API Reference

BLLVM node provides a JSON-RPC 2.0 interface for interacting with the node.

## Connection

Default RPC endpoint: `http://localhost:8332`

## Authentication

For production use, configure RPC authentication:

```toml
[rpc]
enabled = true
username = "rpcuser"
password = "rpcpassword"
```

## Example Requests

### Get Blockchain Info

```bash
curl -X POST http://localhost:8332 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "getblockchaininfo",
    "params": [],
    "id": 1
  }'
```

### Get Block

```bash
curl -X POST http://localhost:8332 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "getblock",
    "params": ["000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f"],
    "id": 1
  }'
```

### Get Network Info

```bash
curl -X POST http://localhost:8332 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "getnetworkinfo",
    "params": [],
    "id": 1
  }'
```

## Available Methods

### Blockchain Methods
- `getblockchaininfo` - Get blockchain information
- `getblock` - Get block by hash
- `getblockhash` - Get block hash by height
- `getblockcount` - Get current block height

### Network Methods
- `getnetworkinfo` - Get network information
- `getpeerinfo` - Get connected peers
- `addnode` - Add a peer manually

### Transaction Methods
- `sendrawtransaction` - Broadcast a transaction
- `getrawtransaction` - Get transaction by hash
- `decoderawtransaction` - Decode a raw transaction

### Mining Methods
- `getblocktemplate` - Get block template for mining
- `submitblock` - Submit a mined block

## Implementation Status

{{#include ../../../modules/bllvm-node/docs/status/RPC_IMPLEMENTATION_STATUS.md}}

