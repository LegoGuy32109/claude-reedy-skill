# Publishing Reedy to GitHub & Claude Code Skills Registry

This guide walks you through setting up your repository for GitHub and publishing to the Claude Code skills registry.

## Step 1: Create a GitHub Repository

1. Go to [GitHub.com](https://github.com/new)
2. **Repository name**: `claude-reedy-skill` (or your preferred name)
3. **Description**: `Reedy RSVP speed reader integration for Claude Code`
4. **Visibility**: Public (required for Claude Code registry)
5. **Initialize with**: Leave unchecked (you'll push existing files)
6. Click **Create repository**

## Step 2: Initialize Git & Push to GitHub

In the `~/Projects/claude-reedy-skill` directory:

```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Reedy skill for Claude Code"

# Add remote repository (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/claude-reedy-skill.git

# Rename branch to main (if needed)
git branch -M main

# Push to GitHub
git push -u origin main
```

## Step 3: Create GitHub Release

Releases make your skill installable via version tags:

1. Go to your GitHub repository
2. Click **Releases** (right sidebar)
3. Click **Create a new release**
4. **Tag version**: `v1.0.0`
5. **Release title**: `Reedy v1.0.0`
6. **Description**: Copy content from README.md
7. Click **Publish release**

To create a release from command line:

```bash
git tag v1.0.0 -m "Initial release"
git push origin v1.0.0
```

## Step 4: Prepare for Claude Code Skills Registry

Once published on GitHub, submit to Claude Code registry:

### Update manifest.json

Before submitting, update the repository URL in `manifest.json`:

```json
"repository": {
  "type": "git",
  "url": "https://github.com/YOUR-USERNAME/claude-reedy-skill.git"
},
"homepage": "https://github.com/YOUR-USERNAME/claude-reedy-skill",
"bugs": {
  "url": "https://github.com/YOUR-USERNAME/claude-reedy-skill/issues"
}
```

### Update README.md

Update the README with your actual GitHub URL in the manual installation section:

```bash
git clone https://github.com/YOUR-USERNAME/claude-reedy-skill.git
```

### Submit to Registry

When the Claude Code skills registry opens for submissions:

1. Visit the Claude Code skills registry page
2. Click **Submit a skill**
3. Enter your repository URL
4. Fill in required information
5. Wait for review and approval

For now, users can install manually:
```bash
cp -r claude-reedy-skill ~/.claude/skills/reedy
```

## Step 5: Maintain Your Repository

### Keep It Updated

After you submit, keep your repo maintained:

1. **Fix bugs** - Test thoroughly, commit, push
2. **Add features** - Follow contribution guidelines
3. **Release updates** - Tag versions with git tags

### Create a Release Workflow

```bash
# 1. Make changes and test
# ... edit files and test with /reedy in Claude Code ...

# 2. Update version in manifest.json and README
# Edit manifest.json: "version": "1.1.0"

# 3. Commit changes
git add .
git commit -m "Feature: Add new capability"

# 4. Create a tag
git tag v1.1.0 -m "Release 1.1.0: Add new feature"

# 5. Push everything
git push origin main
git push origin v1.1.0
```

## Advanced: Setting Up Continuous Integration

Optional but recommended for quality:

### Create `.github/workflows/test.yml`:

```yaml
name: Test Skill

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: 3.9
      - name: Run skill test
        run: python3 ./reedy-serve --list
```

## Directory Structure for GitHub

Your repository should look like this:

```
claude-reedy-skill/
├── reedy-serve           # Main Python script
├── SKILL.md              # Skill definition
├── README.md             # User documentation
├── CONTRIBUTING.md       # Contribution guidelines
├── LICENSE               # MIT License
├── manifest.json         # Skill manifest
├── .gitignore            # Git ignore file
├── GITHUB_SETUP.md       # This file
└── .github/
    └── workflows/        # (optional) CI/CD workflows
        └── test.yml
```

## Troubleshooting

### "Remote origin already exists"
```bash
git remote remove origin
git remote add origin https://github.com/YOUR-USERNAME/claude-reedy-skill.git
```

### "Authentication failed"
- Use SSH instead: `git remote set-url origin git@github.com:YOUR-USERNAME/claude-reedy-skill.git`
- Or generate a personal access token and use it instead of your password

### Repository not appearing in searches
- Ensure it's public (not private)
- Add relevant topics/tags on GitHub
- Add good descriptions and README

## Questions or Issues?

- Check [GitHub documentation](https://docs.github.com)
- Open an issue in your repository
- Ask in Claude Code discussions

---

**Next Steps:**
1. Follow the setup steps above
2. Verify everything is on GitHub
3. Create your first release
4. Share the repository link with others!
