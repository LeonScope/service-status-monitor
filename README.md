# Scope Monitor

**OBSERVE → CONFIRM → RECOVER**

A local operations console for HTTP services. Follow response history, investigate an incident and see when recovery was confirmed. An AI-assisted portfolio project by **[LeonScope](https://github.com/LeonScope)**.

[Deutsch](README.de.md) · [Engineering case study](docs/CASE-STUDY.md) · [Verification record](docs/VERIFICATION.md)

![Scope Monitor operations console with six fictional services and explicitly simulated observations](assets/dashboard-desktop.png)

## Follow an incident from the first observation

| Sequence | Recorded behavior |
| :--- | :--- |
| First failed check | Preserve the failure in the history. |
| Second consecutive failure | Open one confirmed incident and a local journal entry. |
| First expected response | Record the response; the incident remains open. |
| Second consecutive expected response | Confirm recovery and resolve the incident once. |

Unknown results interrupt the confirmation sequence. The timeline distinguishes the first observed failure from the time it was confirmed. These are sampled observations, not proof of exact outage boundaries.

![Incident view with separate first-failure, confirmation and recovery timestamps](assets/incidents-desktop.png)

## An interface for observing change

The dark blue console uses cyan for controls and green, amber and red for outcomes. Compact measurements, aligned numbers and a highlighted incident count make the current state easy to scan. Missing responses remain gaps in the history.

- **Configure:** public HTTP(S) endpoint, expected status, response-time threshold and a one-, five- or fifteen-minute interval.
- **Operate:** manual check, pause/resume, JSON/CSV export and confirmed deletion with associated history.
- **Inspect:** response-header timing, sample-based success ratios, stale observations and local events.
- **Demonstrate:** six fictional services in a separate example workspace, with selectable failure and recovery scenarios. No example address is fetched.

<details>
<summary><strong>Mobile operations view</strong> — services, measurements and controls</summary>

<img src="assets/dashboard-mobile.png" width="340" alt="Dark mobile Scope Monitor console with simulated service states and monitoring controls" />

</details>

## Engineering record

**TypeScript · React · Node.js · SQLite · Vite**

**72 application tests and eight browser workflows passed again on 19 October 2026.** The earlier clean-install check and separate real HTTP observation remain dated in the [verification record](docs/VERIFICATION.md).

Transactional incident updates, per-monitor leases and cancellation prevent overlapping or obsolete results from corrupting history. Requests validate DNS answers, pin connections to an approved address and revalidate redirects. [Architecture and decisions](docs/CASE-STUDY.md).

LeonScope set the portfolio objective and private-source requirement. Codex proposed the scope and technology, generated the implementation, interface and tests, performed the documented checks and prepared the presentation. The application itself does not call an AI model.

## Operating boundary

The **local server** performs checks while it is running; closing the browser does not stop it. Missed checks are not backfilled. Success ratios describe recorded samples, not duration-based uptime. Events stay in the local journal; no email, webhook or chat notifications are sent.

Screenshots contain simulated response times, percentages and incidents. There is no hosted 24/7 service, public application CI or executable download.

**This repository contains presentation material only. Application source remains private.** No open-source license, Creative Commons license or general reuse permission is granted for original material. Statutory rights, GitHub terms and third-party rights remain unaffected. [Rights notice](RIGHTS.md).
