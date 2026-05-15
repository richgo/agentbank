---
title: Build a pretty A2UI banking UI with MCP apps-ext 3rd-party support
metric: ui-completeness
---

# Goal

Build a complete, polished banking UI using Google A2UI / GenUI SDK with 3rd-party extensibility via the MCP Apps extension (`modelcontextprotocol/ext-apps`).

Reference implementation: https://github.com/richgo/aibank

## Deliverables

- **Web app** (Flutter web) — beautiful banking dashboard: accounts, transactions, mortgage, credit card
- **Flutter mobile app** — same feature set, native-feeling
- **Agent backend** (FastAPI) — orchestrates bank MCP tools, returns A2UI templates
- **`mcp:AppFrame` support** — hosts 3rd-party MCP app UIs (e.g. map view for merchant transactions)
- **GenUI SDK integration** — AI-rendered UI components via the A2UI contract
- **3rd-party MCP** — `@modelcontextprotocol/server-map` (from ext-apps) for geocoded merchant locations

## Architecture

```
mcp_server/   Internal banking MCP tools (accounts, transactions, mortgage, credit card)
agent/        FastAPI orchestration (bank MCP + map MCP, returns A2UI templates)
app/          Flutter host app with GenUI + mcp:AppFrame bridge
external/     @modelcontextprotocol/server-map (starts on :3001)
dev.sh        One-command startup for all services
```

## Success metric

All 4 services start cleanly with `./dev.sh`. Flutter web renders an account dashboard with:
- Accounts list
- Transaction history
- Inline map for merchant locations (via mcp:AppFrame + server-map)

UI is polished: dark theme, card-based layout, smooth animations, proper typography.

## Target files

- `agent/`
- `app/`
- `mcp_server/`
- `dev.sh`
- `external/`
