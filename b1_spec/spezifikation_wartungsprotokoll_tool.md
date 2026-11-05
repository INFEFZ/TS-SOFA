|                      |                           |                               |
| -------------------- | ------------------------- | ----------------------------- |
| **HF Systemtechnik** | **Softwareentwicklung A** | ![logo](../x_gitres/logo.png) |

# Musterbeispiel – Spezifikation "Wartungsprotokoll-Tool"

## Kopfdaten

|                       |                                     |
| --------------------- | ----------------------------------- |
| **Projekt / Produkt** | Wartungsprotokoll-Tool              |
| **Auftraggeber/-in**  | Leiter Instandhaltung, Werk Lengnau |
| **Autor/-in**         | [Platzhalter – Ihr Name]            |
| **Datum**             | [Platzhalter]                       |
| **Version**           | 1.0                                 |

---

## 1. Ausgangslage

Wartungsarbeiten an den Produktionsmaschinen werden aktuell auf Papierformularen dokumentiert, die anschliessend in einem Ordner abgelegt werden. Dadurch ist es schwierig, den Wartungsverlauf einer bestimmten Maschine schnell einzusehen oder auszuwerten, wann eine Maschine zuletzt gewartet wurde. Die Instandhaltungsleitung wünscht sich ein einfaches digitales Tool, mit dem Wartungstechniker/-innen Einträge direkt am PC erfassen und frühere Einträge pro Maschine einsehen können.

> **Warum das funktioniert:** Die Ausgangslage beantwortet in wenigen Sätzen **Warum** und **Wer** (W-Fragen-Technik, Kapitel 1.5) – sie beschreibt das Problem (Papierformulare, schwer auswertbar), ohne bereits eine technische Lösung vorwegzunehmen. Das ist wichtig: Eine Ausgangslage sollte nie bereits "Wie" vorgeben.

---

## 2. Funktionale Anforderungen

| **#** | **Priorität**         | **Anforderung**                                                                                                 |
| ----- | --------------------- | --------------------------------------------------------------------------------------------------------------- |
| FA1   | Must                  | Ein/e Techniker/-in kann einen neuen Wartungseintrag (Maschine, Datum, durchgeführte Arbeit, Name) erfassen.    |
| FA2   | Must                  | Alle bisherigen Einträge zu einer ausgewählten Maschine können in chronologischer Reihenfolge angezeigt werden. |
| FA3   | Should                | Einträge können nach Datum gefiltert werden (z. B. "letzte 30 Tage").                                           |
| FA4   | Should                | Ein Eintrag kann nachträglich korrigiert werden, falls ein Tippfehler unterlaufen ist.                          |
| FA5   | Could                 | Die Liste der Einträge einer Maschine kann als PDF exportiert werden.                                           |
| FA6   | Won't (diese Version) | Automatische Erinnerungen für fällige Wartungen sind **nicht** Teil dieser Version.                             |

> **Warum das funktioniert:** Jede Zeile beginnt mit einem Subjekt und einem konkreten, beobachtbaren Verhalten ("kann erfassen", "können angezeigt werden") – das macht sie **testbar** (Kriterium aus Kapitel 1.4): Man kann es ausprobieren und sagen "funktioniert" oder "funktioniert nicht". FA6 zeigt zusätzlich, dass auch ein bewusst **ausgeschlossener** Punkt in der MoSCoW-Logik ("Won't") explizit benannt werden darf, statt ihn einfach wegzulassen – das verhindert spätere Missverständnisse.

---

## 3. Nicht-funktionale Anforderungen

| **#** | **Kategorie**   | **Anforderung**                                                                                       |
| ----- | --------------- | ----------------------------------------------------------------------------------------------------- |
| NFA1  | Performance     | Die Liste der Einträge einer Maschine (bis 500 Einträge) wird innerhalb 1 Sekunde angezeigt.          |
| NFA2  | Benutzbarkeit   | Ein/e Techniker/-in ohne IT-Vorkenntnisse kann einen Eintrag ohne Schulung innert 3 Minuten erfassen. |
| NFA3  | Zuverlässigkeit | Ein einmal gespeicherter Eintrag geht auch bei einem Programmabsturz nicht verloren.                  |
| NFA4  | Sicherheit      | Einträge können nur von angemeldeten Techniker/-innen erfasst werden.                                 |

