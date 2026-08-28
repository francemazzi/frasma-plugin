# Cursor Marketplace and directory submit copy

Use this when submitting the public GitHub repo. Do not click **Submit Application** until `main` is public and the publisher accepts the [Publisher Terms](https://cursor.com/marketplace-publisher-terms).

## cursor.com/marketplace/publish

- **Become a plugin publisher** + first plugin repo (single form).
- **GitHub repository:** `https://github.com/francemazzi/frasma-plugin`
- **Handle:** `frasma`
- **Website:** `https://frasma.org`
- **Logo:** raw GitHub URL of `assets/logo.jpeg` after push, or the relative path in the repo.
- **License:** MIT (permissive; not GPL).
- **Publisher type:** Individual or organization as appropriate.

### Listing blurb

Frasma Kanban as the source of truth. Install the plugin, sign in with your Frasma account, and Cursor (desktop and Cloud Agents) shares the same backlog as the web app over `https://api.frasma.org/mcp`.

### Review notes for the form / email

- Remote Streamable HTTP MCP only; no stdio, no binaries, no secrets in the repo.
- Auth is OAuth 2.1 with Dynamic Client Registration and PKCE. Users never paste API keys.
- Production resource: `https://api.frasma.org/mcp`.
- Privacy: tools run as the signed-in Frasma user with existing RBAC.

Contact if the form stalls: marketplace-publishing@cursor.com

## cursor.directory (immediate, unofficial)

1. Sign in at [cursor.directory/plugins/new](https://cursor.directory/plugins/new) (GitHub or Google).
2. Paste the public repo URL. Auto-detects `.mcp.json`, skills, and rules.
3. Optional MCP-only listing: [cursor.directory/mcp/new](https://cursor.directory/mcp/new) with the deeplink from the README.

## Grok bot

No public catalog form. Users add **Custom** connector `https://api.frasma.org/mcp` at [grok.com/connectors](https://grok.com/connectors). Official tile requires xAI partnership, not this repo.
