# Context Engine

The Context Engine is an open-source platform for deterministic, token-aware context selection. It helps AI agents and LLM applications retrieve exactly the right context within budget constraints.

## Architecture

```
context-engine (you are here)
├── context-core        — Core library: scoring, selection, caching
├── context-cli         — CLI: build, resolve, inspect commands
├── context-mcp-server  — MCP server: JSON-RPC 2.0 stdio transport
├── context-compat      — Compatibility test harness
├── context-specs       — Protocol specifications and ADRs
├── context-docs        — Documentation site
├── context-examples    — Example integrations
├── context-sdk-js      — JavaScript/TypeScript SDK (planned)
└── context-sdk-python  — Python SDK (planned)
```

## Quick Start

```bash
# Build the CLI
git clone https://github.com/contextenginehq/context-cli.git
cd context-cli
cargo build --release

# Build a context cache from your documents
./target/release/context build --sources ./docs --cache ./my-cache

# Resolve context for a query within a token budget
./target/release/context resolve --cache ./my-cache --query "deployment" --budget 4000
```

## MCP Integration

The Context Engine exposes its capabilities through the [Model Context Protocol](https://modelcontextprotocol.io/), making it compatible with any MCP-aware AI agent.

```bash
# Start the MCP server
git clone https://github.com/contextenginehq/context-mcp-server.git
cd context-mcp-server
cargo build --release
./target/release/mcp-context-server --cache-root ./caches
```

## Key Properties

- **Deterministic**: Same input always produces identical output, byte-for-byte
- **Token-aware**: Respects token budgets for LLM context windows
- **Versioned caches**: Backward-compatible cache format with version tracking
- **Frozen contracts**: v0 output schemas, error codes, and behaviors are locked

## Repositories

| Repository | Description | Status |
|-----------|-------------|--------|
| [context-core](https://github.com/contextenginehq/context-core) | Core scoring and selection library | v0.1.0 |
| [context-cli](https://github.com/contextenginehq/context-cli) | Command-line interface | v0.1.0 |
| [context-mcp-server](https://github.com/contextenginehq/context-mcp-server) | MCP server | v0.1.0 |
| [context-compat](https://github.com/contextenginehq/context-compat) | Compatibility test harness | v0.1.0 |
| [context-specs](https://github.com/contextenginehq/context-specs) | Protocol specifications | v0 |
| [context-docs](https://github.com/contextenginehq/context-docs) | Documentation | Active |
| [context-examples](https://github.com/contextenginehq/context-examples) | Example integrations | Active |
| [context-sdk-js](https://github.com/contextenginehq/context-sdk-js) | JavaScript SDK | Planned |
| [context-sdk-python](https://github.com/contextenginehq/context-sdk-python) | Python SDK | Planned |

## License

Apache-2.0

---

"Context Engine" is a trademark of Context Engine Contributors. The software is open source under the [Apache License 2.0](LICENSE). The trademark is not licensed for use by third parties to market competing products or services without prior written permission.
