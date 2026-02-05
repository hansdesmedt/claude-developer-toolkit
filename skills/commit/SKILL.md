---
name: commit
description: Create git commits with conventional commit format. Analyzes staged changes and generates clear, structured commit messages following conventional commits specification with type, scope, and detailed bullet points.
---

# Commit Changes

Create a git commit with a clear message following the conventional commits format used in this repository.

## Usage

When you run `/commit`, the assistant will analyze your changes and create an appropriate commit message.

Example: `/commit`

## Commit Message Format

Follow the conventional commits format:

```
type(scope): brief description

- Detail 1
- Detail 2
- Detail 3
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `chore`: Maintenance tasks
- `refactor`: Code refactoring
- `docs`: Documentation changes
- `test`: Test updates
- `ci`: CI/CD changes

**Scopes:**
- Use project-specific scopes based on the repository structure
- Check existing commits for scope conventions: `git log --oneline -20`

## Guidelines

1. Keep the summary line under 72 characters
2. Use lowercase for the description
3. Be specific but concise
4. Add bullet points for details when multiple changes are involved
5. Focus on what changed, not why (unless the change is complex)

## Commit Format

Use heredoc format for clean multi-line messages:

```bash
git commit -m "$(cat <<'EOF'
feat(app): add user profile settings

- Implement profile edit form with validation
- Add avatar upload functionality
- Update user preferences API integration
EOF
)"
```

## Instructions

When creating a commit:

1. Run `git status` and `git diff --staged` to understand the changes
2. Analyze the scope and nature of the changes
3. Draft a commit message following the format above
4. Stage all changes with `git add -A` (if not already staged)
5. Create the commit using the heredoc format
6. Do NOT include "Co-Authored-By" attribution
7. Show the commit message to the user for confirmation
