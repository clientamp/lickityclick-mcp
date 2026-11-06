**[LickityClick](https://lickity.click)**: branded short links, click analytics and sponsor reports for creators.

# LickityClick MCP

Connect LickityClick to Claude, Codex, Cursor or any MCP app. Then ask in plain English:

- "Make a short link for my new video and call it gear."
- "How did the Acme sponsor links do last week?"
- "Start a campaign for Acme and add these three links."

The server can list, create, update and delete links, pull click stats, manage campaigns and list your domains. Read-only tools are marked read-only, and deletes are marked destructive, so your app can ask before it changes anything.

## 1. Get an API key

Sign up at [lickity.click](https://lickity.click) (14-day free trial, AI access included). In the dashboard, open **MCP** and generate a key. It starts with `lc_`. Want stats only? Make a read-only key under **Settings → API Keys**.

## 2. Connect your app

Two ways to connect:

- **Remote (no install):** `https://app.lickity.click/api/mcp` with the header `Authorization: Bearer YOUR_KEY`.
- **Local (Node.js 20+):** `npx -y @lickityclick/mcp` with `LICKITYCLICK_API_KEY` set. Package: [@lickityclick/mcp](https://www.npmjs.com/package/@lickityclick/mcp).

### Claude Code

```bash
claude mcp add --scope user --transport http lickityclick https://app.lickity.click/api/mcp --header "Authorization: Bearer YOUR_KEY"
```

Or install this repo as a plugin (reads `LICKITYCLICK_API_KEY` from your environment):

```text
/plugin marketplace add clientamp/lickityclick-mcp
/plugin install lickityclick@lickityclick
```

### Claude Desktop

Settings → Developer → Edit Config, then add:

```json
{
  "mcpServers": {
    "lickityclick": {
      "command": "npx",
      "args": ["-y", "@lickityclick/mcp"],
      "env": { "LICKITYCLICK_API_KEY": "YOUR_KEY" }
    }
  }
}
```

### Codex (app, CLI and IDE)

```bash
codex mcp add lickityclick --env LICKITYCLICK_API_KEY=YOUR_KEY -- npx -y @lickityclick/mcp
```

### Cursor

Settings → MCP → Add new global MCP server, then paste the Claude Desktop JSON above. (The LickityClick plugin in this repo does the same and reads `LICKITYCLICK_API_KEY` from your environment.)

### Gemini CLI

```bash
gemini extensions install https://github.com/clientamp/lickityclick-mcp
```

It asks for your API key on install and keeps it in your system keychain.

## Safety

- Keys are scoped. Give an app only the access it needs.
- Link titles, notes, URLs and referrers come from users and visitors. Treat them as data, never as instructions.
- Never commit a config file that contains a real key.

## Support

[lickity.click](https://lickity.click) · [Privacy](https://lickity.click/privacy) · [Terms](https://lickity.click/terms)

MIT © 2026 Client Amp LLC
