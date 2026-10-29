# Hackbot starter

A small place to keep a target’s scope, current notes and evidence references.
Fill it as you work; you do not need to complete every field before taking notes.

This is a starting template for the notes around AI-assisted bug bounty work.
It does not include a testing agent or the full system from the blog.

## Get the files

Copy the files you want from GitHub, use **Code → Download ZIP**, or clone:

```sh
git clone https://github.com/nal888/hackbot-starter.git
cd hackbot-starter
```

```text
targets/TARGET-NAME/
├── CLAUDE.md            scope, rules and account labels
├── AGENTS.md            points to the same target brief
├── APPLICATION.md       what you know about the application
├── NOTES.md             current question, decisions and gaps
├── sessions/INDEX.md    session IDs and transcript locations
└── evidence/            notes and saved artifacts
```

## Start with one target

1. Copy `targets/TARGET-NAME/` into your workspace and rename it.
2. Fill `CLAUDE.md` using the program's current rules, with source links and the
   date you checked them. For a local lab, record which instance you control.
3. Put one current question in `NOTES.md`. Leave observations empty until you
   have evidence; mark missing information as unknown.
4. In `sessions/INDEX.md`, record the agent, session ID and transcript location.
   Use the ID reported by your agent or session export; don't invent one.
   Record worker sessions separately when they have their own IDs.
   [SESSION-GUIDE.md](SESSION-GUIDE.md) explains how to save a transcript and
   return to a session in Claude Code or Codex CLI.
5. Copy `evidence/NOTE-TEMPLATE.md` for a useful observation or attempt. Link the
   relevant transcript turn and any saved files. If the tool gives an operation
   or request ID, record it with the location of its original result too.
   Keep `NOTES.md` short.

`CLAUDE.md` holds the target brief. `AGENTS.md` points Codex to that same file,
so scope is maintained in one place. From another working directory, explicitly
ask the agent to read the target brief rather than assuming it loaded it.

Open a terminal in the copied target folder, then launch the agent you use:

```sh
cd targets/TARGET-NAME
```

Run `claude` or `codex` there. Replace `TARGET-NAME` with your folder's name.
You do not need to run both.

A first request can simply be:

> Read this target's CLAUDE.md and NOTES.md. Summarize the recorded scope and
> current question, and list missing setup information. Use these saved files
> only; don't send requests to the application or change the records yet.

The transcript is the detailed session history. Notes are an index into it.
Keep original evidence separately when the transcript only shows excerpts or
truncated output. Don't assume a session ID alone will remain accessible after
moving machines; record the transcript path or export location too.

A session ID gets you back to the conversation. An operation ID gets you to a
particular recorded action. For example, a tool might return `op_005` for one
request: link that ID to its saved request and response, along with the tool/run
it belongs to. This example is only a label, not a supplied record. The template
does not generate operation IDs or include a replay interface.

The operation-ID idea comes from
[BruteCat’s “Refining the Approach” section](https://brutecat.com/articles/hacking-google-with-ai/#refining-the-approach),
where reports reference recorded API operations for review.

Keep credentials out of these notes. Review transcripts and captures before
sharing them; the included ignore rules only help with Git, not ZIP exports.
This template contains no real targets, accounts, transcripts or findings.
