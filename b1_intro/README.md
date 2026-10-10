|                      |                           |                               |
| -------------------- | ------------------------- | ----------------------------- |
| **HF Systemtechnik** | **Softwareentwicklung A** | ![logo](../x_gitres/logo.png) |

- [1. Einführung in die Softwareentwicklung](#1-einführung-in-die-softwareentwicklung)
  - [1.1. Lernziele](#11-lernziele)
  - [1.2. Warum überhaupt "Softwareentwicklung"?](#12-warum-überhaupt-softwareentwicklung)
    - [1.2.1. Programmieren vs. Softwareentwicklung](#121-programmieren-vs-softwareentwicklung)
  - [1.3. Eigenschaften von Software](#13-eigenschaften-von-software)
  - [1.4. Warum scheitern Softwareprojekte?](#14-warum-scheitern-softwareprojekte)
  - [1.5. Die Rolle des Systemtechnikers/der Systemtechnikerin HF](#15-die-rolle-des-systemtechnikersder-systemtechnikerin-hf)
- [2. Übungsaufgaben](#2-übungsaufgaben)
  - [2.1. Softwareentwicklung vs. Programmieren](#21-softwareentwicklung-vs-programmieren)
  - [2.2. Ursachenanalyse aus der eigenen Praxis](#22-ursachenanalyse-aus-der-eigenen-praxis)

---

</br>

# 1. Einführung in die Softwareentwicklung

## 1.1. Lernziele

Nach diesem Kapitel können Sie:

- [ ] Softwareentwicklung als planmässigen Entwicklungsprozess definieren und von reinem "Programmieren" abgrenzen
- [ ] typische Eigenschaften von Software (im Vergleich zu physischen Produkten) benennen
- [ ] die häufigsten Ursachen für gescheiterte oder verzögerte Softwareprojekte erklären
- [ ] die eigene Rolle als Systemtechniker/-in HF im Softwareentwicklungsumfeld einordnen

![Titelbild](./x_gitres/title-picture.png)

## 1.2. Warum überhaupt "Softwareentwicklung"?

Systemtechniker/-innen HF kommen im Berufsalltag laufend mit Software in Berührung: Auswertetools, kleine Automatisierungsskripte, Konfigurationswerkzeuge, Schnittstellenprogramme. Oft entsteht dabei der Eindruck, Programmieren bestehe einfach aus "Code schreiben, bis es läuft". In der Praxis zeigt sich aber rasch: Ohne systematisches Vorgehen wird selbst ein kleines Programm schwer wartbar, fehleranfällig und für andere Personen nicht nachvollziehbar.

> **Analogie:** Ein Haus baut man nicht, indem man einfach Backsteine aufeinanderschichtet, bis es "irgendwie" steht. Es braucht einen Plan, eine Statik, eine Abnahme durch Fachpersonen. Genauso braucht Software einen strukturierten Entstehungsprozess – auch wenn das Endprodukt "nur" ein PowerShell-Skript oder ein kleines Steuerprogramm ist.

**Definition:** Softwareentwicklung ist der planmässige, methodisch geleitete Prozess, mit dem aus einer Anforderung eine funktionsfähige, nachvollziehbare und wartbare Software-Lösung entsteht – von der ersten Idee bis zum Betrieb und der laufenden Pflege.

Der Begriff **Software Engineering** (Softwaretechnik) betont dabei zusätzlich den ingenieurmässigen Charakter: systematisch, mess- und nachvollziehbar, mit dokumentierten Entscheidungen – im Gegensatz zum reinen "Drauflosprogrammieren" (umgangssprachlich manchmal "Cowboy-Coding" genannt).

### 1.2.1. Programmieren vs. Softwareentwicklung

|                    | **Programmieren**         | **Softwareentwicklung**           |
| ------------------ | ------------------------- | --------------------------------- |
| Fokus              | Code schreiben            | Gesamter Entstehungsprozess       |
| Zeithorizont       | Aufgabe lösen             | Produkt über Lebensdauer betreuen |
| Dokumentation      | Oft implizit/fehlend      | Bewusster Bestandteil             |
| Qualitätssicherung | Ad hoc                    | Geplant (Reviews, Tests)          |
| Team-Fähigkeit     | Schwierig nachvollziehbar | Nachvollziehbar durch Struktur    |

Beide Tätigkeiten gehören zusammen – Programmieren ist eine (wichtige!) Teiltätigkeit **innerhalb** der Softwareentwicklung, nicht deren Synonym.

## 1.3. Eigenschaften von Software

Software unterscheidet sich in wesentlichen Punkten von physischen, "greifbaren" Produkten – dies erklärt, weshalb spezielle Entwicklungsmethoden nötig sind:

| **Eigenschaft**      | **Bedeutung**                           | **Konsequenz für die Entwicklung**                                                       |
| -------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Immateriell**      | Software ist nicht sichtbar/anfassbar   | Fortschritt ist schwer messbar ("zu 80 % fertig" ist vage)                               |
| **Beliebig komplex** | Kein physisches Limit wie bei Bauteilen | Komplexität wächst unbemerkt, wenn nicht bewusst gegengesteuert wird                     |
| **Leicht änderbar**  | Code kann jederzeit geändert werden     | Verführung zu unkontrollierten Änderungen ohne erneuten Test                             |
| **Nicht abnutzbar**  | Software "verschleisst" nicht technisch | Fehler bleiben bestehen, bis sie behoben werden – sie "reparieren sich nicht von selbst" |
| **Stark vernetzt**   | Teile hängen oft unsichtbar zusammen    | Eine kleine Änderung kann an anderer Stelle Folgefehler auslösen                         |

> **Merksatz:** Bei einer Maschine sieht man einen Verschleiss oder Bruch meist direkt. Bei Software ist ein Fehler oft erst sichtbar, wenn ein ganz bestimmter, seltener Fall eintritt – das macht Softwarequalität zu einer besonderen Herausforderung.

## 1.4. Warum scheitern Softwareprojekte?

Zahlreiche Erfahrungsberichte aus der Praxis (unabhängig von Branche oder Unternehmensgrösse) zeigen ein wiederkehrendes Muster von Ursachen für gescheiterte oder stark verzögerte Softwareprojekte:

1. **Unklare oder unvollständige Anforderungen** – die häufigste Ursache überhaupt. Der Auftraggeber weiss oft selbst noch nicht genau, was er will.
2. **Fehlende oder zu späte Einbindung der Anwender** – Software wird "am grünen Tisch" entworfen, ohne die tatsächlichen Arbeitsabläufe zu kennen.
3. **Unrealistische Zeit- und Kostenschätzung** – Softwareaufwand wird systematisch unterschätzt, insbesondere bei Schnittstellen und Fehlerbehebung.
4. **Fehlendes Testen** – Fehler werden zu spät erkannt, wenn die Korrektur bereits deutlich aufwändiger ist.
5. **Fehlende Dokumentation** – Wissen steckt nur im Kopf einer einzelnen Person; fällt diese aus, steht das Projekt still.

> **Wichtig für dieses Modul:** Die in den folgenden Kapiteln vorgestellten Werkzeuge (Spezifikation, Zustandsdiagramm, Struktogramm, PAP) sind direkte Antworten auf die Ursachen 1, 2 und 4 – sie helfen, Anforderungen frühzeitig zu klären und Fehler vor der Implementierung zu erkennen.

## 1.5. Die Rolle des Systemtechnikers/der Systemtechnikerin HF

Systemtechniker/-innen HF sind in der Praxis selten "reine" Softwareentwickler/-innen, übernehmen aber häufig genau jene Rollen, in denen die Grundlagen dieses Moduls direkt zur Anwendung kommen:

- **Anforderungen formulieren**, wenn eine Automatisierungs- oder Auswertelösung extern entwickelt oder beschafft wird
- **Kleine Tools und Skripte selbst erstellen** (Auswertungen, Konfigurationshilfen, einfache Schnittstellen)
- **Mit Softwareentwicklern kommunizieren** und dabei eine gemeinsame fachliche Sprache benötigen (Zustandsdiagramm, Struktogramm sind hierfür ideale, technologieunabhängige Kommunikationsmittel)
- **Bestehende Software beurteilen und abnehmen**, ohne selbst jede Codezeile zu verstehen

---

</br>

# 2. Übungsaufgaben

## 2.1. Softwareentwicklung vs. Programmieren

| **Vorgabe**         | **Beschreibung**                                                             |
| :------------------ | :--------------------------------------------------------------------------- |
| **Lernziele**       | Programmieren und Softwareentwicklung anhand eigener Beispiele unterscheiden |
| **Sozialform**      | Einzelarbeit                                                                 |
| **Auftrag**         | siehe unten                                                                  |
| **Hilfsmittel**     | Unterlagen dieses Kapitels                                                   |
| **Zeitbedarf**      | 20 min                                                                       |
| **Lösungselemente** | 4 begründete Zuordnungen                                                     |

**Aufgabenstellung:**

Ordnen Sie folgende vier Tätigkeiten begründet der Spalte "Programmieren" oder "Softwareentwicklung" zu (Mehrfachnennung möglich, wenn beide Aspekte enthalten sind):

1. Ein PowerShell-Skript schreiben, das einmalig 200 Dateien umbenennt.
2. Ein Auswertetool für die Tagesproduktion planen, spezifizieren, umsetzen, testen und danach über Jahre pflegen.
3. Eine Codezeile in einem bestehenden Programm korrigieren, ohne die Auswirkung auf andere Programmteile zu prüfen.
4. Vor der Umsetzung eines neuen Tools ein Gespräch mit den künftigen Anwendern führen, um die Anforderungen zu klären.

---

## 2.2. Ursachenanalyse aus der eigenen Praxis

| **Vorgabe**         | **Beschreibung**                                                               |
| :------------------ | :----------------------------------------------------------------------------- |
| **Lernziele**       | Ursachen für gescheiterte Softwareprojekte auf ein eigenes Beispiel übertragen |
| **Sozialform**      | Partnerarbeit                                                                  |
| **Auftrag**         | siehe unten                                                                    |
| **Zeitbedarf**      | 25 min                                                                         |
| **Lösungselemente** | Kurzpräsentation im Plenum (2 Min. pro Team)                                   |

**Aufgabenstellung:**

Tauschen Sie sich zu zweit über ein Softwaretool, ein Skript oder eine Automatisierungslösung aus Ihrem Berufsalltag aus, die/das nicht wie gewünscht funktioniert hat oder deutlich mehr Aufwand verursacht hat als geplant.

1. Ordnen Sie das Problem mindestens einer der 5 Ursachen zu.
2. Überlegen Sie: Welches der in diesem Modul vorgestellten Werkzeuge (Spezifikation, Zustandsdiagramm, Struktogramm, PAP) hätte das Problem voraussichtlich vermieden oder zumindest früher sichtbar gemacht?
3. Haltet eure Erkenntnisse in 3–4 Sätzen fest und stellt sie kurz der Klasse vor.

---

© 2026 Lukas Müller – Licensed under CC BY-NC-ND 4.0
See [LICENSE](..\license.md) file for details.
