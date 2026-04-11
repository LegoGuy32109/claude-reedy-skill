---
name: reedy
description: Open Claude responses in the Reedy RSVP speed reader. /reedy to open the last response, /reedy [prompt] to answer and open, /reedy stop to kill the server, /reedy clean to purge history.
---

You are executing the `/reedy` skill. Read the arguments, then follow the matching instructions below.

**Note:** This skill requires the [Reedy Chrome extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj) to be installed. If you don't have it, the web app will display a link to install it.

---

## `/reedy setup` — First-time onboarding (run this once)

Tests that Python 3 is accessible and the script runs correctly on this system.

**macOS / Linux:** Run this in your terminal or directly here.

**Windows:** The bash heredoc syntax (`<<'EOF'`) used by this skill requires bash. Run setup and all `/reedy` commands inside **Git Bash** or **WSL**. PowerShell and cmd are not supported.

Run:
```bash
python3 ~/.claude/skills/reedy/reedy-serve --list >/dev/null 2>&1 && echo "Reedy setup complete! You can now use /reedy" || echo "Setup failed. Ensure Python 3 is installed and accessible as 'python3'."
```

---

## `/reedy stop`

Run:
```bash
python3 ~/.claude/skills/reedy/reedy-serve --stop
```
Tell the user the server was stopped.

---

## `/reedy clean`

Run:
```bash
python3 ~/.claude/skills/reedy/reedy-serve --list
```
Show the user the file list. Ask them to reply with "yes" to confirm deletion. If they confirm, run:
```bash
python3 ~/.claude/skills/reedy/reedy-serve --clean
```

---

## `/reedy` with no additional text — Scenario 1 (fastest path)

1. Extract the most recent AI assistant message from this conversation. Do NOT transform it — take it raw, exactly as written, markdown and all.

2. From the first sentence, pick 4–6 meaningful words to form a slug: lowercase, hyphen-separated, no punctuation. Skip words like: the, a, an, is, it, of, to, and, in, that, was, for, be.

3. Run this bash command (substitute YOUR-SLUG and paste the raw text between the heredoc markers):

```bash
python3 ~/.claude/skills/reedy/reedy-serve --ingest YOUR-SLUG <<'REEDYEOF'
RAW TEXT CONTENT HERE
REEDYEOF
```

4. Tell the user:
> Sent to Reedy. Navigate to **http://localhost:7766** and press **Space** to start reading. If Reedy doesn't load, the page will show you a link to install the extension.

---

## `/reedy [prompt]` — Scenario 2

Apply ALL of the following rules when composing your answer — these rules exist to make the text readable word-by-word in an RSVP speed reader:

RULE 1 — No markdown of any kind. No bullet points, no dashes used as list markers, no headers, no bold (**text**), no italics (*text*), no code blocks, no backticks.
RULE 2 — No citations or source references.
RULE 3 — Do not shorten or summarize. Give a complete and thorough answer.
RULE 4 — ONE UNBROKEN BLOB of text. Zero blank lines anywhere in the response. Separate paragraphs with a single space only. No line breaks except where a natural sentence ends and the next begins in the same flow.
RULE 5 — Write the full answer inline in the chat response, not in a code block or attachment.

After writing the answer inline, pick 4–6 meaningful words from the first sentence for the slug, then run:

```bash
python3 ~/.claude/skills/reedy/reedy-serve --ingest YOUR-SLUG <<'REEDYEOF'
YOUR PLAIN PROSE ANSWER HERE
REEDYEOF
```

Tell the user:
> Sent to Reedy — navigate to **http://localhost:7766** and press **Space** to start reading. If Reedy doesn't load, the page shows a link to install the extension.
