# GSCmate MCP

[![Listed on HookMCP](https://hookmcp.com/badge.svg)](https://hookmcp.com)

GSCmate is a hosted remote MCP server for Google Search Console. It gives MCP-compatible AI clients read-only access to authorized properties, Search Analytics, sitemap metadata, and URL inspection through Google OAuth 2.1.

- Website: https://gscmate.com/
- MCP endpoint: https://gscmate.com/mcp
- Transport: Streamable HTTP
- Authentication: Google OAuth 2.1; each user signs in with their own Google account
- Access: Read-only

This repository contains public integration metadata and example client configuration. The hosted GSCmate service is maintained at https://gscmate.com; this repository does not contain its service source code.

## Connect a client

For a client that supports Streamable HTTP, add the endpoint `https://gscmate.com/mcp` and complete the Google sign-in flow when prompted.

For a client using the `mcp-remote` bridge, use:

```json
{
  "mcpServers": {
    "gscmate": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://gscmate.com/mcp"]
    }
  }
}
```

Gemini CLI can add the remote HTTP server with:

```sh
gemini mcp add --transport http gscmate https://gscmate.com/mcp
```

The server's Google OAuth authorization is per user. Do not put OAuth secrets, API keys, or mailbox credentials in client configuration or this repository.
