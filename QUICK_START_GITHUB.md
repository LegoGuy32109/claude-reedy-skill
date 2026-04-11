# Quick Start: Publish to GitHub

Your Reedy skill is ready to go! Follow these 5 quick steps to publish on GitHub.

## 1. Create GitHub Repository

Go to [github.com/new](https://github.com/new):
- **Repository name**: `claude-reedy-skill`
- **Visibility**: Public
- **Initialize with**: Nothing (you'll push existing files)
- Click **Create repository**

## 2. Connect Your Local Repo

Run these commands:
```bash
cd ~/Projects/claude-reedy-skill
git remote add origin https://github.com/LegoGuy32109/claude-reedy-skill.git
git branch -M main
git push -u origin main
```

## 3. Create a Release

```bash
cd ~/Projects/claude-reedy-skill
git tag v1.0.0 -m "Initial release"
git push origin v1.0.0
```

Or use the GitHub web interface:
- Go to your repo
- Click **Releases**
- Click **Create a new release**
- Tag: `v1.0.0`
- Title: `Reedy v1.0.0`
- Publish!

## 4. Documentation Already Updated

✅ README.md is configured with GitHub URLs
✅ manifest.json is configured with repository information
✅ Everything is ready to go!

No additional updates needed — your repository is fully configured.

## 5. Share Your Skill

Users can now install with:
```bash
git clone https://github.com/LegoGuy32109/claude-reedy-skill.git ~/.claude/skills/reedy
```

**Repository link:** https://github.com/LegoGuy32109/claude-reedy-skill

## What You Have

✅ Complete skill code (`reedy-serve` + `SKILL.md`)
✅ Comprehensive README with installation & troubleshooting
✅ MIT License for open distribution
✅ Manifest for Claude Code registry
✅ Contributing guidelines for collaborators
✅ GitHub setup guide with CI/CD examples
✅ .gitignore for clean commits
✅ Initial git repo initialized

## File Overview

| File | Purpose |
|------|---------|
| `reedy-serve` | Main Python script (the skill) |
| `SKILL.md` | Skill definition & command docs |
| `README.md` | User-facing documentation |
| `manifest.json` | Claude Code skill metadata |
| `LICENSE` | MIT License |
| `CONTRIBUTING.md` | Guidelines for contributors |
| `GITHUB_SETUP.md` | Detailed GitHub publishing guide |
| `QUICK_START_GITHUB.md` | This file |

## Future Updates

When you make improvements:

```bash
# Make changes
# ... edit files and test with /reedy ...

# Update version in manifest.json
# "version": "1.1.0"

# Commit
git add .
git commit -m "Feature: Your feature description"

# Release
git tag v1.1.0 -m "Release 1.1.0"
git push origin main v1.1.0
```

## Share Your Skill!

Once published, share the link:
- **GitHub**: `https://github.com/YOUR-USERNAME/claude-reedy-skill`
- **Direct install**: `git clone https://github.com/YOUR-USERNAME/claude-reedy-skill.git ~/.claude/skills/reedy`

---

Ready? Start with Step 1! 🚀
