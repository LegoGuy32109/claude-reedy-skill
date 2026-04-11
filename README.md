# Reedy for Claude Code

A Claude Code skill that integrates the **Reedy RSVP speed reader** with Claude AI responses. Send Claude's answers directly to Reedy for optimized speed reading in your browser.

## Features

- 📖 **RSVP Speed Reading** - Read Claude responses at your own pace using rapid serial visual presentation
- ⚡ **One-Command Integration** - Use `/reedy` to send responses to Reedy with zero configuration
- 🎯 **Flexible Prompting** - Read the last response or answer a new prompt and read it instantly
- 🧹 **History Management** - View and clean your reading history
- 🌐 **Browser-Based** - Works with the Reedy Chrome extension for the best experience

## Installation

### Option 1: Install from Claude Code (Recommended)

Coming soon! Once published to the Claude Code skill registry, you'll be able to install with:

```
/skills install reedy
```

### Option 2: Manual Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/claude-reedy-skill.git
   ```

2. Copy the skill to your Claude Code skills directory:
   ```bash
   cp -r claude-reedy-skill ~/.claude/skills/reedy
   ```

3. Make the script executable (Linux/Mac):
   ```bash
   chmod +x ~/.claude/skills/reedy/reedy-serve
   ```

4. Verify installation by running:
   ```bash
   /reedy setup
   ```

### Requirements

- **Python 3.6+** - Must be accessible as `python3` in your terminal
- **Reedy Chrome Extension** - Install from the [Chrome Web Store](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj)
- **Claude Code** - Latest version (web, CLI, desktop, or IDE extension)

## Quick Start

### 1. Install the Reedy Browser Extension

Visit the [Chrome Web Store](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj) and click "Add to Chrome".

### 2. Setup the Skill (First Time Only)

```
/reedy setup
```

This verifies Python 3 is available and the skill is ready to use.

### 3. Use Reedy with Claude Responses

**Send the last Claude response to Reedy:**
```
/reedy
```

**Answer a prompt and send the response to Reedy:**
```
/reedy explain how photosynthesis works
```

The response will be sent to Reedy. Open your browser to **http://localhost:7766** and press **Space** to start speed reading.

## Commands

| Command | Description |
|---------|-------------|
| `/reedy` | Send the last Claude response to Reedy |
| `/reedy [prompt]` | Answer a prompt and send it to Reedy |
| `/reedy stop` | Stop the Reedy local server |
| `/reedy clean` | Clear your Reedy reading history |
| `/reedy setup` | Verify Python 3 and skill setup |

## How It Works

1. When you run `/reedy`, the skill sends Claude's text to a local Python server
2. The server opens a web interface at `http://localhost:7766`
3. The Reedy Chrome extension renders the text in RSVP format
4. Press **Space** to start reading - the extension automatically advances words at your set pace
5. Adjust reading speed, font size, and other settings directly in Reedy

## Browser Access

The Reedy reader runs on your local machine at:
- **URL**: `http://localhost:7766`
- **Port**: 7766 (configurable in the source code if needed)

Make sure the Reedy Chrome extension is installed so the web interface renders properly.

## Troubleshooting

### "Setup failed. Ensure Python 3 is installed"
- Verify Python 3 is installed: `python3 --version`
- Make sure it's accessible from your terminal
- On Windows, use **Git Bash** or **WSL** (PowerShell and cmd are not supported)

### Reedy doesn't load at http://localhost:7766
- Ensure the Reedy Chrome extension is installed
- Check that port 7766 is not in use: `lsof -i :7766` (macOS/Linux)
- Try `/reedy stop` then run `/reedy` again

### Python 3 not found on Windows
Use **Git Bash** or **WSL** instead of PowerShell or cmd.exe. The bash heredoc syntax required by this skill doesn't work in native Windows shells.

### "Address already in use" error
The Reedy server may still be running from a previous session:
```bash
/reedy stop
```

## Features & Settings

### Reading Speed
Adjust words per minute (WPM) directly in the Reedy extension. Default is typically 300 WPM.

### Text Formatting
The skill automatically formats your response to be optimal for RSVP reading:
- Removes markdown syntax
- Converts to plain prose
- Maintains paragraph structure for readability

### History
View all your previous readings:
```
/reedy clean
```
This will show you the list. Type "yes" to delete all history.

## Development

### Project Structure

```
claude-reedy-skill/
├── reedy-serve          # Main Python server script
├── SKILL.md             # Skill definition and documentation
├── README.md            # This file
├── LICENSE              # MIT License
└── manifest.json        # Claude Code skill manifest (optional)
```

### Modifying the Skill

The core logic is in `reedy-serve`. To modify:

1. Edit `reedy-serve` in your text editor
2. Make your changes
3. Test with `/reedy` in Claude Code
4. Commit and push to GitHub

### Building & Publishing

This skill is designed for easy distribution:

1. Create a GitHub repository
2. Push all files from this directory
3. When ready, submit to the Claude Code skill registry for `/skills install` support

## Contributing

Found a bug or have a feature request? Open an issue on GitHub!

## License

MIT - See LICENSE file for details

## Credits

- **Reedy Extension** - [Created by Jaxson Van Doorn](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj)
- **Claude Code** - [Anthropic](https://github.com/anthropics/claude-code)

## Frequently Asked Questions

**Q: Does this work with all Claude models?**
A: Yes! The skill works with any Claude response in Claude Code.

**Q: Can I use this on mobile?**
A: The Reedy extension is Chrome-only, so you'll need a desktop or laptop with Chrome installed.

**Q: Can I adjust the reading speed?**
A: Yes! Use the Reedy extension's settings to customize WPM, font size, and other options.

**Q: Is my reading history stored anywhere?**
A: Your history is stored locally in your user's `.claude` directory. Run `/reedy clean` to delete it.

**Q: How fast can I read?**
A: There's no limit! Reedy supports speeds from 100 to 1000+ WPM depending on the extension settings and your reading ability.

---

**Ready to speed-read Claude responses?** Install the [Reedy extension](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj) and run `/reedy setup` in Claude Code to get started!
