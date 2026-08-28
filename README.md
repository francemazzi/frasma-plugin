# Frasma

Clients talk. You ship. Same board.

[Frasma](https://frasma.org) is for freelancers and software teams with clients. Clients message the chat with bugs, requests, and feedback on what to improve — it lands on the Kanban, not in a lost thread. This plugin puts that live board in Cursor, Cloud Agents, Grok Build, Claude, ChatGPT, and the Grok bot, so the agent works the same cards the customer already sees.

The server URL is always production HTTPS:

```text
https://api.frasma.org/mcp
```

Sign in with your Frasma account in the browser (OAuth 2.1). Local `localhost` is only for people developing the Frasma API, not for this plugin.

## Cursor

### Marketplace (after listing)

Install **Frasma** from the [Cursor Marketplace](https://cursor.com/marketplace), then **Connect** and sign in.

### One-click deeplink

[Add Frasma to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=frasma&config=eyJ1cmwiOiJodHRwczovL2FwaS5mcmFzbWEub3JnL21jcCJ9)

### `mcp.json`

```json
{
  "mcpServers": {
    "frasma": {
      "url": "https://api.frasma.org/mcp"
    }
  }
}
```

Open **Customize**, find **frasma**, click **Connect**, and complete the Frasma login. Desktop and [Cloud Agents](https://cursor.com/agents) each store their own OAuth tokens; sign in on both surfaces if you use both.

Team admins can add the same URL under **Dashboard → Integrations & MCP** so Cloud Agents share the server; each person still authenticates as themselves.

## Grok bot

There is no self-serve catalog tile yet. Add a custom connector:

1. Open [grok.com/connectors](https://grok.com/connectors).
2. **New Connector → Custom**.
3. URL: `https://api.frasma.org/mcp`.
4. Sign in with Frasma when the browser opens.

## Grok Build

After this plugin is listed in the [Grok Build marketplace](https://github.com/xai-org/plugin-marketplace):

```bash
grok plugin install frasma --trust
```

Or browse `/marketplace` inside Grok Build.

## Claude

Add a remote connector with `https://api.frasma.org/mcp`. Claude discovers OAuth from the well-known endpoints and registers with DCR.

## ChatGPT (Developer Mode)

1. Settings → Connectors → add connector.
2. URL: `https://api.frasma.org/mcp`.
3. Sign in with Frasma email and password, then allow access.

## What the agent gets

Tools (as the signed-in user, with RBAC and optimistic locking):

- `list_projects`, `get_project`, `get_project_workboard`
- `list_tasks`, `get_task`, `list_task_conversations`
- `search_project_knowledge`
- `create_task`, `update_task`, `move_task`

The plugin also ships:

- **Skill** `frasma-kanban` — when to read the board, when not to create a card, how to patch with `expectedVersion`
- **Rule** — nudge to check Frasma on planned delivery and reported bugs

## Cursor Marketplace listing (submit)

Publisher form: [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish)

| Field | Value |
| --- | --- |
| Plugin name | `frasma` |
| Handle | `frasma` |
| Repository | `https://github.com/francemazzi/frasma-plugin` |
| License | MIT |
| Homepage | `https://frasma.org` |
| Logo | `assets/logo.jpeg` in this repo |
| Short description | Clients talk. You ship. Same board. For freelancers and software teams with clients: they report issues and feedback in chat; you and the Cursor agent work the same Frasma Kanban. |

Community listing (no Cursor review): paste this repo URL at [cursor.directory/plugins/new](https://cursor.directory/plugins/new).

## Local plugin development

```bash
ln -s /path/to/frasma-plugin ~/.cursor/plugins/local/frasma
```

Reload the Cursor window. **Customize** should show the Frasma MCP, skill, and rule. Do not point this plugin at `http://localhost:3000/mcp`.

## License

MIT. The Frasma API and web app are separate products and are not included in this repository.
