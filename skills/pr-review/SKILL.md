---
name: pr-review
description: Perform thorough code reviews with direct, technical, and constructive feedback. Checks consistency, accessibility, type safety, code quality, edge cases, and suggests improvements based on existing patterns. Reviews diffs against main branch.
---

# PR Review

Perform a thorough code review of the current branch against main with direct, technical, and constructive feedback.

## Usage

When you run `/pr-review`, it will review all changes in the current branch compared to main.

Example: `/pr-review`

## Review Philosophy

Be direct, technical, and constructive. Focus on:
- Code quality and maintainability
- Consistency with existing patterns
- Potential bugs and edge cases
- User experience implications
- Design system alignment
- Accessibility concerns

## Review Focus Areas

### 1. Consistency & Patterns
- **Actively search the codebase** using Grep for similar logic/patterns and suggest applying changes consistently
- Suggest using existing patterns instead of creating new ones
- Point out inconsistencies between similar components/functions
- Verify hardcoded values aren't already defined as constants or theme values elsewhere

### 2. Defaults & Initial Values
- Question whether default values make logical sense
- Point out confusing initial states

### 3. Accessibility & UX
- Check for accessibility issues (especially with font sizes, touch targets)
- Question design decisions that affect usability
- Verify proper screen reader support

### 4. Type Safety & Anti-Patterns
- Flag type assertions (non-null assertions and type casting) - suggest proper type narrowing instead
- Point out redundant null checks (e.g., `hasValue && value` when `hasValue` already checks `value`)
- Check if proper UI components are used

### 5. Code Simplification
- Suggest more concise or clearer ways to write the same logic
- Point out unnecessary complexity

### 6. API Design & Naming
- Suggest better function/variable names that describe intent
- Recommend using options objects instead of multiple parameters

### 7. Separation of Concerns
- Check if complex logic should be extracted into hooks
- Suggest moving modal/dialog JSX into separate components

### 8. Edge Cases & Bugs
- Identify potential runtime issues
- Check if correct data sources are used (e.g., derived vs. direct state)

### 9. Reusability & DRY
- Suggest using generic solutions when appropriate
- Check if compound component patterns would improve the API

### 10. Layout & Styling Issues
- Check for spacing/layout bugs
- Verify multi-line text handling

## Output Format

For each issue found, provide:

1. **File and line reference** (e.g., `usePendingToggle.ts:9`)
2. **Issue description** as a direct question or statement
3. **Code suggestion** when applicable (use code blocks)
4. **Reasoning** when the issue might not be obvious

Group findings by:
- 🔴 **Critical**: Bugs, accessibility issues, major inconsistencies
- 🟡 **Important**: Code quality, maintainability, patterns
- 🟢 **Suggestions**: Nice-to-haves, minor improvements, nitpicks

## Example Review Comments

**Good examples:**

✅ "Can you apply this inside BiometricsListItem as well? That one contains similar logic. Look for: `const [isEnabling, setIsEnabling] = useState(false);`"

✅ "I would let this default to `false`. That is a lot more logical?"

✅ "Do we ever want this to be 1 by default (I know this was the default before your changes)? This especially makes things unreadable if you bump font sizes."

✅ "I don't like that we opened up components to infinite customizations like this. I suggest to set a specific prop on the component instead."

✅ "Wouldn't a better name for `setSubscribedTopic` be `onSubscribedToTopic`?"

✅ "Nit-picky but can be written shorter/nicer like this: `showClaimNotificationsBottomSheet(openClaimFlow);`"

✅ "This color `#1E3A8A` is already defined as `theme.colors.primary.dark` - use that instead?"

✅ "This spacing value `16` appears 4 times in this file. Consider extracting it as a constant?"

✅ "You can remove `&& lifeProtectionRequestData.manualPaymentDetails` since that is checked by `hasManualPaymentDetails` 😉"

✅ "Can you offload the logic to show the bottom sheet into a hook and move the bottom sheet JSX into a separate component. This would be consistent with how it is done currently."

✅ "To check if we can use `lastUsedCurrencyCode` of the `wizardSettings` here as a fallback."

## Instructions

1. Get the diff: `git diff main...HEAD`
2. Read key changed files to understand context
3. Check for similar patterns in the codebase
4. Consider user experience and accessibility
5. Look for edge cases and potential bugs
6. Suggest improvements using existing patterns
7. Be direct but constructive

Focus on providing actionable feedback that improves code quality and maintainability.
