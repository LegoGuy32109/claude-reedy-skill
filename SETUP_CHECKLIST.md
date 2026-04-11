# Reedy Skill Setup Checklist

Use this checklist to verify your skill is ready to publish.

## ✅ Project Structure

- [ ] `reedy-serve` - Main Python script (11K)
- [ ] `SKILL.md` - Skill definition file (3.6K)
- [ ] `README.md` - User documentation (6.5K)
- [ ] `manifest.json` - Claude Code skill manifest (1.1K)
- [ ] `LICENSE` - MIT License file (1.1K)
- [ ] `.gitignore` - Git ignore configuration (412 bytes)
- [ ] `CONTRIBUTING.md` - Contribution guidelines (2.3K)
- [ ] `GITHUB_SETUP.md` - GitHub publishing guide (5K)
- [ ] `QUICK_START_GITHUB.md` - Quick setup guide (3.3K)
- [ ] `SETUP_CHECKLIST.md` - This file

## ✅ Git Repository

- [ ] Git initialized: `git init` ✓
- [ ] Initial commit created: `git commit -m "Initial commit"`
- [ ] All files staged and committed
- [ ] No uncommitted changes

Check with:
```bash
cd ~/Projects/claude-reedy-skill
git status
```

## ✅ Code Quality

- [ ] `reedy-serve` is executable: `chmod +x reedy-serve`
- [ ] `SKILL.md` has complete documentation
- [ ] `README.md` includes:
  - [ ] Feature overview
  - [ ] Installation instructions
  - [ ] Quick start guide
  - [ ] Command reference
  - [ ] Troubleshooting section
  - [ ] Browser extension link
  - [ ] FAQ section

## ✅ Documentation

- [ ] `CONTRIBUTING.md` - Guidelines for contributors
- [ ] `GITHUB_SETUP.md` - Step-by-step GitHub publishing guide
- [ ] `QUICK_START_GITHUB.md` - Simplified quick start
- [ ] `LICENSE` - MIT License included
- [ ] `manifest.json` - Updated with correct metadata

## ✅ Before Publishing to GitHub

Update these files with YOUR-USERNAME:

1. **README.md**
   - [ ] Update clone URL: `https://github.com/YOUR-USERNAME/claude-reedy-skill.git`

2. **manifest.json**
   - [ ] Update repository URL
   - [ ] Update homepage URL
   - [ ] Update bugs URL
   - [ ] Verify version is `1.0.0` or appropriate

3. **GITHUB_SETUP.md**
   - [ ] Already has instructions, no changes needed

## ✅ Manual Installation Test

Verify the skill works before publishing:

1. Test in Claude Code:
   ```
   /reedy setup
   ```
   Should output: "Reedy setup complete!" or show Python path

2. Test with a response:
   ```
   /reedy explain how trees grow
   ```
   Should send to http://localhost:7766

3. Test cleanup:
   ```
   /reedy stop
   ```
   Should stop the server

## ✅ GitHub Publication Steps

Follow these in order:

1. [ ] Create GitHub repository at [github.com/new](https://github.com/new)
2. [ ] Copy HTTPS URL from GitHub
3. [ ] Add remote: `git remote add origin https://github.com/YOUR-USERNAME/...`
4. [ ] Push: `git push -u origin main`
5. [ ] Create release: `git tag v1.0.0` → `git push origin v1.0.0`
6. [ ] Or use GitHub web interface for releases

## ✅ Post-Publication

- [ ] Repository is public
- [ ] README is visible on GitHub
- [ ] Release v1.0.0 is created
- [ ] Clone URL works: `git clone https://github.com/YOUR-USERNAME/claude-reedy-skill.git`
- [ ] Installation works:
  ```bash
  cp -r claude-reedy-skill ~/.claude/skills/reedy
  /reedy setup
  ```

## ✅ Ready for Distribution

Once everything above is checked:

- [ ] GitHub repository created ✓
- [ ] All files pushed ✓
- [ ] v1.0.0 release created ✓
- [ ] Verified installation works ✓
- [ ] Documentation complete ✓
- [ ] Ready to share link!

## 🚀 Next Steps

1. **Create GitHub repository** - Use QUICK_START_GITHUB.md
2. **Update YOUR-USERNAME** - In README and manifest.json
3. **Push to GitHub** - Follow git commands in QUICK_START_GITHUB.md
4. **Share the repository** - Everyone can now install!

Example installation for others:
```bash
git clone https://github.com/YOUR-USERNAME/claude-reedy-skill.git ~/.claude/skills/reedy
/reedy setup
```

## Support & Issues

- **Documentation**: See README.md
- **Contributing**: See CONTRIBUTING.md
- **GitHub Setup**: See GITHUB_SETUP.md & QUICK_START_GITHUB.md
- **Troubleshooting**: See README.md FAQ section

---

**You're all set! Your Reedy skill is production-ready.** 🎉
