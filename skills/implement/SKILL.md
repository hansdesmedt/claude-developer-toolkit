---
name: implement
description: Implement features following critical development guidelines. Ensures thorough codebase analysis, library documentation checks, DRY principles, proper package management, and post-implementation validation with linting and type checking.
---

# Implement Feature

Apply critical development guidelines when implementing code changes. This command ensures thorough analysis, library documentation checks, and adherence to best practices.

## Usage

When you run `/implement [description]`, provide a brief description of the feature you want to implement.

Example: `/implement Add user profile deletion with confirmation modal`

## Code Quality Guidelines

1. **Avoid Duplicated Code**
   - Extract common logic into reusable functions or hooks
   - Keep code readable and maintainable
   - Follow DRY (Don't Repeat Yourself) principles
   - Use shared utilities when applicable

2. **Library Documentation**
   - When debugging or implementing features with external libraries, ALWAYS check the official online documentation first
   - Verify API usage and best practices from the source
   - Use WebFetch or WebSearch to access current documentation

3. **Deep Analysis**
   - Do a thorough deep dive into the codebase before implementing changes
   - Understand the full context and existing patterns

4. **Package Management**
   - **CRITICAL**: Always remove the `~` prefix in package.json when adding new packages
   - Use exact versions or `^` for semantic versioning, never `~`
   - Example: Use `"package": "1.2.3"` or `"package": "^1.2.3"`, NOT `"package": "~1.2.3"`

5. **Remove Stale Code**
   - After implementing a feature, check if any old components, screens, or files are now unused
   - Search for imports of components that might have been replaced
   - Remove unused files, imports, route registrations, and any related configurations
   - Keep the codebase clean by eliminating dead code

## Post-Implementation Validation

After generating code, ALWAYS run:

```bash
npm run lint
npm run typecheck
```

Fix any errors before marking the task as complete.

## Instructions

When implementing changes:

1. Read and understand existing code patterns
2. Check library documentation if using external libraries
3. Write clean, maintainable code without duplication
4. Ensure package.json has correct version prefixes
5. Check for and remove any stale/unused files replaced by the new implementation
6. Run lint and typecheck
7. Fix all errors and warnings
8. Verify the implementation meets all requirements
