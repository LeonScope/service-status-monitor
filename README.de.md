# Scope Monitor

**BEOBACHTEN → BESTÄTIGEN → ERHOLUNG ERKENNEN**

Eine lokale Betriebsübersicht für HTTP-Dienste. Antwortverläufe verfolgen, Störungen untersuchen und die bestätigte Erholung nachvollziehen. Ein Portfolioprojekt von **[LeonScope](https://github.com/LeonScope)** mit KI-Unterstützung.

[English](README.md) · [Technische Fallstudie](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md)

![Scope Monitor als Betriebsübersicht mit sechs erfundenen Diensten und ausdrücklich simulierten Beobachtungen](assets/dashboard-desktop.png)

## Eine Störung von der ersten Beobachtung an verfolgen

| Folge | Gespeichertes Verhalten |
| :--- | :--- |
| Erste fehlgeschlagene Prüfung | Fehler im Verlauf aufbewahren. |
| Zweiter aufeinanderfolgender Fehler | Eine bestätigte Störung und einen lokalen Protokolleintrag anlegen. |
| Erste erwartete Antwort | Antwort speichern; die Störung bleibt offen. |
| Zweite aufeinanderfolgende erwartete Antwort | Erholung bestätigen und die Störung einmalig schließen. |

Unbekannte Ergebnisse unterbrechen die Bestätigungsfolge. Der Verlauf trennt den ersten beobachteten Fehler vom Zeitpunkt seiner Bestätigung. Das sind einzelne Beobachtungen, kein Nachweis exakter Ausfallgrenzen.

![Störungsansicht mit getrennten Zeitpunkten für ersten Fehler, Bestätigung und Erholung](assets/incidents-desktop.png)

## Eine Oberfläche für Zustandsänderungen

Die dunkelblaue Übersicht verwendet Cyan für Bedienelemente und Grün, Gelb sowie Rot für Ergebnisse. Kompakte Messfelder, ausgerichtete Zahlen und die hervorgehobene Zahl offener Störungen erleichtern den Überblick. Fehlende Antworten bleiben als Lücken im Verlauf erkennbar.

- **Einrichten:** öffentliche HTTP(S)-Adresse, erwarteter Status, Antwortzeitgrenze und Intervalle von einer, fünf oder fünfzehn Minuten.
- **Bedienen:** manuelle Prüfung, Pause/Fortsetzung, JSON-/CSV-Export und bestätigte Löschung einschließlich Verlauf.
- **Untersuchen:** Zeit bis zu den Antwortheadern, Erfolgsanteil gemessener Prüfungen, veraltete Beobachtungen und lokale Ereignisse.
- **Vorführen:** sechs fiktive Dienste in einem getrennten Beispielbereich, mit auswählbaren Fehler- und Erholungsszenarien. Beispieladressen werden nicht abgerufen.

<details>
<summary><strong>Betriebsübersicht auf dem Smartphone</strong> — Dienste, Messwerte und Bedienung</summary>

<img src="assets/dashboard-mobile.png" width="340" alt="Dunkle mobile Scope-Monitor-Ansicht mit simulierten Zuständen und Bedienelementen" />

</details>

## Technischer Nachweis

**TypeScript · React · Node.js · SQLite · Vite**

**72 Anwendungstests und acht Browserabläufe am 19. Oktober 2026 erneut bestanden.** Die frühere Prüfung nach frischer Installation und der gesonderte echte HTTP-Abruf bleiben mit ihrem Datum im [Prüfbericht](docs/VERIFICATION.de.md) erhalten.

Gemeinsam gespeicherte Störungswechsel, zeitlich begrenzte Sperren pro Monitor und Abbruch verhindern überlappende oder veraltete Ergebnisse im Verlauf. Anfragen kontrollieren DNS-Antworten, binden Verbindungen an eine geprüfte Adresse und prüfen Weiterleitungen erneut. [Architektur und Entscheidungen](docs/CASE-STUDY.de.md).

LeonScope legte Portfolioziel und Schutz des Quellcodes fest. Codex schlug Umfang und Technik vor, erzeugte Implementierung, Oberfläche und Tests, führte die dokumentierten Prüfungen aus und erstellte die Präsentation. Die Anwendung selbst ruft kein KI-Modell auf.

## Betriebsgrenzen

Der **lokale Server** führt Prüfungen aus, solange er läuft; ein geschlossener Browser stoppt ihn nicht. Ausgefallene Prüfungen werden nicht nachträglich erfunden. Erfolgsanteile beschreiben gespeicherte Einzelmessungen und keine zeitbasierte Verfügbarkeit. Ereignisse bleiben im lokalen Protokoll; E-Mails, Webhooks oder Chatnachrichten werden nicht versendet.

Die Screenshots enthalten simulierte Antwortzeiten, Prozentwerte und Störungen. Es gibt keinen gehosteten 24/7-Dienst, keine öffentliche Anwendungs-CI und keinen ausführbaren Download.

**Dieses Repository enthält nur Präsentationsmaterial. Der Anwendungscode bleibt privat.** Es wird keine Open-Source-Lizenz, Creative-Commons-Lizenz oder allgemeine Erlaubnis zur Weiterverwendung des eigenen Materials erteilt. Gesetzliche Rechte, GitHubs Bedingungen und Rechte Dritter bleiben unberührt. [Rechtehinweis](RIGHTS.md).
