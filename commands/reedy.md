---
name: reedy
description: Open Claude responses in the Reedy RSVP speed reader. /reedy to open the last response, /reedy [prompt] to answer and open, /reedy stop to kill the server, /reedy clean to purge history.
---

You are executing the `/reedy` skill. Read the arguments, then follow the matching section below.

**Note:** This skill requires the [Reedy Chrome extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj). If it's not installed, the web app will show a link to install it.

---

## Runtime check (run this first for every command except `/reedy setup`)

Check whether the runtime env exists:

```bash
test -f "$HOME/.local/share/reedy/reedy.env" && echo "ready" || echo "needs_setup"
```

If the output is `needs_setup`, run the **`/reedy setup`** flow below automatically before continuing with the original command.

All reedy bash commands use this invocation pattern:
```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" [args]
```

---

## `/reedy setup` — First-time setup (also runs automatically on first use)

### Step 1 — Detect Python

Tell the user: "Checking for Python 3 (required to run the local Reedy server)..."

```bash
python3 --version 2>/dev/null && echo "python3" || (python --version 2>/dev/null && echo "python") || echo "not_found"
```

- If `not_found`: tell the user Python 3 is required and cannot be found in PATH, then stop.
- Store the working command as PYTHON_CMD (either `python3` or `python`).

### Step 2 — Find the reedy-serve script

Tell the user: "Locating the reedy-serve script in your Claude plugin installation..."

Search the installed plugin cache first, then fall back to the marketplace clone:

```bash
find "$HOME/.claude/plugins/cache" -name "reedy-serve" 2>/dev/null | head -1
```

If empty, try:

```bash
find "$HOME/.claude/plugins/marketplaces" -name "reedy-serve" 2>/dev/null | head -1
```

Store the result as SCRIPT_PATH. If still empty, tell the user the plugin doesn't appear to be installed and stop.

### Step 3 — Write the runtime env

Tell the user: "Writing runtime config to `~/.local/share/reedy/reedy.env` — this stores the Python path and script location so commands run without re-detecting them each session (the SessionStart hook keeps this up to date automatically)..."

```bash
$PYTHON_CMD "$SCRIPT_PATH" --write-runtime "$(dirname "$SCRIPT_PATH")"
```

### Step 4 — Add allowedTools to user settings

Tell the user: "Adding `Bash(*reedy-serve*)` and `Write(/tmp/reedy_content.txt)` to `allowedTools` in `~/.claude/settings.json` — this allows reedy-serve to run and response content to be written to the temp ingest file without prompts each time..."

Read `~/.claude/settings.json`. If it doesn't exist, treat it as `{}`. Add both `"Bash(*reedy-serve*)"` and `"Write(/tmp/reedy_content.txt)"` to the `allowedTools` array (nested under `permissions.allow` if that structure exists, otherwise top-level) if not already present. Write the file back.

### Step 5 — Verify

Tell the user: "Verifying the installation end-to-end..."

```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" --list >/dev/null 2>&1 && echo "ok" || echo "fail"
```

- If `ok`: tell the user setup is complete and they're ready to use `/reedy`.
- If `fail`: tell the user the script was found but failed to run, and show any error output.

---

## `/reedy stop`

```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" --stop
```

Tell the user the server was stopped.

---

## `/reedy clean`

```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" --list
```

Show the file list. Ask the user to reply with "yes" to confirm deletion. If confirmed:

```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" --clean
```

---

## `/reedy` with no additional text — Scenario 1

1. Extract the most recent AI assistant message from this conversation. Take it raw, exactly as written — markdown and all.

2. From the first sentence, pick 4–6 meaningful words for a slug: lowercase, hyphen-separated, no punctuation. Skip: the, a, an, is, it, of, to, and, in, that, was, for, be.

3. Use the **Write tool** to write the raw text to `/tmp/reedy_content.txt`.

4. Run:
```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" --ingest YOUR-SLUG --file /tmp/reedy_content.txt
```

5. Delete the temp file:
```bash
rm -f /tmp/reedy_content.txt
```

6. Tell the user:
> Sent to Reedy. Navigate to **http://localhost:7766** and press **Space** to start reading. If Reedy doesn't load, the page will show a link to install the extension.

---

## `/reedy [prompt]` — Scenario 2

Apply ALL of the following rules when composing your answer:

RULE 1 — No markdown of any kind. No bullet points, no dashes, no headers, no bold, no italics, no code blocks, no backticks.
RULE 2 — No citations or source references.
RULE 3 — Do not shorten or summarize. Give a complete and thorough answer.
RULE 4 — ONE UNBROKEN BLOB of text. Zero blank lines. Separate paragraphs with a single space only.
RULE 5 — Write the full answer inline in the chat response, not in a code block or attachment.

After writing the answer inline:

1. Pick 4–6 meaningful words from the first sentence for the slug.

2. Use the **Write tool** to write the plain prose answer to `/tmp/reedy_content.txt`.

3. Run:
```bash
. "$HOME/.local/share/reedy/reedy.env" && "$REEDY_PY" "$REEDY_SCRIPT" --ingest YOUR-SLUG --file /tmp/reedy_content.txt
```

4. Delete the temp file:
```bash
rm -f /tmp/reedy_content.txt
```

5. Tell the user:
> Sent to Reedy — navigate to **http://localhost:7766** and press **Space** to start reading. If Reedy doesn't load, the page shows a link to install the extension.
