# Validation

- Production build: passed (Next.js 16.3.6).
- Strict TypeScript checking: passed.
- Unit/adapter tests: 6 passed.
- Browser tests: 6 passed across desktop 1440px and mobile 390px, using installed Microsoft Edge through Playwright.
- Desktop workspace, brief, graph, and mobile screenshots reviewed.
- Full flow preserves the original question, creates a labeled brief, downloads text, survives session reload, and filters the chart.
- Unsupported questions show no evidence or expert; empty search, unavailable voice, and Escape dismissal checked.
- API error and malformed-response behavior checked with mocked responses. No live backend was available.

Actual microphone capture and synthetic speech audio were not manually verified. These remain browser-dependent optional capabilities with typed/readable fallbacks.

For Edge-based checks on Windows Command Prompt: `set PLAYWRIGHT_CHANNEL=msedge` then `pnpm test:e2e`. Otherwise install Playwright Chromium as described in the README.
