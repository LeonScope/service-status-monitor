# Lokale Prüfergebnisse

[Übersicht](../README.de.md) · [English](VERIFICATION.md)

## Oberflächenprüfung — 19. Oktober 2026

Privater Anwendungsstand: `3fbd2706b285b5551468a8b567458cb496116d2d`. Dunkle Betriebsübersicht, besser lesbare Statusfarben, ein Tastatursprung zum Inhalt und korrigierter Hinweis: Die Prüfungen hängen vom lokalen Server ab, nicht von einem geöffneten Browser.

**72 Anwendungstests und 8 Browserabläufe bestanden**, ohne Fehler, übersprungene Tests oder Browser-Wiederholungsversuche. TypeScript-Prüfung und Produktionsbuild bestanden. Die Abläufe umfassen Desktop- und Smartphone-Ansichten bei 390 Pixeln; die Screenshots wurden aus diesem Stand erneuert und visuell geprüft.

Die Prüfungen liefen lokal auf dem überarbeiteten privaten Anwendungsstand mit getrennten Testdatenbanken. Bereits installierte Abhängigkeiten wurden wiederverwendet und nicht neu installiert. Abhängigkeitslisten und Lockfiles sind unverändert. Für diese Oberflächenrevision wird kein neuer echter HTTP-Messwert, keine erneute Abhängigkeitswarnprüfung und keine frische Installation der Abhängigkeiten behauptet.

Die folgenden Nachweise behalten ihr ursprüngliches Datum und ihren Prüfumfang.

## Frühere vollständige Prüfung — 18. Oktober 2026

Geprüft am **18. Oktober 2026** gegen die private Anwendungsversion `3f81217815d5f5011ef26bae9db87f8f9b97dea0`. Die abschließenden Prüfungen liefen in einer frischen lokalen Git-Kopie mit neu installierten, festgeschriebenen Abhängigkeiten und getrennten Testdatenbanken.

| Prüfung | Beobachtetes Ergebnis |
| --- | --- |
| Neue Installation der Abhängigkeiten | Bestanden; 29 Pakete installiert, 30 geprüft, zu diesem Zeitpunkt keine gemeldeten Schwachstellen |
| TypeScript und Produktionsbuild | Bestanden |
| Anwendungstests | **72 bestanden**, 0 fehlgeschlagen, 0 übersprungen |
| Browserabläufe | **8 bestanden**, 0 fehlgeschlagen, 0 übersprungen, 0 Wiederholungsversuche |
| Separater echter HTTP-Abruf | `https://example.com/` lieferte HTTP 200; **350 ms** bis zu den Antwortheadern am 18.10.2026 um 14:57:36 UTC |
| Speicherung | Messungen nach erneutem Öffnen der Datenbank erhalten; vollständige Löschung und Aufbewahrungsgrenzen geprüft |
| Smartphone-Layout | Ansichtsfenster 390 × 844; Übersicht, Störungen und Ereignisse ohne horizontales Überlaufen |
| Exporte und Darstellung | JSON-/CSV-Downloads kontrolliert; eingeschleustes Markup blieb wirkungsloser Text |
| Öffentliche Anwendungstests oder Hosting | Nicht durchgeführt; dieses Repository enthält nur die Präsentation |

## Geprüftes Verhalten

**Monitoringregeln:** einzelner Fehler, Bestätigung nach zwei Fehlern, Verhinderung doppelter Störungen, Erholung nach zwei erwarteten Antworten, langsame erwartete Antworten, unbekannte Ergebnisse als Unterbrechung beider Folgen, erster Fehlerzeitpunkt, Erfolgsanteil aus Einzelmessungen, fehlende Daten, Median der Antwortzeiten und veralteter Status.

**Zeitplanung und Speicherung:** fällige Prüfungen, höchstens zwei gleichzeitige Anfragen, keine überlappende Prüfung desselben Monitors, Sperren über getrennte SQLite-Verbindungen, Ablauf und Besitz einer Sperre, Pause/Löschung während einer Anfrage, Abbruch, tatsächlich ausgeführter Timer, Wartezeit zwischen manuellen Prüfungen, überfällige Dienste nach einer Betriebspause ohne erfundene Messungen, erneutes Öffnen der Datenbank, Aufbewahrungsgrenzen und abgefangene Speicherfehler. Beispieldaten werden vollständig oder gar nicht angelegt; erneutes Laden erzeugt keine Duplikate.

**Netzwerkgrenzen:** private und reservierte IPv4-/IPv6-Adressen, alternative Loopback-Schreibweisen, Beschränkungen für Protokolle, Ports, Zugangsdaten und URL-Parameter, gemischte DNS-Antworten, Weiterleitungen, Schleifen, Weiterleitungslimit sowie Abbruch einschließlich laufender DNS-Auflösung. Ein echter lokaler Socket-Test prüft Adressbindung, ursprünglichen Host, Zeitlimit und Abschluss nach den Headern ohne Warten auf den Antwortkörper. Die austauschbare Testfunktion eröffnet keine produktive Einstellung zum Umgehen der Zielprüfung.

**Schnittstelle und Oberfläche:** Anlegen, Prüfen, Pausieren, Fortsetzen und Löschen; ausdrückliche Bestätigung der Überwachung; Host-/Origin-/Herkunftsprüfung; Eingabegrenzen; Trennung eigener und simulierter Dienste; keine Auslieferung privater Quelldateien; Exporte und Entschärfung von Tabellenformeln. Acht Browserabläufe prüfen Bereichswechsel, Störung und Erholung, lokale Ereignisse, Neuladen, Pause/Fortsetzung, Downloads, Löschbestätigung und Escape, Rückmeldung für gesperrte Adressen, mobile Ansichten und wirkungslose Darstellung fremden Markups.

## Aussagegrenzen

Die automatisierten Tests verwenden kontrollierte Testdaten. Der echte HTTP-Abruf erfolgte separat und einmalig. Die 350 ms sind eine Beobachtung dieser Umgebung und kein Benchmark, Lasttest oder Verfügbarkeitsversprechen. Für diesen Abruf wurde kein dauerhafter echter Monitor angelegt.

Die Screenshots zeigen sechs fiktive Dienste und erzeugte Verläufe. Antwortzeiten, Erfolgsanteile und Störungen sind simuliert. Unbekannte und fehlende Messungen werden nicht als Erfolge gezählt. Das lokale Ereignisprotokoll verschickt keine Benachrichtigungen außerhalb der Anwendung.

Es wird kein dauerhafter öffentlicher Betrieb, keine Produktionsfreigabe, vollständige Barrierefreiheit, umfassende Browserunterstützung oder Sicherheitszertifizierung behauptet. Die Prüfungen sind begrenzte technische Nachweise und kein unabhängiger Penetrationstest. Ohne den privaten Anwendungscode und seine Abhängigkeiten lassen sich die Anwendungstests aus diesem Präsentationsrepository nicht wiederholen.

## Umgebung und Herkunft der Screenshots

macOS 26.6 · Node.js 24.19.0 · npm 11.17.0 · Chrome 155.0.8059.84 · TypeScript 5.x · React 19.2.0 · Vite 8.3.4 · Playwright 1.64.1.

Die aktuellen Screenshots stammen aus der oben beschriebenen Oberflächenprüfung vom 19. Oktober. Desktopaufnahmen verwenden ein 1440 Pixel breites Ansichtsfenster, die mobile Aufnahme 390 Pixel. Die Präsentation enthält keine Quellen, Build-Dateien, Datenbank, Zugangsdaten, Abhängigkeitspakete oder Quellcodearchive.
