<!-- 2026-05-25 -->
# MCP Configuration Guide

> **STATUS: TODO** — This is a placeholder for future content.

## What Will Go Here

A practical guide for configuring and using Model Context Protocol (MCP) servers with Kiro IDE and Claude Code. MCP lets AI agents call external services (Google Sheets, Slack, databases, internal APIs) as tools during development.

---

## Topics to Cover

### 1. What Is MCP and Why It Matters
- TODO: Explain MCP as a protocol for AI ↔ service communication
- TODO: When to use MCP vs. direct API calls
- TODO: The shift from "AI reads docs" to "AI calls services directly"

### 2. Configuring MCP Servers in Kiro / Claude Code
- TODO: File locations (`.kiro/settings/mcp.json`, `~/.kiro/settings/mcp.json`)
- TODO: Config format and precedence (user < workspace)
- TODO: Using `uvx` to run servers without installation
- TODO: Auto-approve lists for trusted tools
- TODO: Enabling/disabling servers

### 3. Making Your Own Service Callable via MCP
- TODO: When to build a custom MCP server
- TODO: Minimal server implementation (Python with FastMCP)
- TODO: Exposing CRUD operations as tools
- TODO: Input/output schema design
- TODO: Error handling patterns

### 4. Access Control & Security
- TODO: What data flows through MCP (prompts, tool calls, responses)
- TODO: Scoping permissions (read-only vs. read-write)
- TODO: Secrets management (env vars, not hardcoded)
- TODO: Audit logging for MCP tool calls

### 5. Common MCP Patterns
- TODO: Google Sheets (read/write spreadsheet data)
- TODO: Slack (send messages, read channels)
- TODO: Database (query, but never mutate without approval)
- TODO: Internal REST APIs (CRUD with auth)
- TODO: Documentation search (fetch and summarize)

### 6. Troubleshooting
- TODO: Server won't connect (uvx not installed, path issues)
- TODO: Tools not appearing (config precedence, disabled flag)
- TODO: Timeout issues (long-running operations)
- TODO: Permission errors (missing env vars)

---

## References

- [Kiro MCP Documentation](https://kiro.dev/docs/mcp/)
- [Model Context Protocol Spec](https://modelcontextprotocol.io/)
- [FastMCP (Python)](https://github.com/jlowin/fastmcp)

---

*This file will be expanded with full content in a future update. For now, configure MCP servers using the Kiro command palette → "MCP" or by editing `.kiro/settings/mcp.json` directly.*
