# Local verification

[Overview](../README.md) · [Deutsch](VERIFICATION.de.md)

Verified on **18 October 2026** against private application revision `3f81217815d5f5011ef26bae9db87f8f9b97dea0`. Final checks ran in a fresh local Git clone with a clean lockfile installation and isolated test databases.

| Check | Observed result |
| --- | --- |
| Clean dependency installation | Passed; 29 packages installed, 30 audited, no reported vulnerabilities at that time |
| TypeScript and production build | Passed |
| Application suite | **72 passed**, 0 failed, 0 skipped |
| Browser suite | **8 passed**, 0 failed, 0 skipped, 0 retries |
| Separate real HTTP check | `https://example.com/` returned HTTP 200; **350 ms** to response headers at 2026-10-18 14:57:36 UTC |
| Persistence | Database reopen preserved observations; deletion cascades and bounded retention tested |
| Mobile layout | 390 × 844 viewport; dashboard, incidents and events had no horizontal overflow |
| Exports and rendering | JSON/CSV downloads inspected; injected markup remained inert text |
| Public application CI or hosting | Not performed; this repository is presentation only |

## Covered behavior

**Monitoring rules:** isolated failure, two-failure confirmation, duplicate suppression, two-response recovery, slow-but-expected responses, unknown breaking both streaks, correct first-failure timestamp, sample-based ratios, no-data values, median response timing and stale status.

**Scheduling and persistence:** due checks, the two-request concurrency limit, per-monitor overlap prevention, cross-connection SQLite leases, lease expiry and ownership, pause/delete during a pending request, cancellation, a real periodic timer tick, manual-check cooldown, restart-style overdue scheduling without invented history, database reopen, check/incident/event retention and contained storage failure. Synthetic example creation is atomic, idempotent and capacity-limited.

**Network boundaries:** private/reserved IPv4 and IPv6, alternate loopback notations, schemes/ports/credentials/query restrictions, mixed DNS answers, redirect validation, loops and depth, cancellation and DNS lookup cancellation. A real loopback socket fixture verifies connection pinning, original Host, timeout and completion after headers without waiting for the body. Test-only dependency injection does not create a production bypass setting.

**API and interface:** create/check/pause/resume/delete, explicit monitoring permission, Host/Origin/cross-site checks, input limits, live/example separation, source-file exclusion, JSON/CSV export and spreadsheet-formula escaping. Eight browser workflows cover workspace switching, incident confirmation and recovery, local events, reload persistence, pause/resume, export downloads, delete confirmation and Escape, blocked-target feedback, mobile layouts and inert rendering of untrusted labels.

## What the evidence does not claim

Automated tests use controlled fixtures; the real HTTP request is separate and was performed once. The 350 ms result is an observation from this environment, not a benchmark, load test or availability guarantee. No persistent real monitor was created for that check.

The screenshots show six fictional services and generated history. Their response times, success ratios and incidents are synthetic. Unknown and absent measurements are not counted as successes. The local event journal sends no notifications outside the application.

There is no claim of continuous public operation, production readiness, complete accessibility compliance, broad browser coverage or security certification. Network and application checks are scoped engineering verification, not an independent penetration test. The public repository cannot reproduce private application tests because it does not contain the code or dependencies.

## Environment and screenshot provenance

macOS 26.6 · Node.js 24.19.0 · npm 11.17.0 · Chrome 155.0.8059.84 · TypeScript 5.x · React 19.2.0 · Vite 8.3.4 · Playwright 1.64.1.

Screenshots were captured by the passing browser workflows in the fresh copy and visually reviewed. Desktop captures use a 1440-pixel-wide viewport; mobile uses 390 pixels. The presentation contains no source, build output, database, credentials, dependency bundle or source archive.
