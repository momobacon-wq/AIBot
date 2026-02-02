# Browser Cleanup

Clean up browser tabs to free up memory and declutter the workspace.

## Capabilities

- **Close All Tabs**: Close all open tabs in the connected browser profile.
- **Close Specific Tabs**: Close tabs by target ID (internal use).
- **Cleanup Background Tabs**: (Manual implementation required) Identify and close tabs that are not "active" or "focused".

## Usage

### Close All Tabs (Reset)

To close all tabs that OpenClaw is currently attached to:

```javascript
// 1. Get list of all tabs
const tabs = await browser.action({ action: "tabs" });

// 2. Loop and close each one
for (const tab of tabs) {
  await browser.action({ action: "close", targetId: tab.targetId });
}
```

### Best Practice for Memory Management

When finishing a complex task (like deep research or multiple file lookups):
1.  Run `browser.action({ action: "tabs" })` to see what's open.
2.  Close the ones that are no longer needed.
3.  This prevents the "Tab not found" errors and keeps the bridge stable.
