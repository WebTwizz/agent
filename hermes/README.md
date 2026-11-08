# WebTwizz for Hermes Agent

Build, change and publish websites and web apps with [WebTwizz](https://webtwizz.com) from Hermes Agent: landing pages, online stores, booking sites, portfolios and web apps with sign-ins and a database. Publish to a webtwizz.app address or your own domain, undo changes, edit site data and sync with GitHub.

## Install

```bash
hermes plugins install webtwizz
```

The first WebTwizz tool call opens a browser to sign in to WebTwizz or create a free account. Nothing is configured by hand and no API key is stored in this package. The account needs a verified email address before WebTwizz can build or change anything.

## What to ask for

- "Build me a site for my bakery with a menu, opening hours and a contact form."
- "Show me WebTwizz templates for a photography portfolio."
- "Change the big heading on my bakery site to 'Fresh bread every morning'."
- "Publish my bakery site."

Builds take from a few seconds to several minutes. `get-site` shows when a change is finished. `publish-site` never publishes on its own: it returns a link that opens Publish in the WebTwizz editor, and the site goes live when you press it.

## What this package does

- **Configuration only.** It holds `plugin.json` and `mcp.json` and no code of its own. The tools are served at runtime by WebTwizz's hosted MCP server at `https://app.webtwizz.com/mcp` and are not covered by the pinned commit.
- **Network:** every tool call goes to `app.webtwizz.com` and acts on your WebTwizz account. Builds and edits use WebTwizz credits, the same as in the WebTwizz editor.
- **Sign-in:** runs the pinned `mcp-remote@0.1.49` through `npx` (Node.js and npm required). On first use it opens a browser and a local callback port, and it stores the OAuth tokens under `~/.mcp-auth`.
- **Approvals:** the package marks the server `untrusted`, so Hermes asks before every tool the server doesn't mark read-only, and refuses them in unattended runs.
- **Disconnect:** in WebTwizz, open **Settings**, then **Sessions**, and remove Hermes Agent under **Connected apps**. Deleting `~/.mcp-auth` removes the local tokens.

## Links

- [WebTwizz for AI assistants](https://webtwizz.com/mcp)
- [Docs](https://docs.webtwizz.com/ai-assistants)
- [Privacy policy](https://webtwizz.com/privacy#ai-assistants)
- Support: support@webtwizz.com
