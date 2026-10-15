# Shortimize MCP server

**[Shortimize](https://www.shortimize.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing)** lets your AI assistant track and analyze short-form video: TikTok, Instagram Reels and YouTube Shorts accounts and videos, their views, growth and history, organized into collections.

[Website](https://www.shortimize.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) · [Pricing](https://www.shortimize.com/pricing?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) · [API docs](https://docs.shortimize.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) · [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.shortimize)

| | |
|---|---|
| **Endpoint** | `https://api.shortimize.com/mcp` |
| **Transport** | Streamable HTTP (remote, hosted, nothing to install) |
| **Auth** | `Authorization: Bearer <API key>`. Create one in [Shortimize](https://www.shortimize.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) under Settings → API & Automation |
| **Registry name** | `com.shortimize/mcp` |

## What you can ask

- "Start tracking these 20 TikTok creators and tell me who grew fastest this week."
- "Which of our tracked videos passed 1M views in the last 7 days?"
- "Show the view history of this Reel and compare it to the account's average."
- "Put every video about our launch into a collection called 'Launch week'."
- "How many accounts and videos is our organisation tracking?"

## Tools

| Area | Tools |
|---|---|
| Accounts | `get_all_accounts`, `get_account`, `get_account_history`, `get_videos_linked_to_account`, `track_account`, `bulk_track_accounts`, `stop_tracking_account`, `bulk_stop_tracking_accounts`, `refresh_account_data`, `total_accounts` |
| Videos | `get_all_videos`, `get_video`, `get_video_history`, `track_video`, `bulk_track_videos`, `stop_tracking_video`, `bulk_stop_tracking_videos`, `refresh_video_data`, `total_videos` |
| Collections | `get_all_collections`, `get_collection`, `create_collection`, `update_collection`, `delete_collection`, `get_collection_videos`, `add_videos_to_collection`, `remove_videos_from_collection`, `get_collection_accounts`, `add_accounts_to_collection`, `remove_accounts_from_collection` |
| Organisation | `get_organisation_history`, `authenticate` |

Bulk tools handle up to 500 accounts or videos per call. Full API reference: [docs.shortimize.com](https://docs.shortimize.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing).

## Connect

**Claude Code**

```bash
claude mcp add --transport http shortimize https://api.shortimize.com/mcp \
  --header "Authorization: Bearer $SHORTIMIZE_API_KEY"
```

**Any MCP client** (Claude Desktop, Cursor, Windsurf, VS Code…): use [`.mcp.json`](.mcp.json) and set `SHORTIMIZE_API_KEY`.

```json
{
  "mcpServers": {
    "shortimize": {
      "type": "http",
      "url": "https://api.shortimize.com/mcp",
      "headers": { "Authorization": "Bearer ${SHORTIMIZE_API_KEY}" }
    }
  }
}
```

## Find it in MCP directories

- [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.shortimize)
- [Smithery](https://smithery.ai/server/topinit/shortimize)
- [MCP.so](https://mcp.so/servers/shortimize)
- [AllMCPs](https://allmcps.com/mcp/shortimize)
- [MCP Repository](https://mcprepository.com/top-init/shortimize-mcp-registry-listing)
- [AI Indigo](https://aiindigo.com/tool/shortimize)

## Also from the same team

- [App Store Tracker MCP](https://github.com/top-init/appstoretracker-mcp-registry-listing): iOS rankings, reviews, keywords and revenue estimates
- [Social Growth Engineers MCP](https://github.com/top-init/socialgrowthengineers-mcp-registry-listing): viral short-form videos, hooks and app growth playbooks

## About this repo

| | |
|---|---|
| **What it is** | Config only: the MCP Registry entry (`server.json`) and a client config (`.mcp.json`). The server itself runs at the endpoint above. |
| **How it deploys** | Bump `version` in `server.json` and merge to `main`. The `publish` workflow republishes to the MCP Registry after a maintainer approves the run. |
| **Ownership proof** | DNS TXT record on shortimize.com. The signing key is a GitHub environment secret. |
| **Health check** | `curl -s "https://registry.modelcontextprotocol.io/v0/servers?search=shortimize"` |

The files in this repo are MIT licensed. Use of the hosted service follows the terms at [shortimize.com](https://www.shortimize.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing).
