# Freda Ops Cockpit — Beta 0.2.31

This package keeps the 0.2.23 reporting.site busy-hours POST parser and adds forced Playwright/Chromium browser diagnostics for Render connection resets.

## Main purpose

Reporting.site may reset Render server-side requests with `ECONNRESET`. Beta 0.2.31 adds a browser-only POS sync, one-store diagnostics, and direct browser-runtime extraction for Busy Hours chart data so hourly rows can be recovered from rendered reporting.site pages.

## Render build

```text
Root Directory: server
Build Command: npm install && npx playwright install chromium
Start Command: node server.js
Health Check Path: /health
```

## Key endpoints

```text
/health
/api/config/status
/api/diagnostics/browser-sync
/api/sync/pos/day-browser
/api/sync/pos/day-browser-store
/api/sync/pos/day
/api/sync/pos/benchmarks
```

## Notes

- POS remains sync-first from reporting.site; uploaded POS files are backup only.
- Uber, Frieda/Square and production still use uploaded files unless explicitly synced.
- Do not commit real cookies, session IDs or API keys.

## Beta 0.2.31 notes

V30 is the first package where the front-end Sync POS buttons are wired to the working browser POS path. It also forces the selected reporting date using browser-context POST requests before falling back to normal page navigation. Stores are synced sequentially and saved after each store.

Render build command remains:

```bash
npm install && npx playwright install chromium
```
