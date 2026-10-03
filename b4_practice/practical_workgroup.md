|                      |                           |                               |
| -------------------- | ------------------------- | ----------------------------- |
| **HF Systemtechnik** | **Softwareentwicklung A** | ![logo](../x_gitres/logo.png) |

- [1. Praxisarbeit – Vom Modell zum Code](#1-praxisarbeit--vom-modell-zum-code)
  - [1.1. Lernziele](#11-lernziele)
  - [1.2. Rahmenbedingungen](#12-rahmenbedingungen)
  - [1.3. Ablauf](#13-ablauf)
  - [1.4. Hinweise zur Umsetzung in Flowgorithm](#14-hinweise-zur-umsetzung-in-flowgorithm)
  - [1.5. Abgabe](#15-abgabe)
  - [1.6. Bewertungskriterien](#16-bewertungskriterien)
- [2. Auftrag A – Garagentor-Steuerung](#2-auftrag-a--garagentor-steuerung)
- [3. Auftrag B – Alarmanlage](#3-auftrag-b--alarmanlage)
- [4. Auftrag C – Waschmaschinen-Programmablauf](#4-auftrag-c--waschmaschinen-programmablauf)
- [5. Auftrag D – Kaffee-Vollautomat](#5-auftrag-d--kaffee-vollautomat)

---

</br>

# 1. Praxisarbeit – Vom Modell zum Code

## 1.1. Lernziele

Nach dieser Praxisarbeit können Sie:

- [ ] für eine neue, unbekannte Aufgabenstellung eigenständig eine Spezifikation erstellen
- [ ] die passenden Zustände und Ereignisse identifizieren und in einem korrekten Zustandsdiagramm darstellen
- [ ] die Zustandslogik in ein lauffähiges Flowgorithm-Programm überführen
- [ ] die Implementierung anhand selbst definierter Testfälle prüfen
- [ ] das eigene Vorgehen und Ergebnis einer Klasse kurz und verständlich präsentieren

## 1.2. Rahmenbedingungen

|                  |                                                                                                 |
| ---------------- | ----------------------------------------------------------------------------------------------- |
| **Sozialform**   | Partnerarbeit (2 Personen)                                                                      |
| **Zeitbudget**   | max. 4 Stunden (inkl. Vorbereitung der Kurzpräsentation)                                        |
| **Hilfsmittel**  | Papier/draw.io für die Modellierung, Flowgorithm für die Implementierung, eigene Kursunterlagen |
| **Auftragswahl** | Jedes Team wählt **einen** der vier Aufträge (A, B, C oder D) oder erhält diesen zugeteilt      |

## 1.3. Ablauf

Bearbeiten Sie den gewählten Auftrag konsequent in diesen vier Phasen – genau wie im bisherigen Unterricht:

```bash
Spezifikation → Zustandsdiagramm → Implementierung (Flowgorithm) → Kurzpräsentation
```

1. **Spezifikation:** Formulieren Sie mindestens 3 funktionale und 1 nicht-funktionale Anforderung zum gewählten Szenario.
2. **Zustandsdiagramm:** Leiten Sie daraus die Zustände und Ereignisse ab und zeichnen Sie ein vollständiges, korrektes Zustandsdiagramm (Startzustand, saubere Trennung Zustand/Ereignis, Determinismus).
3. **Implementierung:** Setzen Sie die Zustandslogik als lauffähiges Flowgorithm-Programm um (siehe Hinweise unten).
4. **Kurzpräsentation:** Bereiten Sie eine ca. 5-minütige Präsentation vor (Spezifikation → Diagramm → Demo des laufenden Programms).

## 1.4. Hinweise zur Umsetzung in Flowgorithm

Da Flowgorithm über keine echten Sensoren oder Unterbrechungen verfügt, werden Ereignisse durch eine **Eingabe** simuliert. Ein bewährtes Grundmuster:

```bash
zustand ← "Startzustand"

SOLANGE eingabe ≠ "ende"
    AUSGABE "Aktueller Zustand: " + zustand
    EINGABE eingabe   // simuliertes Ereignis, z. B. Tastendruck, Sensorwert

    WENN zustand = "A" UND eingabe = "x" DANN
        zustand ← "B"
    SONST WENN zustand = "B" UND eingabe = "y" DANN
        zustand ← "C"
    ...
```

- Verwenden Sie eine Variable (z. B. `zustand`), die immer genau einen der modellierten Zustände enthält.
- Jede `Wenn`-Verzweigung entspricht genau einem Übergang aus Ihrem Zustandsdiagramm – prüfen Sie nach der Implementierung, ob **jeder** Pfeil aus dem Diagramm im Code vorkommt.
- Lassen Sie den aktuellen Zustand nach jeder Eingabe ausgeben, damit der Ablauf beim Testen sichtbar ist.
- Ein Exit-Wert (z. B. "ende") beendet die Schleife sauber.

## 1.5. Abgabe

- Spezifikation (Textdokument, ca. ½ Seite)
- Zustandsdiagramm (Foto, draw.io-Export oder Scan)
- Flowgorithm-Datei (`.fprg`) sowie ein Screenshot eines erfolgreichen Testdurchlaufs
- Kurzes Testprotokoll (mindestens 3 Testfälle inkl. mindestens 1 Sonderfall)

## 1.6. Bewertungskriterien

| Kriterium                                                                                               | Punkte |
| ------------------------------------------------------------------------------------------------------- | ------ |
| Spezifikation vollständig und verständlich                                                              | 5      |
| Zustandsdiagramm korrekt (Zustände/Ereignisse sauber getrennt, deterministisch, Startzustand erkennbar) | 6      |
| Flowgorithm-Implementierung lauffähig und entspricht dem Zustandsdiagramm                               | 10     |
| Testprotokoll mit sinnvollen Testfällen inkl. Sonderfall                                                | 3      |
| Kurzpräsentation (Nachvollziehbarkeit, Live-Demo)                                                       | 6      |
| **Total**                                                                                               | **30** |

---

</br>

# 2. Auftrag A – Garagentor-Steuerung

**Ausgangslage:** Ein Hausbesitzer möchte sein Garagentor automatisch per Funk-Fernbedienung steuern lassen. Das Tor besitzt zudem eine Lichtschranke, die ein Hindernis im Torbereich erkennt.

**Verhalten (vereinfacht, ohne Hardwaredetails):**

- Im Ruhezustand ist das Tor **geschlossen**.
- Wird die Fernbedienung gedrückt, **öffnet** sich das Tor.
- Ist das Tor vollständig offen, bleibt es eine feste Zeit **offen** stehen.
- Nach Ablauf dieser Zeit **schliesst** das Tor automatisch wieder.
- Erkennt die Lichtschranke während des Schliessens ein Hindernis, **stoppt** das Tor sofort und öffnet wieder vollständig.
- Ein erneuter Druck auf die Fernbedienung während des Öffnens oder Schliessens **stoppt** die Bewegung sofort (Sicherheitsstopp).

**Ihre Aufgabe:** Analysieren Sie dieses Verhalten selbständig, leiten Sie die notwendigen Zustände und Ereignisse ab und setzen Sie den vollständigen Zyklus gemäss Kapitel 1.3 um.

**Mindestanforderungen:** mindestens 4 Zustände, mindestens 5 Übergänge (inkl. mindestens einem Sicherheits-/Fehlerfall).

---

# 3. Auftrag B – Alarmanlage

**Ausgangslage:** Ein kleines Gewerbegebäude soll mit einer einfachen Alarmanlage mit Zahlencode-Tastatur gesichert werden.

**Verhalten (vereinfacht):**

- Im Normalfall ist die Anlage **unscharf** (deaktiviert).
- Durch Eingabe des korrekten Codes wird die Anlage **scharf geschaltet**.
- Wird im scharfen Zustand eine Bewegung erkannt, beginnt eine **Vorwarnzeit**, innerhalb der der korrekte Code eingegeben werden kann, um die Anlage zurück auf unscharf zu setzen.
- Läuft die Vorwarnzeit ab, ohne dass der korrekte Code eingegeben wurde, löst die Anlage **Alarm** aus.
- Im Alarmzustand setzt nur die Eingabe des korrekten Codes die Anlage zurück auf unscharf.
- Wird während der Vorwarnzeit ein falscher Code eingegeben, bleibt die Anlage in der Vorwarnzeit (keine Sonderbehandlung nötig) – überlegen Sie sich aber, ob das sinnvoll ist oder ob Sie dies in Ihrer Spezifikation bewusst anders festlegen.

**Ihre Aufgabe:** Analysieren Sie dieses Verhalten selbständig, leiten Sie die notwendigen Zustände und Ereignisse ab und setzen Sie den vollständigen Zyklus gemäss Kapitel 1.3 um.

**Mindestanforderungen:** mindestens 4 Zustände, mindestens 5 Übergänge (inkl. korrekter und falscher Code-Eingabe als unterscheidbare Ereignisse).

---

# 4. Auftrag C – Waschmaschinen-Programmablauf

**Ausgangslage:** Für eine einfache Haushalts-Waschmaschine soll die grundlegende Ablaufsteuerung eines Waschprogramms nachgebildet werden (ohne technische Details zu Motor, Pumpe oder Sensorik).

**Verhalten (vereinfacht):**

- Die Maschine ist im Ruhezustand **bereit**.
- Durch Programmstart beginnt die Phase **Waschen**.
- Nach Abschluss des Waschens folgt automatisch **Spülen**.
- Nach dem Spülen folgt automatisch **Schleudern**.
- Nach dem Schleudern ist das Programm **fertig** und die Maschine kehrt nach einer Quittierung (z. B. Tür öffnen) zurück in den Zustand "bereit".
- Zu jedem Zeitpunkt während Waschen, Spülen oder Schleudern kann die Taste "Pause" gedrückt werden – das Programm **pausiert** und kann durch erneutes Drücken an derselben Stelle fortgesetzt werden.
- Wird die Taste "Abbruch" gedrückt, kehrt die Maschine aus jedem laufenden Zustand direkt in "bereit" zurück.

**Ihre Aufgabe:** Analysieren Sie dieses Verhalten selbständig, leiten Sie die notwendigen Zustände und Ereignisse ab und setzen Sie den vollständigen Zyklus gemäss Kapitel 1.3 um.

**Mindestanforderungen:** mindestens 5 Zustände, mindestens 7 Übergänge (inkl. Pause/Fortsetzen und Abbruch aus mehreren Zuständen).

> **Hinweis:** Bei diesem Auftrag ist besonders die **Determinismus-Regel** (Kapitel 1.4) zu beachten – überlegen Sie genau, wie "Pause" und "Abbruch" aus mehreren unterschiedlichen Zuständen heraus sauber modelliert werden können, ohne dass unübersichtlich viele Einzelpfeile entstehen.

---

# 5. Auftrag D – Kaffee-Vollautomat

**Ausgangslage:** Für ein Büro soll die grundlegende Ablaufsteuerung eines Kaffee-Vollautomaten nachgebildet werden (ohne technische Details zu Pumpe, Mahlwerk oder Heizung).

**Verhalten (vereinfacht):**

- Die Maschine ist im Ruhezustand **bereit**.
- Durch Drücken der Tassentaste beginnt die Maschine zu **mahlen**.
- Nach Abschluss des Mahlvorgangs folgt automatisch das **Brühen**.
- Nach dem Brühen folgt die **Ausgabe** des Kaffees in die Tasse.
- Nach Abschluss der Ausgabe kehrt die Maschine automatisch zurück in den Zustand "bereit".
- Erkennt der Wassertank-Sensor während des Mahlens **oder** während des Brühens einen leeren Tank, wechselt die Maschine sofort in einen **Fehlerzustand** – unabhängig davon, in welcher der beiden Phasen sie sich gerade befand.
- Aus dem Fehlerzustand gelangt die Maschine ausschliesslich durch das Ereignis "Tank nachgefüllt" zurück in den Zustand "bereit".
- Wird im Zustand "bereit" stattdessen die Taste "Reinigung" gedrückt, startet ein **Reinigungszyklus**; nach dessen Abschluss kehrt die Maschine automatisch zu "bereit" zurück.

**Ihre Aufgabe:** Analysieren Sie dieses Verhalten selbständig, leiten Sie die notwendigen Zustände und Ereignisse ab und setzen Sie den vollständigen Zyklus gemäss Kapitel 1.3 um.

**Mindestanforderungen:** mindestens 5 Zustände, mindestens 7 Übergänge (inkl. des Fehlerzustands, der aus zwei unterschiedlichen Zuständen heraus erreichbar sein muss).

> **Hinweis:** Prüfen Sie insbesondere die **Vollständigkeitsregel** (Kapitel 1.4/1.7): Wenn der Fehlerzustand aus zwei verschiedenen Zuständen erreichbar sein muss, braucht es dafür zwei separate, aber gleichartige Übergänge – ein einzelner Pfeil kann nicht zwei Quellzustände gleichzeitig haben.

---

© 2026 Lukas Müller – Licensed under CC BY-NC-ND 4.0
See [LICENSE](..\license.md) file for details.
