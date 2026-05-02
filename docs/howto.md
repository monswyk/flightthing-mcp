# How to call tools (cURL)

These examples target the MCP endpoint for **The Flight Thing** at `flightthing.com`.

## 1) List available tools
```bash
curl -X POST "https://flightthing.com/api/mcp" \
  -H "Content-Type: application/json" \
  -H "x-mcp-token: YOUR_TOKEN_HERE" \
  --data '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'
```

## 2) Call a tool
Pick a tool name and required fields from the `tools/list` output.

Example: `list_flights`
```bash
curl -X POST "https://flightthing.com/api/mcp" \
  -H "Content-Type: application/json" \
  -H "x-mcp-token: YOUR_TOKEN_HERE" \
  --data '{"jsonrpc":"2.0","id":2,"method":"list_flights","params":{"email":"user@example.com","filters":{"limit":10}}}'
```

Example: `create_flight` (minimal)
```bash
curl -X POST "https://flightthing.com/api/mcp" \
  -H "Content-Type: application/json" \
  -H "x-mcp-token: YOUR_TOKEN_HERE" \
  --data '{"jsonrpc":"2.0","id":3,"method":"create_flight","params":{"email":"user@example.com","flight":{"flight_date":"2026-02-05","flight_number":"LX65"}}}'
```

Notes:
- Required fields are listed in each tool’s `inputSchema`.
- Keep your token private and never commit it to git.
