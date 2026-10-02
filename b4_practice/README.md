|                      |                           |                               |
| -------------------- | ------------------------- | ----------------------------- |
| **HF Systemtechnik** | **Softwareentwicklung A** | ![logo](../x_gitres/logo.png) |

- [1. Praktikum: Vom Modell zum Code](#1-praktikum-vom-modell-zum-code)
  - [1.1. Lernziele](#11-lernziele)
  - [1.2. Der vollständige Mini-Zyklus](#12-der-vollständige-mini-zyklus)
  - [1.3. Wahl der Umgebung](#13-wahl-der-umgebung)
    - [1.3.1. Grundgerüst C# (Konsolenanwendung)](#131-grundgerüst-c-konsolenanwendung)
    - [1.3.2. Grundgerüst Arduino (C, Simulation über Serial Monitor ohne echte Hardware möglich)](#132-grundgerüst-arduino-c-simulation-über-serial-monitor-ohne-echte-hardware-möglich)
  - [1.4. Praktikumsaufgabe – Ampelsteuerung (Leitbeispiel)](#14-praktikumsaufgabe--ampelsteuerung-leitbeispiel)
    - [1.4.1. Auftrag](#141-auftrag)
    - [1.4.2. Bewertungskriterien](#142-bewertungskriterien)
  - [1.5. Zusatzaufgaben (für schnellere Studierende oder als Wahlaufgabe)](#15-zusatzaufgaben-für-schnellere-studierende-oder-als-wahlaufgabe)
    - [1.5.1. Zusatzaufgabe A – Sortieralgorithmus implementieren](#151-zusatzaufgabe-a--sortieralgorithmus-implementieren)
    - [1.5.2. Zusatzaufgabe B – Zustandsautomat Getränkeautomat](#152-zusatzaufgabe-b--zustandsautomat-getränkeautomat)
  - [1.6. Vorbereitung auf die Teilprüfung](#16-vorbereitung-auf-die-teilprüfung)

---

</br>

# 1. Praktikum: Vom Modell zum Code

## 1.1. Lernziele

Nach diesem Kapitel können Sie:

- [ ] die in den vorangehenden Kapiteln erlernten Werkzeuge (Spezifikation, Zustandsdiagramm, Struktogramm/PAP, Algorithmus) auf eine eigene, kleine Aufgabenstellung anwenden
- [ ] eine einfache Aufgabenstellung eigenständig in Arduino (C) oder C# mit VS Code umsetzen
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

## 1.3. Wahl der Umgebung

| **Option**         | **Eignung**                                                                 | **Voraussetzungen**                                                                                                                          |
| ------------------ | --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Arduino (C)**    | Studierende mit Interesse an einfacher Hardware-Simulation (LED, Taster)    | Arduino IDE oder Onlinesimulator (z. B. Wokwi/Tinkercad); *Hardwaredetails werden bewusst nicht vertieft – im Fokus steht die Programmlogik* |
| **C# mit VS Code** | Studierende mit Fokus auf klassische Softwareentwicklung, Konsolenanwendung | .NET SDK, VS Code mit C#-Erweiterung                                                                                                         |

Die Wahl ist freigestellt; entscheidend ist die konsequente Anwendung des gesamten Entwicklungsprozesses, nicht die gewählte Technologie.

### 1.3.1. Grundgerüst C# (Konsolenanwendung)

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Ampelsteuerung gestartet.");
        // Zustandslogik folgt hier
    }
}
```

### 1.3.2. Grundgerüst Arduino (C, Simulation über Serial Monitor ohne echte Hardware möglich)

```c
void setup() {
  Serial.begin(9600);
  Serial.println("Ampelsteuerung gestartet.");
}

void loop() {
  // Zustandslogik folgt hier
}
```

## 1.4. Praktikumsaufgabe – Ampelsteuerung (Leitbeispiel)

| **Vorgabe**         | **Beschreibung**                                                  |
| :------------------ | :---------------------------------------------------------------- |
| **Lernziele**       | Vollständigen Mini-Entwicklungszyklus eigenständig durchlaufen    |
| **Sozialform**      | Einzel- oder Partnerarbeit                                        |
| **Hilfsmittel**     | VS Code, Arduino IDE/Simulator oder .NET SDK                      |
| **Auftrag**         | siehe unten                                                       |
| **Zeitbedarf**      | ca. 3 Lektionen praktische Umsetzung + 1 Lektion Präsentation     |
| **Lösungselemente** | Spezifikation, Modell, lauffähiger Code, Testprotokoll, Reflexion |

### 1.4.1. Auftrag

1. **Spezifikation:** Verfassen Sie in wenigen Sätzen, was das Programm leisten soll, z. B.: "Fussgängerampel mit Anforderungstaster, Ablauf Rot → Rot-Gelb → Grün → Gelb → Rot." Definieren Sie mindestens 2 funktionale Anforderungen und 1 nicht-funktionale Anforderung.
2. **Modellierung:** Erstellen Sie dazu ein Zustandsdiagramm **und** ein Struktogramm oder einen PAP für die zentrale Ablauflogik. Nutzen Sie dazu bei Bedarf das Ampelbeispiel aus Kapitel 4.5 als Ausgangspunkt.
3. **Implementierung:**
   - *Arduino-Variante:* Simulieren Sie die Ampelphasen über LEDs (oder Ausgabe über den Serial-Monitor, falls keine Hardware vorhanden ist). Zustandswechsel über `delay()` oder eine einfache Zustandsvariable mit `millis()`.
   - *C#-Variante:* Konsolenanwendung, die den Zustand in einer Schleife durchläuft, Wartezeiten über `Thread.Sleep()` simuliert und den aktuellen Zustand ausgibt.
4. **Test:** Dokumentieren Sie mindestens 2 Testfälle (z. B. Normalablauf, Sonderfall "Taste während Grün gedrückt") und das jeweilige Ergebnis in einer kleinen Tabelle.
5. **Reflexion:** Beantworten Sie schriftlich (5–8 Sätze): Wo hat Ihnen die Modellierung (Zustandsdiagramm/Struktogramm) beim Programmieren konkret geholfen? Was würden Sie beim nächsten Mal anders angehen?

### 1.4.2. Bewertungskriterien

| Kriterium                                                      | Punkte |
| -------------------------------------------------------------- | ------ |
| Spezifikation vollständig und verständlich                     | 3      |
| Zustandsdiagramm korrekt (Zustände/Ereignisse sauber getrennt) | 4      |
| Struktogramm/PAP korrekt und nachvollziehbar                   | 4      |
| Lauffähige Umsetzung entspricht dem Modell                     | 5      |
| Testfälle sinnvoll gewählt und dokumentiert                    | 2      |
| Reflexion vorhanden und substanziell                           | 2      |
| **Total**                                                      | **20** |

---

## 1.5. Zusatzaufgaben (für schnellere Studierende oder als Wahlaufgabe)

### 1.5.1. Zusatzaufgabe A – Sortieralgorithmus implementieren

|                |              |
| -------------- | ------------ |
| **Sozialform** | Einzelarbeit |
| **Zeitbedarf** | 30–40 min    |

Implementieren Sie den Bubble-Sort-Algorithmus aus Kapitel 8.4 für ein Array von 5 Zahlen in Ihrer gewählten Sprache (C oder C#). Geben Sie das Array vor und nach der Sortierung aus.

### 1.5.2. Zusatzaufgabe B – Zustandsautomat Getränkeautomat

|                |               |
| -------------- | ------------- |
| **Sozialform** | Partnerarbeit |
| **Zeitbedarf** | 45–60 min     |

Modellieren (Zustandsdiagramm) und implementieren Sie einen einfachen Getränkeautomaten mit den Zuständen: `Bereit`, `Geld eingeworfen`, `Auswahl getroffen`, `Ausgabe`. Gehen Sie analog zur Ampel (Kapitel 10.3) vor: zuerst Spezifikation und Modell, dann Implementierung.

---

## 1.6. Vorbereitung auf die Teilprüfung

Zum Abschluss des Praktikums und des gesamten Moduls empfiehlt sich eine Repetition anhand folgender Fragestellungen, die den Prüfungsstoff abdecken:

- Kernphasen des Softwareentwicklungsprozesses benennen und je einen Arbeitsschritt zuordnen (Kap. 2)
- Funktionale und nicht-funktionale Anforderungen anhand eines Beispiels unterscheiden (Kap. 3)
- Zustandsdiagramm für ein einfaches, neues System zeichnen (Zustände von Ereignissen sauber trennen) (Kap. 4)
- Struktogramm für eine Verzweigung/Schleife erstellen (Kap. 5)
- PAP mit allen 5 Standardsymbolen für einen Ablauf mit Schleife zeichnen (Kap. 6)
- Aufgabe eines Compilers erklären, Unterschied Hoch-/Maschinensprache (Kap. 7)
- Eigenschaften eines Algorithmus benennen und an einem Beispiel prüfen (Kap. 8)
- Agiles vs. klassisches Vorgehen anhand von Kriterien vergleichen (Kap. 9)

> Diese Fragestellungen orientieren sich an Aufbau und Niveau der bisherigen Teilprüfung des Moduls und sind bewusst ohne SPS-/Hardwarebezug formuliert.
