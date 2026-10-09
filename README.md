# Taskhold

Taskhold is a task list you share with your coding agents, through a remote MCP server and an Agent Skill. You add and order tasks in the web app; Claude Code, Cursor or Codex picks up the next one, adds notes, blocks with a question when it needs you, and completes it with a summary. $12 a month per person.

**Works with:** Claude Code, Cursor, Codex, Windsurf, VS Code Copilot, Gemini CLI, Cline, OpenCode and any MCP client. Every change is marked as made by you or by an agent.

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
| Claude Code plugin (skill + server) | `/plugin marketplace add gettaskhold/taskhold-plugin`, then `/plugin install taskhold@taskhold` and paste your key when asked |
| Skill only (any agent that reads skills) | `npx skills add gettaskhold/taskhold-plugin` |
| Cursor, Windsurf, Codex, VS Code, Gemini CLI | Config generator: https://taskhold.com/tools/mcp-config |

Per-agent guides: https://taskhold.com/for/claude-code, /for/cursor, /for/codex, /for/windsurf.

## Install the skill in any agent

[![skills.sh](https://img.shields.io/badge/skills.sh-taskhold-111111?style=flat-square)](https://skills.sh/gettaskhold/taskhold-plugin/taskhold)

```shell
npx skills add gettaskhold/taskhold-plugin        # this project (asks which agents)
npx skills add gettaskhold/taskhold-plugin -g     # user-level, every project
```

Where the skill lands (to install by hand, copy `skills/taskhold/` there):

| Agent | Project folder | User folder (`-g`) |
|---|---|---|
| Claude Code | `.claude/skills/taskhold/` | `~/.claude/skills/taskhold/` |
| Codex | `.agents/skills/taskhold/` | `~/.codex/skills/taskhold/` |
| Cursor | `.agents/skills/taskhold/` | `~/.cursor/skills/taskhold/` |
| GitHub Copilot | `.agents/skills/taskhold/` | `~/.copilot/skills/taskhold/` |
| Gemini CLI | `.agents/skills/taskhold/` | `~/.gemini/skills/taskhold/` |
| OpenCode | `.agents/skills/taskhold/` | `~/.config/opencode/skills/taskhold/` |
| Cline | `.agents/skills/taskhold/` | `~/.agents/skills/taskhold/` |
| Windsurf | `.windsurf/skills/taskhold/` | `~/.codeium/windsurf/skills/taskhold/` |
| Goose | `.goose/skills/taskhold/` | `~/.config/goose/skills/taskhold/` |
| OpenClaw | `skills/taskhold/` | `~/.openclaw/skills/taskhold/` |

The skill tells your agent when and how to use Taskhold; the MCP server does the work, so connect that too (see Install above).

## What your agent can do

`taskhold_get_current`, `taskhold_list`, `taskhold_get`, `taskhold_search`, `taskhold_create`, `taskhold_create_from_todo`, `taskhold_start`, `taskhold_complete`, `taskhold_block`, `taskhold_unblock`, `taskhold_add_note`, `taskhold_update`, `taskhold_set_priority`, `taskhold_list_projects`, `taskhold_list_labels`, `taskhold_get_summary`.

## Pricing

One plan: $12 a month or $120 a year per person, every agent you run included. 7-day trial with a card up front; cancel before it ends and nothing is charged. Details: https://taskhold.com/#pricing

## Support

hello@greatwork.company. Taskhold is made by Great Work LLC.

## License

The skill and the files in this repository are MIT licensed. The Taskhold service itself is hosted and is not open source.

<sub>Last updated: 2026-10-09</sub>
