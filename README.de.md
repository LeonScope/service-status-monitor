# Scope Monitor · Service Status Monitor

**Eine Projektpräsentation von [LeonScope](https://github.com/LeonScope)**  
Full-Stack Developer · AI-Assisted Product Builder

[English](README.md) · [Fallstudie](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md)

Sehen, wie Dienste antworten, ihre Prüfungen nachverfolgen und Störungen bis zur bestätigten Erholung begleiten. Scope Monitor verbindet regelmäßige HTTP-Prüfungen, gespeicherte Messwerte und eine responsive Oberfläche. **Der Anwendungscode bleibt privat.** Dieses Repository enthält ausschließlich die Projektpräsentation.

![Scope Monitor am Desktop mit ausdrücklich gekennzeichneten synthetischen Diensten und Messwerten](assets/dashboard-desktop.png)

## Was die Anwendung kann

- **Dienste überwachen:** öffentliche HTTP(S)-Adressen anlegen, Intervalle von einer, fünf oder fünfzehn Minuten wählen sowie erwarteten Status und Antwortzeitgrenze festlegen.
- **Messungen nachvollziehbar darstellen:** erreichbar, langsam, fehlerhaft, unbekannt und pausiert unterscheiden. Antwortzeiten bis zu den HTTP-Headern, den Anteil erfolgreicher Prüfungen und Lücken im Verlauf zeigen.
- **Störungen bestätigen:** zwei aufeinanderfolgende Fehler eröffnen eine Störung; zwei aufeinanderfolgende erwartete Antworten bestätigen die Erholung. Ein einzelner Fehler bleibt im Verlauf sichtbar.
- **Den Ablauf steuern:** manuell prüfen, pausieren und fortsetzen, JSON oder CSV exportieren sowie einen Monitor mit seinem Verlauf nach Bestätigung löschen.
- **Ohne Kundendaten vorführen:** ein getrennter Beispielbereich enthält sechs fiktive Dienste, simulierte Messwerte und auswählbare Ausfall- und Erholungsszenarien. Beispieladressen werden nicht aufgerufen.

## Ausgewählte Ansichten

| Störungsverlauf | Smartphone-Ansicht |
| --- | --- |
| [![Bestätigte Störung und Erholung mit getrennten Beobachtungszeitpunkten](assets/incidents-desktop.png)](assets/incidents-desktop.png) | <img src="assets/dashboard-mobile.png" width="220" alt="Responsive Scope-Monitor-Ansicht mit klar gekennzeichneten synthetischen Daten"> |

## Technische Nachweise

**72 automatisierte Anwendungstests und acht Browserabläufe bestanden in einer frisch eingerichteten lokalen Kopie.** Neuinstallation der festgeschriebenen Abhängigkeiten, TypeScript-Prüfung und Produktionsbuild waren erfolgreich. Ein gesonderter echter Abruf von `https://example.com/` lieferte HTTP 200; die Antwortheader trafen in der Prüfumgebung nach **350 ms** ein. Das ist eine einzelne Beobachtung, kein Benchmark oder Verfügbarkeitsnachweis. [Prüfbericht](docs/VERIFICATION.de.md).

Die Anwendung verwendet **TypeScript, React, Node.js, SQLite und Vite**. Transaktionen, befristete Sperren pro Monitor und Abbruchlogik schützen den Verlauf vor doppelten oder veralteten Ergebnissen. Netzwerkprüfungen kontrollieren DNS-Antworten, binden Verbindungen an geprüfte IP-Adressen und bewerten Weiterleitungen erneut. [Architektur und Entscheidungen](docs/CASE-STUDY.de.md).

## Rolle und KI-Unterstützung

LeonScope legte das Portfolioziel und die Vorgabe fest, den Anwendungscode privat zu halten. Codex schlug Umfang und Technik vor, erzeugte Implementierung, Oberfläche und Tests, führte die dokumentierten Prüfungen aus und bereitete diese Präsentation vor. Die laufende Anwendung ruft kein KI-Modell auf.

## Verfügbarkeit und Rechte

Die Überwachung läuft, solange der **lokale Server** läuft. Es gibt keine öffentlich gehostete Anwendung und keinen rund um die Uhr betriebenen Monitoringdienst. Nur das Browserfenster zu schließen beendet den lokalen Server nicht. Verpasste Prüfungen werden nicht nachgetragen. Der Erfolgsanteil beschreibt gespeicherte Einzelmessungen und keine zeitbasierte Verfügbarkeit. Benachrichtigungen sind ein **lokales Ereignisprotokoll**; es werden keine E-Mails, Webhooks oder Nachrichten versendet.

Die Screenshots zeigen synthetische Daten einschließlich Antwortzeiten und Erfolgsanteilen. Der echte HTTP-Abruf ist separat dokumentiert. Dieses Präsentationsrepository führt keine Anwendungstests auf GitHub aus und verteilt kein ausführbares Anwendungspaket.

**Es wird keine Open-Source-Lizenz oder allgemeine Erlaubnis zur Weiterverwendung des eigenen Portfolio-Materials erteilt.** Gesetzliche Rechte, GitHubs Plattformbedingungen und Rechte Dritter bleiben unberührt. [Rechtehinweis](RIGHTS.md).
