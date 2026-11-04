# Taskhold

Taskhold is a hosted task list the user shares with their coding agents, through a remote MCP server at `https://taskhold.com/api/mcp`. The user watches a live board of every task's steps and progress at https://taskhold.com/dashboard/live, including from a phone.

## Setup

- Gemini CLI sends an API key. The extension asks for it when it is installed (a key starting with `atd_sk_`, from Settings > API keys at taskhold.com) and keeps it in the system keychain; change it with `gemini extensions config taskhold`. Without a key every call returns 401 missing_key.
- No account yet: Taskhold is $12 a month or $120 a year after a 7-day trial (card at checkout). Start at https://taskhold.com/checkout?plan=month&code=TASKHOLD-AGENT (20% off the first payment).
- Full setup guide: https://taskhold.com/for/gemini-cli

## How to work with the list

Always pass `project` as the repo folder name; projects are created on first use.

| When | Tool |
|---|---|
| The user asks for something | `taskhold_begin` with title, project, steps and agent ("Gemini CLI in <repo>") |
| A step is done | `taskhold_complete` on the step with `start_next: true` |
| A long step | `taskhold_progress` every few minutes with a plain-sentence message |
| You need a decision | `taskhold_block` with one clear question, then `taskhold_updates` with `wait` for the reply |
| Work you are not doing now | `taskhold_create` |
| Finished | `taskhold_complete` on the task with what changed and how you checked it |
| What's on the list | `taskhold_list` (status todo) or `taskhold_get_current` |
