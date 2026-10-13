# appstoretracker-mcp-registry-listing

## At a glance

| | |
|---|---|
| **What it is** | Config only: the MCP Registry entry (`server.json`, published as `com.appstoretracker/mcp`) and a client config (`.mcp.json`). No server code. |
| **Where it runs** | The MCP server itself is `src/app/api/mcp/route.ts` in `appstoretracker-website`, served by Vercel at `https://www.appstoretracker.com/api/mcp`. |
| **Where data is saved** | Nothing here. The endpoint reads the self-hosted Supabase `server.appstoretracker.com` (box 77.42.77.238, Beszel `appstoretracker-database-and-cron-jobs`). API keys live in its `mcp_api_keys` table and usage in `mcp_api_usage`. |
| **How it deploys** | Manual. Changing `server.json` does nothing until it is republished to the MCP Registry with `mcp-publisher publish` (needs the `com.appstoretracker` namespace login). Version 1.0.0 is live in the registry. Server code deploys with `appstoretracker-website` (merge to `master` → Vercel). |
| **How to check it's healthy** | `curl -s "https://registry.modelcontextprotocol.io/v0/servers?search=appstoretracker"` shows the listing. Call the endpoint with a Bearer key to test the server. |

## Related repos (all `top-init`)

| repo | role |
|---|---|
| [appstoretracker-website](https://github.com/top-init/appstoretracker-website) | hosts the MCP server at `/api/mcp` |
| [appstoretracker-cron-jobs](https://github.com/top-init/appstoretracker-cron-jobs) | Node cron jobs: app enrichment, manual-app import, tweet bot |
| [appstoretracker-ads-and-rankings-collector](https://github.com/top-init/appstoretracker-ads-and-rankings-collector) | Python collector: ads, keyword ranks, chart ranks |
| [appstoretracker-chrome-extension](https://github.com/top-init/appstoretracker-chrome-extension) | Chrome extension (unreleased) |
| [appstoretracker-mcp-registry-listing](https://github.com/top-init/appstoretracker-mcp-registry-listing) | this repo |

## App Store Tracker MCP server

App Store Tracker is a hosted remote MCP server for iOS App Store data.
It gives an AI assistant chart rankings, app details, reviews, keywords and revenue estimates.

- **Endpoint:** `https://www.appstoretracker.com/api/mcp`
- **Transport:** Streamable HTTP
- **Auth:** `Authorization: Bearer <API key>`
- **Docs:** https://www.appstoretracker.com/mcp
- **Get an API key:** https://www.appstoretracker.com/account/api

This repo holds no server code. The server runs at the endpoint above.
It holds the config files that MCP clients and directories read.

## Files

| file | what it is |
|---|---|
| `.mcp.json` | Remote HTTP server entry. Set `APPSTORETRACKER_API_KEY` in your environment. |
| `server.json` | The entry published to the MCP Registry as `com.appstoretracker/mcp`. |

## Connect

Claude Code:

```bash
claude mcp add --transport http appstoretracker https://www.appstoretracker.com/api/mcp \
  --header "Authorization: Bearer $APPSTORETRACKER_API_KEY"
```

Any other client: use the entry in `.mcp.json`.

## License

The files in this repo are MIT licensed. Use of the hosted service follows the terms at
https://www.appstoretracker.com.
