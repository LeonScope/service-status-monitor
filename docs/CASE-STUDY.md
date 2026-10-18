# Case study · Scope Monitor

[Overview](../README.md) · [Deutsch](CASE-STUDY.de.md) · [Verification](VERIFICATION.md)

## Problem and outcome

An HTTP failure is an observation, not necessarily an outage. A useful monitoring tool needs to preserve evidence, show uncertainty and make status changes understandable. Scope Monitor implements that workflow in a small local application: checks, confirmation, incident history and recovery, with explicit controls for pause, manual checks and export.

The first version is complete as a locally verified portfolio project. It is not a managed monitoring service. Source code and implementation history remain private.

## The main decisions

| Decision | Reason and observable behavior |
| --- | --- |
| Confirm with two consecutive checks | One transient failure does not open an incident. Two failures open one incident and one journal entry; two expected responses resolve it once. |
| Preserve unknown outcomes | Policy-blocked or internally failed checks do not become successful observations. Unknown results break confirmation streaks and never resolve an open incident. |
| Separate observations from uptime | Success is calculated from successful versus failed samples over the available 24-hour window, excluding unknowns. There is no invented success for missing data. |
| Separate first failure and confirmation | The timeline records first observed failure, confirmed incident and confirmed recovery. Actual outage boundaries may lie between checks. |
| Store state in SQLite | Checks, incident transitions and event entries commit together. A unique constraint prevents multiple open incidents for one service. |
| Invalidate obsolete work | Pause/resume changes the monitor generation and invalidates its lease. Deleted monitors cannot receive late results. |
| Run a bounded local scheduler | One-, five- or fifteen-minute intervals, at most two simultaneous checks in the process, 30-second leases and a six-second request budget. Restart checks due services without backfilling. |
| Isolate synthetic examples | Six fictional services use the same persistence and confirmation rules as real probes, but their network responses are simulated. They never enter the own-services totals. |

## Architecture

```mermaid
flowchart LR
    UI[React dashboard] --> API[Local HTTP API]
    API --> DB[(SQLite)]
    API --> Engine[Scheduler and manual checks]
    Engine --> Probe[Bounded HTTP probe]
    Probe --> Target[Approved public endpoint]
    Engine --> Example[Explicitly simulated response]
    Probe --> Transition[Transactional state transition]
    Example --> Transition
    Transition --> DB
    DB --> Export[JSON and CSV]
    DB --> Journal[Local event journal]
```

The server binds to loopback and checks Host and Origin on requests. Target validation blocks private/reserved addresses, nonstandard ports, embedded credentials and query parameters. Every DNS answer must be public; the chosen address is pinned to the connection, while the original hostname is retained. Redirect targets are validated again. Connections stop after the response headers arrive.

The history chart uses actual sample timestamps and leaves missing responses and long gaps disconnected. The interface distinguishes the most recent observed state from a stale result. Exports preserve the data source and neutralize spreadsheet-formula prefixes in CSV cells.

## Scope and limitations

The local server must stay running; no operating-system background service is installed. A sleeping or stopped computer produces gaps. The browser is not the scheduler. DNS failures and TLS errors are observations from this machine and do not establish a global outage.

The application allows up to 20 monitors. Check history is capped at 2,000 samples per monitor, with data older than seven days pruned on subsequent recording. Closed incident history and the local event journal are also bounded. No authenticated endpoints, custom ports, browser transactions, distributed probes, email delivery or external incident-management integration are included.

This application measures time to response headers, including DNS, TLS and redirects. It does not measure full page load, application correctness, certificate expiry or duration-based uptime. The synthetic example's percentages and timings are not performance claims.

## Role and evidence

LeonScope commissioned the project and selected the portfolio and privacy constraints. Codex generated the implementation, design, tests and documentation and performed the recorded verification. The project demonstrates AI-assisted product development and testable monitoring behavior; it does not claim an independently hand-written implementation or AI inference inside the product.

[72 application tests and eight browser workflows](VERIFICATION.md) passed in a fresh local installation. The public material includes the scope and results, not the private source needed to rerun those tests.
