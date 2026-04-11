# Reedy for Claude Code

A Claude Code plugin that sends Claude responses directly to the [Reedy RSVP speed reader](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj) for word-by-word reading in your browser.

## Requirements

- **Python 3.6+** accessible as `python3` or `python`
- **[Reedy Chrome Extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj)**
- **Claude Code** (latest version)
- **Windows users:** Git Bash or WSL required

## Installation

```bash
claude plugin marketplace add https://github.com/LegoGuy32109/claude-reedy-skill
claude plugin install reedy@reedy
```

On first use, the command will automatically detect your Python install, write a runtime config, add `Bash(*reedy-serve*)` to your `allowedTools`, and verify everything works. You can also trigger this manually:

```
/reedy setup
```

> **Note:** Depending on your Claude Code version the command may appear as `/reedy:reedy` in the skill list. Both `/reedy` and `/reedy:reedy` invoke the same skill.

## Commands

| Command | Description |
|---|---|
| `/reedy` | Send the last Claude response to Reedy |
| `/reedy [prompt]` | Answer a prompt in plain prose and send it to Reedy |
| `/reedy setup` | First-time setup: detects Python, writes runtime config, configures permissions |
| `/reedy stop` | Stop the local Reedy server |
| `/reedy clean` | Clear reading history |

## How It Works

1. The plugin runs a local HTTP server on port 7766 (started on first use, persists until stopped)
2. Claude writes response text to a temp file and passes it to the server
3. The server saves the content and notifies the browser via polling
4. The Reedy extension intercepts the page and starts RSVP playback when you press Space

Navigate to **http://localhost:7766** to view your reading history.

## Troubleshooting

**`needs_setup` on every run** — the SessionStart hook couldn't find Python. Run `/reedy setup` manually.

**Page loads but Reedy doesn't activate** — install the [Reedy Chrome extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj).

**Server won't start** — check that port 7766 is free: `lsof -i :7766` (Linux/Mac) or `netstat -ano | findstr 7766` (Windows).

**Python not found** — ensure `python3` or `python` is in your PATH and retry `/reedy setup`.

## License

MIT — [Josh Hale](https://github.com/LegoGuy32109)
