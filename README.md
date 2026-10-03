# App Store Tracker MCP server

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
