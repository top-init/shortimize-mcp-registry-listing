# shortimize-mcp-registry-listing

## At a glance

| | |
|---|---|
| **What it is** | Config only: the MCP Registry entry (`server.json`, published as `com.shortimize/mcp`) and a client config (`.mcp.json`). No server code. |
| **Where it runs** | The MCP server lives in `top-init/shortimize-gateway` (`src/mcp/server.ts`), served at `https://api.shortimize.com/mcp`. |
| **How it deploys** | Automatic. Bump `version` in `server.json` and merge to `main` → the `publish` workflow republishes to the MCP Registry. The same version cannot be published twice. |
| **Auth for publishing** | DNS domain proof: the apex TXT record `v=MCPv1; k=ed25519; p=<public key>` (Cloudflare); the private key (hex) is the `MCP_REGISTRY_PRIVATE_KEY` secret on the `mcp-registry-publish` environment, which needs a reviewer to approve each run. |
| **How to check it's healthy** | `curl -s "https://registry.modelcontextprotocol.io/v0/servers?search=shortimize"` shows the listing. |

## Shortimize MCP server

A hosted remote MCP server for short-form video analytics: track TikTok, Instagram Reels and YouTube Shorts accounts and videos, their views, growth and performance.

- **Endpoint:** `https://api.shortimize.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** `Authorization: Bearer <API key>`
- **API docs:** https://docs.shortimize.com
- **Website:** https://www.shortimize.com

## Connect

Claude Code:

```bash
claude mcp add --transport http shortimize https://api.shortimize.com/mcp \
  --header "Authorization: Bearer $SHORTIMIZE_API_KEY"
```

Any other client: use the entry in `.mcp.json`.

## License

The files in this repo are MIT licensed. Use of the hosted service follows the terms at https://www.shortimize.com.
