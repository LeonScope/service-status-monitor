# Scope Monitor

### HTTP-Dienste prüfen und Störungen nachvollziehen

Scope Monitor prüft in regelmäßigen Abständen, ob HTTP-Dienste antworten. Die Übersicht zeigt den letzten Status und die bisherigen Antwortzeiten. Schlagen zwei Prüfungen hintereinander fehl, wird eine Störung angelegt. Zwei erwartete Antworten in Folge bestätigen, dass der Dienst wieder antwortet.

[English](README.md) · [Technische Fallstudie](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md)

![Scope Monitor als Betriebsübersicht mit sechs erfundenen Diensten und ausdrücklich simulierten Beobachtungen](assets/dashboard-desktop.png)

## Wann eine Störung entsteht

| Prüfung | Was passiert |
| :--- | :--- |
| Erste fehlgeschlagene Prüfung | Fehler im Verlauf aufbewahren. |
| Zweiter aufeinanderfolgender Fehler | Eine bestätigte Störung und einen lokalen Protokolleintrag anlegen. |
| Erste erwartete Antwort | Antwort speichern; die Störung bleibt offen. |
| Zweite aufeinanderfolgende erwartete Antwort | Erholung bestätigen und die Störung einmalig schließen. |

Ein unbekanntes Ergebnis unterbricht die Folge. Im Verlauf steht deshalb sowohl der erste beobachtete Fehler als auch der Zeitpunkt der Bestätigung. Wann der Ausfall tatsächlich begonnen hat, lässt sich aus einzelnen Prüfungen nicht genau bestimmen.

![Störungsansicht mit getrennten Zeitpunkten für ersten Fehler, Bestätigung und Erholung](assets/incidents-desktop.png)

## Mit dem Monitor arbeiten

Die Übersicht zeigt erreichbare, langsame, fehlerhafte, unbekannte und pausierte Dienste getrennt. Ein Klick auf einen Dienst öffnet seine Messwerte und Prüfregeln. Fehlt eine Antwort, bleibt im Diagramm eine Lücke.

- **Einrichten:** öffentliche HTTP(S)-Adresse, erwarteter Status, Antwortzeitgrenze und Intervalle von einer, fünf oder fünfzehn Minuten.
- **Bedienen:** manuelle Prüfung, Pause/Fortsetzung, JSON-/CSV-Export und bestätigte Löschung einschließlich Verlauf.
- **Untersuchen:** Zeit bis zu den Antwortheadern, Erfolgsanteil gemessener Prüfungen, veraltete Beobachtungen und lokale Ereignisse.
- **Vorführen:** sechs fiktive Dienste in einem getrennten Beispielbereich, mit auswählbaren Fehler- und Erholungsszenarien. Beispieladressen werden nicht abgerufen.

<details>
<summary><strong>Betriebsübersicht auf dem Smartphone</strong> — Dienste, Messwerte und Bedienung</summary>

<img src="assets/dashboard-mobile.png" width="340" alt="Dunkle mobile Scope-Monitor-Ansicht mit simulierten Zuständen und Bedienelementen" />

</details>

## Umsetzung und Tests

**TypeScript · React · Node.js · SQLite · Vite**

Am 19. Oktober 2026 bestanden erneut **72 Anwendungstests und acht Browserabläufe**. Im [Prüfbericht](docs/VERIFICATION.de.md) stehen die einzelnen Testbereiche sowie die Neuinstallation und der separate echte HTTP-Abruf vom 18. Oktober.

Messwert, Störungswechsel und Protokolleintrag werden gemeinsam gespeichert. Eine laufende Prüfung darf nach dem Pausieren oder Löschen eines Monitors keine veralteten Ergebnisse mehr eintragen. Auch DNS-Adressen und Weiterleitungen werden vor dem Abruf geprüft. Die [Fallstudie](docs/CASE-STUDY.de.md) erklärt diese Entscheidungen genauer.

Ich habe das Projekt als nächsten Baustein meines Portfolios ausgewählt und den Umfang begleitet. Codex erstellte die Umsetzung, Oberfläche, Tests und Dokumentation und führte die Prüfungen aus. Der Monitor selbst arbeitet ohne KI-Modell.

## Lokaler Betrieb

Die Prüfungen laufen auf dem **lokalen Server**. Der Browser kann dabei geschlossen sein. Ist der Server ausgeschaltet, entstehen keine Messungen; diese Lücken werden später auch nicht aufgefüllt. Der angezeigte Erfolgsanteil bezieht sich auf gespeicherte Prüfungen, nicht auf die gesamte Betriebszeit. Meldungen bleiben im lokalen Protokoll. E-Mail-, Webhook- und Chatbenachrichtigungen sind nicht eingebaut.

Die Screenshots enthalten simulierte Antwortzeiten, Prozentwerte und Störungen. Es gibt keinen gehosteten 24/7-Dienst, keine öffentliche Anwendungs-CI und keinen ausführbaren Download.

**Hier wird nur das Projekt vorgestellt. Der Anwendungscode bleibt privat.** Für das eigene Material wird keine Open-Source- oder Creative-Commons-Lizenz und keine allgemeine Nutzungserlaubnis erteilt. [Rechtehinweis](RIGHTS.md).
