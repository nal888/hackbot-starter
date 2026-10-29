# Keep a link to the session

Start Claude Code or Codex from your target folder. Record the session's real ID
and transcript location in `sessions/INDEX.md`. Notes should point back to that
record, with a turn, timestamp or tool-call reference when useful.

## Save a readable copy

These are commands to type inside the agent's terminal interface, not shell
commands. Wait until the current turn finishes. Use a different filename for
each session and record when you exported it.

| Tool | Save the conversation |
| --- | --- |
| Claude Code | `/export sessions/claude-01.txt` |
| Codex CLI | `/export sessions/codex-01.md` |

Claude exports plain text; Codex exports Markdown. Open the file afterwards to
check what it contains. An export is a snapshot, so export again after more work.
See the [Claude commands](https://code.claude.com/docs/en/commands) and
[Codex commands](https://learn.chatgpt.com/docs/developer-commands#export-a-conversation-with-export).

## Record the ID and original log

For **Claude Code**, local transcripts normally live at
`~/.claude/projects/<project>/<session-id>.jsonl`. The filename gives the session
ID. Check the working directory and messages before linking a file; do not pick
the newest file across all projects. A custom `CLAUDE_CONFIG_DIR` changes the
base directory. See [Claude session storage](https://code.claude.com/docs/en/sessions).

For **Codex CLI**, check `/status` for the current session details. You can also
use `/statusline` to display the session ID. Local installations may have JSONL
logs under `~/.codex/sessions/`, but storage can differ by version or runtime.
Record a verified log path when available; otherwise keep the exported file and
mark the original log as unavailable. Do not make up a path from the ID.
See [Codex session commands](https://learn.chatgpt.com/docs/developer-commands).

If you later automate the bookkeeping, both tools expose `session_id` and
`transcript_path` to hooks. Codex's path can be null. Use the values supplied by
the runtime instead of guessing filenames. This template does not install hooks.
See [Claude hooks](https://code.claude.com/docs/en/hooks#common-input-fields) and
[Codex hooks](https://learn.chatgpt.com/docs/hooks#common-input-fields).

## Come back to it

From your target folder, run the relevant shell command, replacing the example
ID with the recorded one:

```sh
claude --resume YOUR_SESSION_ID
```

```sh
codex resume YOUR_SESSION_ID
```

These reopen locally available sessions. A text or Markdown export is a reading
copy, not a restore file. If the session was deleted, its ID alone cannot restore it.

When a worker has its own record, keep its ID, its parent session ID and its own
transcript reference. In Claude, a subagent's `agent_id` is distinct from the main
`session_id`; label it as a worker ID. Do not use the parent's transcript as if it
contained every worker tool result.

Keep original evidence files if a log contains shortened output. Before sharing,
review exports and logs for credentials or private data. Record missing history
as missing; a generated summary cannot replace it.
