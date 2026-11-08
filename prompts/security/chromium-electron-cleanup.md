# chromium and electron cleanup
- category: security
- post link: https://x.com/dave_deguzza/status/2117561292936606163
- description: A Claude Code prompt from @dave_deguzza that deletes old Playwright/Puppeteer Chromium builds, sandboxes the Playwright MCP onto system Chrome, and audits Electron app versions.

## prompt

```text
Find every Playwright/Puppeteer browser cache on this machine and delete the Chromium builds older than 156.0.8078.73. Then edit the Playwright MCP config to add --browser chrome --sandbox so it uses my auto-updated system Chrome. Also grep every Electron app in AppData for its Chrome/ Electron/ version string and tell me which ones are below Electron 43.8.6 / 44.10.1 / 45.2.1.
```

edits: removed the surrounding quotation marks and the author's intro and outro.
