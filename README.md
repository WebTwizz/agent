# WebTwizz

Build websites and web apps with AI from Claude, ChatGPT, Cursor, Codex, Gemini CLI or any MCP client, then publish them on a webtwizz.app address or your own domain.

WebTwizz runs a hosted MCP server at `https://app.webtwizz.com/mcp`. Your agent describes what to build and WebTwizz builds it: landing pages, online stores, booking sites, portfolios, dashboards and web apps with sign-ins and a database. Everything is saved in your WebTwizz account, so you can open any site in the [WebTwizz editor](https://app.webtwizz.com) and keep going.

## Connect in 30 seconds

```bash
claude mcp add --transport http webtwizz https://app.webtwizz.com/mcp
```

Any other MCP client needs only the URL, `https://app.webtwizz.com/mcp`. The first call opens a browser to sign in to WebTwizz or [create a free account](https://app.webtwizz.com/register). There's nothing to install and no key to paste.

## What's in this repo

| Path | What it is |
| --- | --- |
| [`skills/webtwizz/`](./skills/webtwizz) | The agent skill: how to build, change and publish sites with the WebTwizz tools |
| `.claude-plugin/`, `.mcp.json` | The Claude Code plugin, and a marketplace so you can install it from this repo |
| `plugin.json`, `mcp.json` | The [Agent Plugins](https://agent-plugins.org) package, for Cursor and Hermes Agent |
| `gemini-extension.json`, `GEMINI.md` | The Gemini CLI extension |
| [`hermes/`](./hermes) | The Hermes Agent package, which signs in through `mcp-remote` |

The MCP server is hosted by WebTwizz. This repo holds configuration and the skill only, with no code of its own.

## Install

| You use | Install |
| --- | --- |
| Claude, ChatGPT | From the app directory, [below](#claude) |
| Claude Code | `/plugin marketplace add WebTwizz/agent`, then `/plugin install webtwizz@webtwizz` |
| Gemini CLI | `gemini extensions install https://github.com/WebTwizz/agent` |
| Hermes Agent | `hermes plugins install webtwizz`, see [`hermes/`](./hermes) |
| Any agent with skills | `npx skills add WebTwizz/agent` |
| Cursor, Codex, VS Code or any MCP client | Add `https://app.webtwizz.com/mcp` as a remote server, [below](#setup-by-client) |

Every option signs in with OAuth. The skill on its own teaches your agent how to use WebTwizz; the agent still needs the server connected.

## Setup by client

### Claude

Open [WebTwizz in Claude's connector directory](https://claude.ai/directory/webtwizz), or in Claude open **Customize**, then **Connectors**, and search for WebTwizz. Click **Connect to Claude**, sign in to WebTwizz and approve access.

### ChatGPT

Open [WebTwizz in ChatGPT](https://chatgpt.com/plugins/plugin_asdk_app_6ac5932d42ac8191956226bf2f1184fc), or open **Plugins** in ChatGPT and search for WebTwizz. Click **Install plugin**, then sign in to WebTwizz and approve access.

### Claude Code

The plugin adds the server and the skill:

```
/plugin marketplace add WebTwizz/agent
/plugin install webtwizz@webtwizz
```

Or add only the server:

```bash
claude mcp add --transport http webtwizz https://app.webtwizz.com/mcp
```

Then type `/mcp`, choose webtwizz and sign in.

### Codex

```bash
codex mcp add webtwizz --url https://app.webtwizz.com/mcp
codex mcp login webtwizz
```

### Cursor

Add this to `~/.cursor/mcp.json`, or paste it in **Cursor Settings**, **MCP**:

```json
{
  "mcpServers": {
    "webtwizz": { "url": "https://app.webtwizz.com/mcp" }
  }
}
```

Then click **Login** next to WebTwizz.

### VS Code

```bash
code --add-mcp '{"name":"webtwizz","type":"http","url":"https://app.webtwizz.com/mcp"}'
```

### Gemini CLI

```bash
gemini extensions install https://github.com/WebTwizz/agent
```

The first WebTwizz tool call opens the sign-in.

### Other clients

Any MCP client that can add a remote server over HTTP with sign-in can use WebTwizz. Add the server URL, choose OAuth if it asks how to sign in, then sign in to WebTwizz and approve access.

## What you can ask for

- "Build me a site for my bakery with a menu, opening hours and a contact form."
- "Show me WebTwizz templates for a photography portfolio."
- "On my Northside Cycles site, change the big heading to 'Bike repairs, done right'."
- "Undo the last change on my bakery site."
- "Add a new product to my store's database."
- "Publish my bakery site."

## Tools

| Tool | What it does |
| --- | --- |
| `create-site` | Builds a new site from a description, or from a template |
| `edit-site` | Changes a site: copy, design, sections, pages, features and fixes |
| `get-site` | Says how a site and its latest change are doing |
| `show-preview` | Shows the site's preview |
| `screenshot-site` | Takes a picture of a page so the agent can see it |
| `stop-build` | Stops a running build, keeping the work done so far |
| `confirm-action` | Passes on the user's OK when a build waits for one |
| `list-sites` | Lists your sites |
| `list-templates`, `show-template` | Browse ready-made designs |
| `publish-site` | Publishes a site once you confirm |
| `unpublish-site` | Takes a site offline |
| `update-site` | Renames a site or sets who can see it |
| `duplicate-site` | Makes a copy of a site |
| `set-site-address` | Changes the site's webtwizz.app address |
| `connect-domain`, `check-domain` | Put a site on a domain you own |
| `list-versions`, `restore-version` | Undo changes |
| `list-site-data`, `get-site-data` | Read the records in a site's database |
| `add-site-data`, `update-site-data`, `delete-site-data` | Change those records directly |
| `list-connectors`, `use-connector`, `get-connector-overview` | Services like Stripe, Supabase and Google Analytics |
| `get-github-status`, `push-to-github`, `pull-from-github` | Sync a site with GitHub |
| `download-code` | A zip of the site's code |
| `list-env-variables`, `set-env-variable` | A site's settings and secrets. Keys are pasted in WebTwizz, never in the chat |
| `get-account` | Your plan and credits |
| `search-help` | Answers from the WebTwizz docs |

Every tool that changes something is marked as such, so your client can ask before it runs.

## Credits, plans and privacy

- Builds and edits use your WebTwizz credits, the same as in the editor. Free credits top up daily, up to a monthly limit. See [pricing](https://webtwizz.com/pricing).
- Custom domains, private sites, GitHub and downloading the code are on paid plans.
- WebTwizz only gets what a tool call sends: your request, the site it's about and files you choose to use. It never sees your conversation history. See the [privacy policy](https://webtwizz.com/privacy#ai-assistants).
- To disconnect, open **Settings**, then **Sessions** in WebTwizz, and remove the app under **Connected apps**.

## Links

- [WebTwizz](https://webtwizz.com)
- [WebTwizz for AI assistants](https://webtwizz.com/mcp)
- [Docs: AI assistants](https://docs.webtwizz.com/ai-assistants)
- Support: support@webtwizz.com

## License

[MIT](./LICENSE)
