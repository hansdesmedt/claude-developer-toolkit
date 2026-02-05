---
name: changelog
description: Generate changelog entries from git commits since a specified reference. Formats changes by category with ticket numbers. Pass a git reference (branch, tag, or commit) as argument to compare against.
---

# Generate Changelog

Write a changelog of the changes on main since the specified reference.

## Usage

When you run `/changelog [reference]`, provide a git reference (branch name, tag, or commit hash) to compare against.

Example: `/changelog v1.2.0`
Example: `/changelog main`
Example: `/changelog abc123`

## Format

Use the format below, organizing changes by logical categories. Try to include ticket numbers if available in commit messages:

```md
## Category 1

- TICKET-123: add change password functionality
- TICKET-124: update user profile validation

## Category 2

- TICKET-125: fix issue with preview mode
- TICKET-126: resolve navigation bug on iOS
```

## Instructions

When generating a changelog:

1. Get commits since the reference: `git log [reference]..HEAD --oneline`
2. Read commit messages and organize by category
3. Extract ticket numbers from commit messages (e.g., JIRA-123, PROJ-456)
4. Group related changes together
5. Use clear, user-facing language
6. Format each entry as: `TICKET-XXX: description`

## Categories

Choose appropriate categories based on your project. Common examples:
- Features
- Bug Fixes
- Performance
- Documentation
- Dependencies
- Breaking Changes
