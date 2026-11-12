# Installing Taskhold (for agents)

Taskhold is a remote MCP server. There is nothing to clone, build or run: you add one URL to the client's MCP settings.

- Server URL: `https://taskhold.com/api/mcp` (Streamable HTTP)
- Auth: OAuth with no key. The client shows an Authenticate button or opens a browser, and the connection finishes there with no sign-up.
- Tools: `taskhold_*` (list, begin, plan, progress, block, complete and more).

## Cline

Add this to `cline_mcp_settings.json` (Cline panel > MCP Servers > Configure > Configure MCP Servers):

```json
{
  "mcpServers": {
    "taskhold": {
      "type": "streamableHttp",
      "url": "https://taskhold.com/api/mcp"
    }
  }
}
```

Keep `"type": "streamableHttp"`; without it Cline tries legacy SSE. Save, then the user clicks Authenticate on the taskhold row (Cline 4.1.7 or later).

## Other clients

- Claude Code: `claude mcp add --transport http --scope user taskhold https://taskhold.com/api/mcp`, then `/mcp` and Authenticate.
- Cursor, VS Code, Codex, Windsurf, Gemini CLI and more: https://taskhold.com/for

## After connecting

Call `taskhold_get_current`. If the account has no plan yet, the reply is a SETUP NEEDED message with a one-time link where the user starts the 7-day trial or signs in to an account they already have. Show that message to the user as written and let them open the link. Don't open it for them, and don't invent an API key.

## With an API key instead

For a machine with no browser: the user makes a setup URL in Taskhold > Settings and pastes it to you. Fetch it; it is markdown with an API key and the exact config for your client. Or add a header to the entry above:

```json
"headers": { "Authorization": "Bearer atd_sk_..." }
```

## How to use it

`skills/taskhold/SKILL.md` in this repo has the full workflow: start of session, splitting work into steps, reporting progress, asking the user when blocked, and finishing with a summary.
