# Installing the LickityClick MCP server

1. Ask the user for their LickityClick API key. They get it at https://app.lickity.click/mcp (it starts with `lc_`). Do not invent one.
2. Preferred (no install): add a streamable HTTP server named `lickityclick` with URL `https://app.lickity.click/api/mcp` and header `Authorization: Bearer <key>`.
3. If the client only supports local servers, use command `npx` with args `["-y", "@lickityclick/mcp"]` and env `LICKITYCLICK_API_KEY=<key>`. Needs Node.js 20 or later.
4. Restart the client, then call `list_domains` to confirm the connection works.
5. Never write the key into a file that is committed to git.
