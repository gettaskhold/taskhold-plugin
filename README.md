# Taskhold

**A task list you share with your coding agents.** You add and order tasks in the web app. Claude Code, Cursor, Codex, Windsurf or any MCP client reads and updates the same list: picks up the next task, adds notes as it goes, blocks with a question when it needs you, and completes with a summary. Every change is marked as made by you or by an agent.

- Website: https://taskhold.com
- MCP server: `https://taskhold.com/api/mcp` (Streamable HTTP, `Authorization: Bearer atd_sk_...`)
- Agent Skill: [`skills/taskhold/SKILL.md`](skills/taskhold/SKILL.md)
- Official MCP Registry: `com.taskhold/taskhold`

This repository holds the agent skill and the MCP config. The Taskhold service is hosted; its code is not here.

## Install

The easy way: in Taskhold, open Settings, make a setup URL, paste it into your agent and say "set this up". It returns a new API key and the exact config for your client.

| Agent | How |
|---|---|
| Claude Code | `claude mcp add --transport http --scope user taskhold https://taskhold.com/api/mcp --header "Authorization: Bearer <your atd_sk_ key>"` |
| Claude Code plugin (skill + server) | `/plugin marketplace add taskhold-com/taskhold-plugin`, then `/plugin install taskhold@taskhold` and paste your key when asked |
| Skill only (any agent that reads skills) | `npx skills add taskhold-com/taskhold-plugin` |
| Cursor, Windsurf, Codex, VS Code, Gemini CLI | Config generator: https://taskhold.com/tools/mcp-config |

Per-agent guides: https://taskhold.com/for/claude-code, /for/cursor, /for/codex, /for/windsurf.

## What your agent can do

`taskhold_get_current`, `taskhold_list`, `taskhold_get`, `taskhold_search`, `taskhold_create`, `taskhold_create_from_todo`, `taskhold_start`, `taskhold_complete`, `taskhold_block`, `taskhold_unblock`, `taskhold_add_note`, `taskhold_update`, `taskhold_set_priority`, `taskhold_list_projects`, `taskhold_list_labels`, `taskhold_get_summary`.

## Pricing

One plan: $12 a month or $120 a year per person, every agent you run included. 7-day trial with a card up front; cancel before it ends and nothing is charged. Details: https://taskhold.com/#pricing

## Support

hello@greatwork.company. Taskhold is made by Great Work LLC.

## License

The skill and the files in this repository are MIT licensed. The Taskhold service itself is hosted and is not open source.
