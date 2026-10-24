---
name: excalidraw-mcp-workflow
description: Reliable workflow for converting Mermaid diagrams into Excalidraw files using Pi's mcp tool with the excalidraw_readwrite server and browser-backed canvas. Use when creating, syncing, exporting, QA-checking, or troubleshooting Excalidraw diagrams generated through MCP.
compatibility: Requires Pi with the mcp tool enabled, an excalidraw_readwrite MCP server configured, and a browser available for the Excalidraw frontend canvas.
---

# Excalidraw MCP Workflow

Use this skill when working with Mermaid → Excalidraw conversion through Pi's `mcp` tool.

## Important: yes, this skill still uses the MCP server

A skill is **instructions**, not a replacement for tools.

This skill assumes Pi already has:
- the `mcp` tool available
- the `excalidraw_readwrite` server configured
- usually the `chrome-devtools` server available as well for browser automation / screenshots

This skill tells the agent **how to use** those tools correctly.

## Core lesson

`excalidraw_readwrite_create_from_mermaid` is **not** a pure server-side conversion.

It sends a Mermaid conversion request to the **frontend Excalidraw canvas**.

That means successful conversion depends on all of these being true:
1. the Excalidraw canvas server is running
2. the frontend is open in a browser
3. the browser page is connected to the canvas
4. the converted scene is synced back to the backend before export

If any of those are missing, you can get:
- empty exports
- diagrams that only exist in the browser tab
- valid `.excalidraw` JSON with bad viewport state
- files that appear blank on open

## Default local canvas project

If the configured `excalidraw_readwrite` server expects the standard local canvas setup, the canvas project is:

- `/Users/luketych/_/Dev/alphabetical/pi/excalidraw/excalidraw_readwrite`

Typical canvas start command:

```bash
cd /Users/luketych/_/Dev/alphabetical/pi/excalidraw/excalidraw_readwrite
npm run canvas
```

Default URL:

- `http://localhost:3000`

## Required workflow

Follow this sequence every time.

### 1. Make sure the canvas server is running

Check whether `http://localhost:3000` responds.
If not, start the canvas server.

### 2. Open the canvas in a browser

The frontend must be open before Mermaid conversion can finish.

Use a browser page at:
- `http://localhost:3000`

### 3. Prefer a fresh browser page per diagram

Do not keep reusing the same page for many conversions if you can avoid it.

This setup can hit frontend Mermaid registration issues such as:
- `Diagram flowchart-v2 already registered`

Best practice:
- open a fresh page per diagram
- or use a cache-busted URL, e.g.
  - `http://localhost:3000/?t=diagram-name-<timestamp>`

### 4. Send Mermaid through the MCP server

Use:
- `mcp` → `excalidraw_readwrite_create_from_mermaid`

Important:
- this only requests frontend conversion
- it does **not** guarantee the backend now contains the diagram

### 5. Sync the converted diagram back to the backend

After conversion, trigger **Sync to Backend** in the browser.

Do not assume the diagram is saved until this happens.

Until synced:
- `excalidraw_readwrite_query_elements`
- `excalidraw_readwrite_export_scene`

may not reflect the converted diagram correctly.

### 6. Verify the backend actually has the diagram

After syncing, confirm with MCP tools such as:
- `excalidraw_readwrite_query_elements`
- `excalidraw_readwrite_export_scene`

Do not trust the browser view alone.

### 7. Fit the viewport before export

A diagram can be valid but still open badly.

Use:
- `excalidraw_readwrite_set_viewport` with `scrollToContent: true`

This helps prevent diagrams that appear blank or badly framed when opened later.

### 8. Take a screenshot and visually inspect it

This step is mandatory.

Do **not** rely only on:
- JSON validity
- successful export
- element count

A diagram can be technically valid and still be:
- off-screen
- zoomed badly
- cramped
- overlapping
- clipped
- unreadable

### 9. Export only after QA passes

Only export `.excalidraw` after:
- conversion succeeded
- sync succeeded
- backend verification succeeded
- viewport was fitted
- screenshot looks acceptable

### 10. Name outputs clearly

Avoid ambiguous first-pass files.

Prefer names like:
- `draft-...`
- `wip-...`
- `approved-...`

Do not leave rough first-pass exports looking final.

## Quality gates

Before keeping an exported diagram, verify all of the following:

- Is the canvas server running?
- Was the frontend browser page open during conversion?
- Was this conversion done on a fresh page?
- Was **Sync to Backend** triggered after conversion?
- Does `query_elements` show the expected element count?
- Was the viewport fitted to content?
- Was a screenshot taken?
- Is the screenshot readable without manual recovery?
- Does the file open without looking blank?
- Is the filename clearly draft or final?

If any answer is "no", do not treat the export as done.

## Troubleshooting

### If the diagram does not appear after conversion

Check:
- is the canvas server running?
- is the browser page open?
- is the page connected?
- did the frontend receive the Mermaid conversion request?
- did you trigger **Sync to Backend**?

### If a diagram looks blank when opened

Likely causes:
- bad saved viewport
- content off-screen
- zoom too large or too small

Try:
- fit viewport to content
- use **Scroll back to content** in the UI if present
- re-export after fixing viewport

### If conversion starts failing after repeated runs

Likely cause:
- page reuse caused Mermaid frontend registration conflicts

Fix:
- open a fresh page with a unique query string
- rerun conversion there

## Practical repeatable process

For each diagram:

1. start or verify canvas server
2. open fresh browser page
3. run Mermaid conversion via `excalidraw_readwrite_create_from_mermaid`
4. sync to backend
5. verify elements exist in backend
6. fit viewport to content
7. take screenshot
8. inspect readability
9. export `.excalidraw`
10. keep only acceptable outputs

## What this skill does *not* do

This skill does not replace:
- the `mcp` tool
- the `excalidraw_readwrite` MCP server
- the browser frontend

It is a reusable instruction layer for using those pieces correctly.

## Recommended tool usage

When using this skill, prefer:
- `mcp` for Excalidraw server calls
- `mcp` with `chrome-devtools` for browser opening / clicking / screenshots when available
- `bash` for checking server state or starting the canvas process
- `read` for inspecting exported files if needed

## After installing this skill

Pi usually discovers skills at startup.

If Pi is already running, use:
- `/reload`

You can also force-load it with:
- `/skill:excalidraw-mcp-workflow`
