# Contributing to Reedy for Claude Code

Thanks for your interest in contributing! Here's how you can help.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork locally**:
   ```bash
   git clone https://github.com/yourusername/claude-reedy-skill.git
   cd claude-reedy-skill
   ```
3. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Making Changes

### For Bug Fixes
1. Clearly describe the bug in your commit message
2. Include steps to reproduce if possible
3. Test your fix thoroughly

### For New Features
1. Open an issue first to discuss the feature
2. Get feedback before implementing
3. Document the feature in README.md if user-facing
4. Update SKILL.md with new command syntax if applicable

### Code Style
- Keep Python code readable and well-commented
- Follow PEP 8 conventions
- Test changes with `/reedy` in Claude Code

## Testing Your Changes

1. Copy your modified files to `~/.claude/skills/reedy/`
2. Test in Claude Code with `/reedy` and `/reedy [prompt]`
3. Verify setup works: `/reedy setup`
4. Test cleanup: `/reedy clean`
5. Test server stop: `/reedy stop`

## Submitting Changes

1. Push to your fork: `git push origin feature/your-feature-name`
2. Open a Pull Request on GitHub
3. Describe what your changes do
4. Reference any related issues: "Fixes #123"
5. Wait for review and feedback

## Pull Request Guidelines

- Keep PRs focused on a single feature or fix
- Write clear commit messages
- Include tests if applicable
- Update documentation as needed
- Be respectful and collaborative

## Reporting Bugs

Found a bug? Open an issue on GitHub with:
1. **Description** - What's broken?
2. **Steps to reproduce** - How do you trigger it?
3. **Expected behavior** - What should happen?
4. **Actual behavior** - What actually happens?
5. **Environment** - OS, Python version, Claude Code version

## Feature Requests

Have an idea? Open an issue and describe:
1. **The problem** - What pain point does this solve?
2. **Your solution** - How should it work?
3. **Why it matters** - Who benefits and how?

## Questions?

Feel free to open an issue with the label `question` or start a discussion.

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

Thank you for helping make Reedy better! 🚀
