# Scope Monitor · Service Status Monitor

**A project presentation by [LeonScope](https://github.com/LeonScope)**  
Full-Stack Developer · AI-Assisted Product Builder

[Deutsch](README.de.md) · [Case study](docs/CASE-STUDY.md) · [Verification](docs/VERIFICATION.md)

See how services respond, follow their check history and trace an incident through confirmed recovery. Scope Monitor combines scheduled HTTP checks, persistent observations and a responsive dashboard. **Application source remains private.** This repository contains presentation material only.

![Scope Monitor desktop dashboard with explicitly marked synthetic services and observations](assets/dashboard-desktop.png)

## What the application does

- **Monitor services:** add public HTTP(S) endpoints, choose a one-, five- or fifteen-minute interval, set an expected status and a response-time threshold.
- **Keep observations honest:** distinguish reachable, slow, failed, unknown and paused states. Show response-header timing, sample-based success ratios and gaps in the history.
- **Confirm incidents:** two consecutive failed checks open an incident; two consecutive expected responses confirm recovery. A single failure remains visible without opening an incident.
- **Control the workflow:** run a manual check, pause/resume monitoring, export JSON or CSV and delete a monitor with its history.
- **Demonstrate without customer data:** a separate example workspace contains six fictional services, simulated samples and selectable failure/recovery scenarios. No example domain is fetched.

## Selected views

| Incident history | Mobile dashboard |
| --- | --- |
| [![Confirmed incident and recovery with distinct observation timestamps](assets/incidents-desktop.png)](assets/incidents-desktop.png) | <img src="assets/dashboard-mobile.png" width="220" alt="Responsive Scope Monitor dashboard with clearly marked synthetic data"> |

## Engineering evidence

**72 automated application tests and eight browser workflows passed in a fresh local copy.** A clean dependency installation, TypeScript check and production build passed. One separate real request to `https://example.com/` returned HTTP 200 in **350 ms to response headers** in the verification environment. This is one observation, not a benchmark or availability claim. [Verification details](docs/VERIFICATION.md).

Built with **TypeScript, React, Node.js, SQLite and Vite**. Transactional incident transitions, per-monitor leases and cancellation protect the history from overlapping or obsolete results. Requests validate DNS answers, pin the connection to an approved address and revalidate redirects. [Architecture and decisions](docs/CASE-STUDY.md).

## Role and AI assistance

LeonScope set the portfolio objective and the requirement to keep source private. Codex proposed the scope and technology, generated the implementation, interface and tests, ran the documented checks and prepared this presentation. The running application does not call an AI model.

## Availability and rights

Monitoring runs while the **local server** is running. There is no hosted application or 24/7 monitoring service. Closing only the browser does not stop the local server. Missed checks are not backfilled, and the success ratio describes recorded samples rather than duration-based uptime. Notifications are a **local event journal**; no emails, webhooks or chat messages are sent.

The screenshots use synthetic data, including their response times and success ratios. Real HTTP verification is documented separately. This presentation repository does not run application tests on GitHub and does not distribute an executable package.

**No open-source license or general reuse permission is granted for the original portfolio material.** Applicable law, GitHub's platform terms and third-party rights remain unaffected. [Rights notice](RIGHTS.md).
