---
name: debug
description: Debug applications collaboratively through strategic logging and real-time monitoring. Automatically starts development servers, adds debug logs, monitors output, and helps identify issues in running applications. Best for React Native, Expo, and web apps.
---

# Debug Application

Help debug application issues collaboratively through strategic logging and real-time monitoring.

## Usage

When you run `/debug [description]`, provide a brief description of the bug or error you're experiencing.

Example: `/debug Delete button crashes on Android when pressed`

## Process

1. **Analyze**: Understand the error and locate the relevant code
2. **Add Debug Logs**: Insert strategic `console.log` statements at key points:
   - Component lifecycle (mount/unmount)
   - User interaction handlers (button press, form submit)
   - API calls (request/response/error)
   - State updates and conditional logic
   - Navigation events

3. **Ask Platform**: Ask user which platform they want to debug (e.g., Metro only, iOS, Android, web)

4. **Auto-Start Everything** (in background with run_in_background: true):
   - Development server (e.g., `npm run start`, `npm run dev`)
   - Platform-specific builds if applicable
   - Log monitoring commands

5. **Real-Time Monitoring**:
   - **Agent**: "Debug monitoring started. Please reproduce the issue."
   - **Agent**: Continuously monitors TaskOutput from background processes
   - **User**: Reproduces the bug in the app
   - **Agent**: Automatically detects and analyzes errors/unexpected values in logs

6. **Iterate**: Add more logs or test fixes as needed

## Log Format

Use descriptive prefixes for easy filtering:

```typescript
console.log('[ComponentName] Action:', data);
console.error('[ComponentName] Error:', error);
```

## Instructions

When debugging:

1. Read the provided error/bug description
2. Locate the relevant code
3. Add strategic console.log statements
4. **CRITICAL**: Ask user which platform they want to debug
5. **AUTOMATICALLY START** the development environment (do NOT ask user to paste logs)
6. Monitor the TaskOutput of the background processes to capture logs in real-time
7. Announce: "Debug monitoring started. Please reproduce the issue."
8. As logs come in from TaskOutput, analyze them immediately for errors, unexpected values, or missing output
9. When you see the issue in the logs, provide findings with code references
10. Suggest fixes or additional logging if needed
