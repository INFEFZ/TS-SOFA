|                      |                           |                               |
| -------------------- | ------------------------- | ----------------------------- |
| **HF Systemtechnik** | **Softwareentwicklung A** | ![logo](../x_gitres/logo.png) |

- [1. Praktikum: Vom Modell zum Code](#1-praktikum-vom-modell-zum-code)
  - [1.1. Lernziele](#11-lernziele)
  - [1.2. Der vollständige Mini-Zyklus](#12-der-vollständige-mini-zyklus)
  - [1.3. Werkzeug: Flowgorithm](#13-werkzeug-flowgorithm)
    - [1.3.1. Grundmuster für eine Zustandslogik](#131-grundmuster-für-eine-zustandslogik)
  - [1.4. Praxisarbeit – vier Aufträge zur Wahl](#14-praxisarbeit--vier-aufträge-zur-wahl)

---

</br>

# 1. Praktikum: Vom Modell zum Code

## 1.1. Lernziele

Nach diesem Kapitel können Sie:

- [ ] die in den vorangehenden Kapiteln erlernten Werkzeuge (Spezifikation, Zustandsdiagramm, Struktogramm/PAP, Algorithmus) auf eine eigene, kleine Aufgabenstellung anwenden
- [ ] eine einfache Zustandslogik eigenständig in Flowgorithm umsetzen
- [ ] eine Implementierung anhand selbst definierter Testfälle prüfen
- [ ] den eigenen Entwicklungsprozess und Kompetenzzuwachs dokumentieren und reflektieren

---

## 1.2. Der vollständige Mini-Zyklus

In diesem Praktikum wird der gesamte in diesem Modul gelernte Prozess an einem konkreten, kleinen Projekt durchlaufen:

``` bash
Spezifikation → Modellierung (Zustandsdiagramm/Struktogramm) → Implementierung → Test → Reflexion
```

> Damit schliesst sich der Kreis zu Kapitel 1: Sie sollen am eigenen Beispiel erleben, weshalb sich der Mehraufwand der Modellierung lohnt, **bevor** eine einzige Codezeile geschrieben wird.

---

## 1.3. Werkzeug: Flowgorithm

Als Implementierungsumgebung dient **Flowgorithm** – dasselbe Werkzeug, das Sie bereits aus Kapitel 6 (PAP) kennen. Das hat einen didaktischen Vorteil: Die grafische Modellierung (Zustandsdiagramm) und die lauffähige Umsetzung (Flowgorithm-Programm) liegen näher beieinander als bei einer klassischen Textsprache, und Sie können Ihr Programm direkt im selben Werkzeug Schritt für Schritt ausführen und beobachten.

Da Flowgorithm über keine echten Sensoren oder Unterbrechungen verfügt, werden Ereignisse (Tastendruck, Sensorwert, Zeitablauf usw.) durch eine **Eingabe** simuliert.

### 1.3.1. Grundmuster für eine Zustandslogik

Jede Aufgabe in diesem Praktikum folgt demselben Grundmuster:

```bash
zustand ← "Startzustand"

SOLANGE ereignis ≠ "ende"
    AUSGABE "Aktueller Zustand: " + zustand
    EINGABE ereignis   // simuliertes Ereignis, z. B. Tastendruck, Sensorwert

    WENN zustand = "A" UND ereignis = "x" DANN
        zustand ← "B"
    SONST WENN zustand = "B" UND ereignis = "y" DANN
        zustand ← "C"
    ...
```

- Verwenden Sie eine Variable (z. B. `zustand`), die immer genau einen der modellierten Zustände enthält.
- Jede `Wenn`-Verzweigung entspricht genau einem Übergang aus Ihrem Zustandsdiagramm – prüfen Sie nach der Implementierung, ob **jeder** Pfeil aus dem Diagramm im Code vorkommt.
- Lassen Sie den aktuellen Zustand nach jeder Eingabe ausgeben, damit der Ablauf beim Testen sichtbar ist.
- Ein Exit-Wert (z. B. `"ende"`) beendet die Schleife sauber.

---

## 1.4. Praxisarbeit – vier Aufträge zur Wahl

Die praktische Umsetzung erfolgt im Rahmen einer **Praxisarbeit in Partnerarbeit** (max. 4 Stunden). Jedes Team wählt einen von vier Aufträgen – alle vier verlangen denselben vollständigen Zyklus (Spezifikation → Zustandsdiagramm → Implementierung in Flowgorithm → Kurzpräsentation), unterscheiden sich aber im Szenario und im Schwierigkeitsgrad:

| Auftrag | Szenario                                                      | Schwierigkeitsgrad |
| ------- | ------------------------------------------------------------- | ------------------ |
| **A**   | Garagentor-Steuerung (Fernbedienung, Lichtschranke)           | mittel             |
| **B**   | Alarmanlage (Scharf/Unscharf, Vorwarnzeit, Code-Eingabe)      | einfach            |
| **C**   | Waschmaschinen-Programmablauf (mehrere Phasen, Pause/Abbruch) | anspruchsvoll      |
| **D**   | Kaffee-Vollautomat (Mahlen/Brühen/Ausgabe, Fehlerzustand)     | mittel             |

Vollständige Aufgabenstellungen, Rahmenbedingungen und Abgabeanforderungen: **[praxisarbeit.md](practical_workgroup.md)**

---

© 2026 Lukas Müller – Licensed under CC BY-NC-ND 4.0
See [LICENSE](..\license.md) file for details.