> **Warum das funktioniert:** Vergleichen Sie NFA2 mit dem Negativbeispiel aus Kapitel 1.4.1 ("Die Software soll benutzerfreundlich sein.") – hier steht stattdessen eine **messbare** Zeitangabe und eine klar definierte Zielgruppe. Genau das unterscheidet eine brauchbare von einer unbrauchbaren nicht-funktionalen Anforderung.

---

## 4. Abgrenzung

- Keine Anbindung an ein ERP- oder Instandhaltungsplanungssystem in dieser Version.
- Keine automatische Erinnerungsfunktion für fällige Wartungen (siehe FA6).
- Keine Verwaltung von Ersatzteilbeständen – dies bleibt Teil des bestehenden Lagerverwaltungssystems.

> **Warum das funktioniert:** Eine Abgrenzung ist genauso wichtig wie die Anforderungen selbst: Sie verhindert, dass der Auftraggeber später etwas erwartet, das nie vereinbart wurde ("Scope Creep"). Formulieren Sie Abgrenzungen so konkret wie die Anforderungen selbst – nicht nur "diverses Weiteres ist nicht enthalten".

---

## 5. Schnittstellen

- Export der Einträge als PDF-Datei (lokal speicherbar, FA5).
- Keine Datenbankanbindung an Drittsysteme in dieser Version; Daten werden lokal in einer SQLite-Datenbank gespeichert.

---

## 6. Randbedingungen

- Lauffähig auf den bestehenden Werkstatt-PCs (Windows 10/11).
- Kein zusätzlicher Lizenzaufwand – Umsetzung mit bereits vorhandenen Werkzeugen (z. B. C# / .NET).
- Fertigstellung bis Ende des laufenden Quartals gewünscht.

---

## Qualitätscheck (Selbstkontrolle gemäss Kapitel 1.4)

| Kriterium        | Erfüllt? | Begründung                                                                                                 |
| ---------------- | :------: | ---------------------------------------------------------------------------------------------------------- |
| Eindeutig        |    X     | Jede Anforderung lässt nur eine Interpretation zu (z. B. "innert 3 Minuten", nicht "schnell").             |
| Testbar          |    X     | Jede Anforderung lässt sich konkret überprüfen (ausprobieren, Zeit stoppen, Rolle prüfen).                 |
| Widerspruchsfrei |    X     | Keine Anforderung widerspricht einer anderen oder der Abgrenzung.                                          |
| Vollständig      |    X     | Auch der Sonderfall "Programmabsturz" (NFA3) und ein bewusst ausgeschlossener Punkt (FA6) sind mitgedacht. |
| Nachvollziehbar  |    X     | Jede Anforderung lässt sich auf das in der Ausgangslage beschriebene Bedürfnis zurückführen.               |

---

## Was Sie aus diesem Beispiel mitnehmen sollten

1. **Kurz halten, aber konkret sein.** Die Ausgangslage braucht keine Seite – 3–5 Sätze reichen, wenn sie präzise sind.
2. **Jede Anforderung einzeln und nummeriert.** So können Sie später in Tests und Präsentationen gezielt darauf verweisen (vgl. Testprotokolle in den Musterlösungen der Praxisarbeit).
3. **"Won't have" ist genauso wertvoll wie "Must have".** Explizit ausgeschlossene Punkte verhindern Missverständnisse.
4. **Nicht-funktionale Anforderungen brauchen Zahlen.** "Schnell", "sicher", "modern" sind ohne Mass- oder Prüfkriterium wertlos.
5. **Die Abgrenzung ist kein Nebensatz.** Nehmen Sie sich dafür genauso viel Zeit wie für die funktionalen Anforderungen.

---

© 2026 Lukas Müller – Licensed under CC BY-NC-ND 4.0
See [LICENSE](..\license.md) file for details.
