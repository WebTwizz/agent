# WebTwizz

WebTwizz builds real websites and web apps from a description, hosts them and publishes them. This extension connects Gemini CLI to the user's WebTwizz account over MCP.

## Signing in

The server is at `https://app.webtwizz.com/mcp`. It answers an unauthenticated call with a 401 that points at its OAuth metadata, so Gemini CLI opens a browser the first time a tool runs. The user signs in to WebTwizz or creates a free account. No API key is stored in this extension. The account needs a verified email address before WebTwizz can build or change anything.

## How to work with it

- `create-site` and `edit-site` start the work and return at once. The work is done only when a result says **Finished**; until then, check with `get-site` and don't describe the result.
- When WebTwizz asks a question, ask the user and pass the answer with `edit-site`. When it waits for an OK, ask the user and pass the answer to `confirm-action`. Never approve it yourself.
- `screenshot-site` lets you see a page before telling the user what changed.
- `publish-site` never publishes on its own. Gemini CLI can't show the WebTwizz card, so `publish-site` returns a link that opens Publish in the WebTwizz editor. Give the user that link and tell them to press **Publish**, and don't say the site is live until they have.
- Every `site_id` also takes the site's name.
- Secret keys are never typed into the chat. `set-env-variable` returns the WebTwizz page where the user pastes them.
- Builds and edits use WebTwizz credits. When they run out, WebTwizz says so and nothing changes.

The full guide is in [`skills/webtwizz/SKILL.md`](./skills/webtwizz/SKILL.md).
