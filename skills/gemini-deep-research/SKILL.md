# Gemini Deep Research

Automates the process of opening Google Gemini, activating the Deep Research feature, submitting a query, and starting the research process.

This process is highly reliant on the stability of the browser connection (Chrome Extension Relay).

## Usage

**Goal**: Ask Gemini a question and use its deep research mode.

### Steps (Automated Sequence)

1.  **Open Gemini**:
    ```javascript
    browser.action({ action: "open", profile: "chrome", targetUrl: "https://gemini.google.com/app" })
    ```
2.  **Activate Deep Research**:
    *   Click the **Tools** button (ref `e132` in new session snapshots).
    *   Click the **Deep Research** menu item (ref `e166` in menu snapshot).
    ```javascript
    browser.action({ action: "act", request: { kind: "click", text: "工具" } }) // Open Tool Menu
    browser.action({ action: "act", request: { kind: "click", text: "Deep Research" } }) // Click Deep Research
    ```
3.  **Input Query & Generate Plan**:
    *   Type the research query into the prompt textbox (ref `e207` in Deep Research Mode snapshot).
    ```javascript
    browser.action({ action: "act", request: { kind: "type", ref: "e207", text: "<query>" } })
    browser.action({ action: "act", request: { kind: "press", key: "Enter" } })
    ```
4.  **Start Research**:
    *   Wait for the plan to load.
    *   Click the **開始研究** (Start Research) button (ref `e159` in plan snapshot).
    ```javascript
    browser.action({ action: "act", request: { kind: "click", text: "開始研究" } })
    ```

**Note**: Due to the aggressive anti-automation nature of Gemini's UI, frequent `snapshot` calls and explicit `targetId` usage (which is handled internally by OpenClaw if the session is active) are necessary, but manual intervention may sometimes be required due to page refreshes or 'tab not found' errors.
