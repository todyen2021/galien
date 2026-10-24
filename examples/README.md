# Connect examples

Copy-paste configs for connecting your own AI assistant to Galien, fandaburg's
agent access. Replace `fbag_YOUR_KEY` with your personal agent key from your
fandaburg profile. Leave the `Authorization` header out entirely for read-only
use — reads need no key.

Server, for every client below:

- URL: `https://fandaburg.com/mcp`
- Transport: Streamable HTTP (JSON-RPC 2.0)

## Claude Code

```bash
claude mcp add --transport http galien https://fandaburg.com/mcp --header "Authorization: Bearer fbag_YOUR_KEY"
```

## Claude Desktop

Add to `claude_desktop_config.json` — see [claude-desktop.json](claude-desktop.json):

```json
{
  "mcpServers": {
    "galien": {
      "url": "https://fandaburg.com/mcp",
      "headers": { "Authorization": "Bearer fbag_YOUR_KEY" }
    }
  }
}
```

## Cursor

Add to `~/.cursor/mcp.json` (or the project's `.cursor/mcp.json`) — see
[cursor.json](cursor.json). The format is the same as Claude Desktop's above.

## Any other MCP client

Use the generic shape in [generic-mcp.json](generic-mcp.json): a remote server
entry named `galien`, the URL above, and the bearer header with your key.
Clients that cannot send custom headers can still connect read-only — just
omit the header.
