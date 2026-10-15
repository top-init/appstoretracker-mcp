# App Store Tracker MCP server

**[App Store Tracker](https://www.appstoretracker.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing)** lets your AI assistant look up iOS App Store data: chart rankings, app details, reviews, keywords, ads and revenue estimates for any app in any country.

[Website](https://www.appstoretracker.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) · [MCP docs](https://www.appstoretracker.com/mcp?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) · [Get an API key](https://www.appstoretracker.com/account/api?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) · [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.appstoretracker)

| | |
|---|---|
| **Endpoint** | `https://www.appstoretracker.com/api/mcp` |
| **Transport** | Streamable HTTP (remote, hosted, nothing to install) |
| **Auth** | `Authorization: Bearer <API key>`. Create one at [appstoretracker.com/account/api](https://www.appstoretracker.com/account/api?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing) |
| **Registry name** | `com.appstoretracker/mcp` |

## What you can ask

- "What are the top 20 free Health & Fitness apps in the US right now?"
- "How has Duolingo ranked in Germany over the last 90 days?"
- "Find apps similar to Calm and estimate their monthly revenue."
- "What keywords does Notion rank for, and which ads is it running?"
- "What changed in Spotify's App Store listing recently?"

## Tools

| Tool | What it does |
|---|---|
| `search_apps` | Search iOS apps by meaning, with ratings and revenue estimates |
| `get_app_details` | Full listing: description, screenshots, ratings, rankings, revenue |
| `get_rankings` | Top apps by country and category |
| `get_ranking_history` | An app's chart positions over time |
| `get_revenue_history` | An app's revenue estimates over time |
| `get_similar_apps` | Competitors by semantic similarity |
| `get_reviews` | Recent user reviews |
| `get_timeline` | Every recorded change to a listing (version, name, price, screenshots) |
| `get_keywords` | Search terms an app ranks for, with positions |
| `get_ads` | Ad creatives an app is running, by ad library |
| `get_categories` | App Store category IDs |
| `add_to_watchlist`, `get_tracked_apps`, `get_keyword_watchlist` | Your watchlist and tracked keywords |

## Connect

**Claude Code**

```bash
claude mcp add --transport http appstoretracker https://www.appstoretracker.com/api/mcp \
  --header "Authorization: Bearer $APPSTORETRACKER_API_KEY"
```

**Any MCP client** (Claude Desktop, Cursor, Windsurf, VS Code…): use [`.mcp.json`](.mcp.json) and set `APPSTORETRACKER_API_KEY`.

```json
{
  "mcpServers": {
    "appstoretracker": {
      "type": "http",
      "url": "https://www.appstoretracker.com/api/mcp",
      "headers": { "Authorization": "Bearer ${APPSTORETRACKER_API_KEY}" }
    }
  }
}
```

## Also from the same team

- [Social Growth Engineers MCP](https://github.com/top-init/socialgrowthengineers-mcp-registry-listing): viral short-form videos, hooks and app growth playbooks
- [Shortimize MCP](https://github.com/top-init/shortimize-mcp-registry-listing): TikTok, Reels and Shorts analytics

## About this repo

| | |
|---|---|
| **What it is** | Config only: the MCP Registry entry (`server.json`) and a client config (`.mcp.json`). The server itself runs at the endpoint above. |
| **How it deploys** | Changing `server.json` does nothing until it's republished to the MCP Registry with `mcp-publisher publish`. Version 1.0.0 is live. |
| **Health check** | `curl -s "https://registry.modelcontextprotocol.io/v0/servers?search=appstoretracker"` |

The files in this repo are MIT licensed. Use of the hosted service follows the terms at [appstoretracker.com](https://www.appstoretracker.com/?utm_source=github&utm_medium=referral&utm_campaign=mcp-listing).
