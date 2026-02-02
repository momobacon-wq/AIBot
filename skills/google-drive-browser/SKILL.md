# Google Drive (Browser Mode)

Access Google Drive file lists using the connected browser session (no API credentials required).

## Capabilities

- **List Files**: View files in "My Drive".
- **Search**: Use the browser's search bar to find specific files.

## Usage

### List Files

1. **Open Drive**:
   ```javascript
   browser.action({ action: "open", profile: "chrome", targetUrl: "https://drive.google.com/drive/my-drive" })
   ```
2. **Snapshot**:
   ```javascript
   browser.action({ action: "snapshot", targetId: "<targetId>" })
   ```
   (The file list is in the `grid "項目清單"` or `rowgroup` elements).

### Search

1. **Type Query**:
   Click the search box (`textbox "在雲端硬碟中搜尋"`) and type the query.
2. **Submit**:
   Press Enter or click the search button.

## Requirements

- **Chrome Browser**: Must be running with the OpenClaw extension active.
- **Logged In**: The user must be already logged into Google Drive in that browser profile.
