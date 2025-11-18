# Module Development

The SDK provides a composition framework for building custom Bitcoin implementations through declarative module composition.

## Module System

The module system allows you to:

- **Compose Custom Nodes**: Declaratively assemble Bitcoin nodes from modules
- **Module Registry**: Register and manage modules
- **Economic Integration**: Integrate modules through merge mining
- **Lifecycle Management**: Manage module loading and execution

## Module Development

Modules are sandboxed, secure components that can extend Bitcoin functionality:

- **Sandboxed Execution**: Modules run in isolated environments
- **Secure Loading**: Cryptographic verification of module integrity
- **API Integration**: Modules integrate with node APIs
- **Composition**: Modules can be composed together

For implementation details, see the [bllvm-node module system documentation](../../modules/bllvm-node/docs/MODULE_SYSTEM.md).

