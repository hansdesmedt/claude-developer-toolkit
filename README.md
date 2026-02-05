# Claude Developer Toolkit

Essential development workflow skills for Claude Code - automate commits, code reviews, debugging, feature implementation, and changelog generation.

## 🎯 Skills Included

- **`/commit`** - Create conventional git commits with structured messages
- **`/pr-review`** - Thorough code reviews with direct, constructive feedback
- **`/implement`** - Feature implementation following best practices
- **`/debug`** - Interactive debugging with auto-start and log monitoring
- **`/changelog`** - Generate changelog entries from git history

## 📦 Installation

### Option 1: Install as Plugin (Recommended)

```bash
/plugin marketplace add hansdesmedt/claude-developer-toolkit
/plugin install developer-toolkit@claude-developer-toolkit
```

### Option 2: Clone to Global Skills Directory

```bash
git clone https://github.com/hansdesmedt/claude-developer-toolkit.git ~/.claude/skills/developer-toolkit
```

Or clone to a project-specific directory:

```bash
git clone https://github.com/hansdesmedt/claude-developer-toolkit.git .claude/skills/developer-toolkit
```

### Option 3: Manual Installation

1. Download this repository
2. Copy the `skills` folder to one of these locations:
   - Global: `~/.claude/skills/`
   - Project: `.claude/skills/`

## 🚀 Usage

After installation, use any skill by mentioning it in your conversation:

```
/commit
```

or

```
Use the commit skill to create a git commit
```

### Commit

Creates conventional commits with proper formatting:

```
/commit
```

The skill will:
1. Analyze staged changes
2. Generate a conventional commit message (feat, fix, chore, etc.)
3. Format with proper scope and bullet points
4. Create the commit

### PR Review

Performs thorough code reviews comparing your branch to main:

```
/pr-review
```

Reviews include:
- Code quality and consistency checks
- Accessibility and UX concerns
- Type safety and anti-patterns
- Edge cases and potential bugs
- Suggestions for improvement

### Implement

Guides feature implementation with best practices:

```
/implement Add user authentication with OAuth
```

Ensures:
- No code duplication (DRY principles)
- Library documentation checks
- Proper package management
- Stale code removal
- Post-implementation linting and type checking

### Debug

Interactive debugging with automatic environment setup:

```
/debug Button click crashes on mobile
```

The skill will:
1. Add strategic debug logs
2. Auto-start development servers
3. Monitor logs in real-time
4. Identify and analyze issues
5. Suggest fixes

### Changelog

Generates formatted changelogs from git history:

```
/changelog v1.2.0
```

Creates organized changelog entries with:
- Changes grouped by category
- Ticket numbers extracted from commits
- User-facing descriptions

## 🔧 Customization

Each skill can be customized by editing its `SKILL.md` file. Common customizations:

- **Commit scopes**: Update the scopes in `skills/commit/SKILL.md` to match your project
- **Review focus areas**: Adjust review criteria in `skills/pr-review/SKILL.md`
- **Debug platforms**: Modify platform-specific commands in `skills/debug/SKILL.md`
- **Changelog categories**: Customize categories in `skills/changelog/SKILL.md`

## 📖 Skill Structure

Each skill follows the standard SKILL.md format:

```
skills/
├── commit/
│   └── SKILL.md
├── debug/
│   └── SKILL.md
├── implement/
│   └── SKILL.md
├── pr-review/
│   └── SKILL.md
└── changelog/
    └── SKILL.md
```

## 🤝 Contributing

Contributions are welcome! To add or improve skills:

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Test the skill in your local Claude Code setup
5. Submit a pull request

## 📄 License

MIT License - see LICENSE file for details

## 🔗 Resources

- [Claude Code Documentation](https://code.claude.com/docs)
- [Official Skills Repository](https://github.com/anthropics/skills)
- [Skills Specification](https://github.com/anthropics/skills/tree/main/spec)
- [How to Create Custom Skills](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills)

## 🙏 Acknowledgments

Skills are designed to work with Claude Code CLI and follow the Agent Skills specification.

---

Made with ❤️ for the Claude Code community
