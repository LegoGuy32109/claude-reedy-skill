# Reedy for Claude Code

A Claude Code plugin that sends Claude responses directly to the [Reedy RSVP speed reader](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj) for word-by-word reading in your browser.

_[for web claude ai users go here](#web-version-claudeai)_

## Requirements

- __Python 3.6+__ accessible as `python3` or `python`
- __[Reedy Chrome Extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj)__
- __Claude Code__ (latest version)
- __Windows users:__ Git Bash or WSL required

## Installation

```bash
claude plugin marketplace add https://github.com/LegoGuy32109/claude-reedy-skill
claude plugin install reedy@reedy
```

On first use, the command will automatically detect your Python install, write a runtime config, add `Bash(*reedy-serve*)` to your `allowedTools`, and verify everything works. You can also trigger this manually:

```
/reedy setup
```

> __Note:__ Depending on your Claude Code version the command may appear as `/reedy:reedy` in the skill list. Both `/reedy` and `/reedy:reedy` invoke the same skill.

## Web Version (claude.ai)

No Python or local server required. The web skill strips markdown from Claude's responses and outputs clean prose ready to paste into Reedy's text field.

__Setup:__

1. Download [`reedy-claude-web-skill.md`](https://raw.githubusercontent.com/LegoGuy32109/claude-reedy-skill/main/reedy-claude-web-skill.md) from this repo.
2. Navigate to [claude.ai](https://claude.ai/customize/skills)
3. In the sidebar, click __Customize__ → __Skills__ → __+ (Plus)__ -> __Create skill__ and upload `reedy-claude-web-skill.md`.
4. That's it! The skill is now active for every conversation in that Project.

__Usage:__

| Message | What happens |
|---|---|
| `/reedy` | Rewrites the last Claude response as clean, citation-free prose |
| `/reedy [prompt]` | Answers your prompt as clean prose, ready for Reedy |

At the end of every response you'll see:

```
— Select the text above and press Alt+S to open in Reedy
```

Select all the prose text, then press __Alt+S__ with the [Reedy extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj) installed to begin speed-reading.

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

Navigate to __<http://localhost:7766>__ to view your reading history.

## Troubleshooting

__`needs_setup` on every run__ — the SessionStart hook couldn't find Python. Run `/reedy setup` manually.

__Page loads but Reedy doesn't activate__ — install the [Reedy Chrome extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj).

__Server won't start__ — check that port 7766 is free: `lsof -i :7766` (Linux/Mac) or `netstat -ano | findstr 7766` (Windows).

__Python not found__ — ensure `python3` or `python` is in your PATH and retry `/reedy setup`.

## License

MIT — [Josh Hale](https://github.com/LegoGuy32109)
