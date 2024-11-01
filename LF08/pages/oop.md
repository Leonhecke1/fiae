# Übersicht zu Objektorientierte Softwarelösungen(LF8)

Inhalte zum Kapitel Objektorientierte Softwarelösungen

Inhalte basierend auf dem Unterricht von Herrn Burggraf, Frau Bardon und dem Lehrbuch

[zurück](/LF08/lf8.md)

## Inhalt

- [Übersicht zu Objektorientierte Softwarelösungen(LF8)](#übersicht-zu-objektorientierte-softwarelösungenlf8)
  - [Inhalt](#inhalt)
  - [Programmierparadigmen](#programmierparadigmen)
    - [Imperative Programmierparadigmen](#imperative-programmierparadigmen)
    - [Deklarative Programmierparadigmen](#deklarative-programmierparadigmen)
  - [Objektorientiertes Programmierparadigma](#objektorientiertes-programmierparadigma)
    - [(Konzept) Abstraktion](#konzept-abstraktion)
    - [(Konzept) Kapselung](#konzept-kapselung)
    - [(Konzept) Vererbung](#konzept-vererbung)
    - [(Konzept) Polymorphie](#konzept-polymorphie)
  - [UML](#uml)
    - [Übersicht UML-Diagramme](#übersicht-uml-diagramme)
    - [Anwendungsfalldiagramm](#anwendungsfalldiagramm)
    - [Klassendiagramm](#klassendiagramm)
  - [Prüfungsaufgaben](#prüfungsaufgaben)
    - [UML, Aufgabe 2, Sommer22](#uml-aufgabe-2-sommer22)

## Programmierparadigmen

> ist das grundlegende Konzept, mit dem der Aufbau und die Ausführung von Programmen beschrieben wird und welches den Programmiersprachen zugrunde liegt

+ beeinflusst die Vorgehensweise, welche bei Programmentwicklung verwendet wird -> grundlegender Programmierstil
+ gibt kein "richtig" / "falsch"
+ spiegeln sich meist in Programmiersprachen wider

![Alt Programmierparadigmen](/LF08/images/paradigmen.png)<br>
*Abb. Programmierparadigmen*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

### Imperative Programmierparadigmen

> hierbei wird im Programm bschrieben, wie ein Problem zu lösen ist<br>
> Lösung wird als eine Folge von einzelnen Anweisungen beschrieben

+ Verwendung von Kontrollstrukturen (Verzweigungen, Schleifen)
+ Programmcode ist leicht verständlich, aber umfangreich

**Strukturiertes Programmierparadigma**
+ Bsp: C, Pascal
+ Verzicht auf bestimmte Sprunganweisungen (GoTo)
+ beinhaltet ersten Ansatz in richtung prozedualen Programmierparadigmas
  + Zerlegung des Programms in Teilprogramme/Funktionen

**Prozedurales Programmierparadigma**
+ Bsp: C, COBOL, Pascal
+ baut auf strukturiertes auf
+ zielt darauf ab, Quelltexte wieder verwendbar zu machen
+ Aufteilung in überschaubare Teile -> Prozeduren, Unterprogramme, Funktionen
  + Programmcode wird übersichtlicher
  + CodeWiederholungen werden vermieden
+ Vorteil von universell einsetzbaren Prozeduren

**Objektorientiertes Programmierparadigma**
+ wird im weiteren Verlauf noch beschrieben

### Deklarative Programmierparadigmen
> im Programm wird beschrieben, was das Problem ist
> System wird Lösung des Problems selbst überlassen

+ Quelltext ist schwer verständlich durch hohen Abstraktionsgrad
  + dafür jedoch kurz und präzise
+ Ausführung des Programms durch Algorithmen klar von eigentlicher Programmentwicklung getrennt
  + Wartung und Optimierung des Systems lässt sich unbhängig von eigentlichen Anwendung durchführen

**Funktionales Programmierparadigma**
+ Bsp: Lisp, Haskell
+ Programm besteht aus Reihe von Funktionsaufrufen
+ keine reine Wertzuweisung
+ eingesetzt für künstliche Intelligenz oder Compilerbau

**Logisches Programmierparadigma**
+ Bsp. Prolog
+ beruht auf mathematischer Logik
+ Programm ist Datenbasis, die aus Regeln und Fakten besteht
+ Interpreter greift auf diese Regeln und Fakten zurück und wendet sie an, um auf gewünschtes Ergebnis zu kommen

[Hoch](#inhalt)

---
---
---

## Objektorientiertes Programmierparadigma

+ Grundidee = Software soll so entwickelt werden, dass der Aufbau des Programms sich an Strukturen (Objekten) der Wirklichkeit ausrichtet
+ Umsetzung erfordert Einführung und Umsetzung verschiedener **Konzepte** 
+ soll erreichen, dass Qualitätsstandards ISO/IEC 9126 (z.B. Zuverlässigkeit, Änderbarkeit) bei der Entwicklung eingehalten werden
+ fördert Flexibilität und Wiederverwendbarkeit von Programmen
+ OOP-Sprachen: C++, Java, C#

### (Konzept) Abstraktion

+ zur besseren Verwaltung gleichartiger Objekte -> Konzept der Klasse

> Objekt ist ein abstrakter oder realer Gegenstand, welcher durch seinen Zustand (Eigenschaft mit konkreten Werten) und sein Verhalten (Anzahl bestimmter Methoden) beschrieben wird

+ Eigenschaften und Methoden gleichartiger Objekte werden abstrahiert und für diese Objekte jeweils eine Klasse generiert
  + Klasse = gemeinsame Eigenschaften und Methoden einer menge von gleichartigen Objekten
 
> Klasse ist eine Beschreibung (Vorlage, Bauplan) für eine menge gleichartiger Objekte
> Exemplar (Instanz) einer Klasse ist wiederum ein konkretes Objekt

**Beispiel**

![Alt Klasse](/LF08/images/class.png)<br>
*Abb. Eine Klasse von Wasserfahrzeugen*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

### (Konzept) Kapselung

+ beinhaltet Verbergen von Implementierungsdetails eines Objektes
+ auf Eigenschaften (Daten) eines Objektes kann nicht mehr zugegriffen werden sondern nur über definierte Schnittstellen
+ Daten sollen nicht in unerwarteter Weise gelesen oder geändert werden
+ Methoden eines Objektes bilden Schnittstelle
+ Zugriff auf einzelne Eigenschaften und Methoden wird durch Zugriffsmodifier geregelt
+ Zugriffsmodifier werden in Klassenbeschreibung von Objekten allen Komponenten zugeordnet

| Zugriffsmodifier | Beschreibung |
| -- | -- |
| public | uneingeschränkter zugriff auf Komponente |
| protected | kann nur innerhalb der eigenen Klasse und aus Klassen, die von dieser Klasse abgeleitet wurden zugegriffen werden |
| private | Zugriff ist nur innerhalb der Klasse erlaubt |

### (Konzept) Vererbung

+ Erzeugung einer neuen Klasse auf Basis einer bereits vorhandenen Klasse (Basisklasse, Elternklasse)
+ abgeleitete Klasse übernimmt sämtliche Eigenschaften und Methoden der Basisklasse und fügt neue hinzu
  + erweitert somit die Basisklasse

### (Konzept) Polymorphie
+ Vielgestaltigkeit
+ verschiedene Objekte bei Aufruf derselben Methode zeigen ein unterschiedliches Verhalten
+ ermöglicht, dass Referenz eines Objekttyps einer Basisklasse nicht nur Objekte der Basisklasse, sondern aller abgeleiteten Klassen zugewiesen werden können
+ erst in Laufzeit festgestellt, welche methoden zu welchem Objekt gehören

[Hoch](#inhalt)

---
---
---

## UML

> Unified Modeling language ist Modellierungssprache zur Spezifikation, visualisierung, Konstruktion und Dokumentation von Modellen für Softwaresysteme <br>
> kann auch zur Darstellung von Geschäftsmodellen genutzt werden

![Alt UML-Diagramme](/LF08/images/uml.png)<br>
*Abb. UML-Diagramme*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

+ Strukturdiagramme beschreiben den Zustand eines Systems -> sind statisch
  + stellen Aufbau und Beziehungen der Komponenten zu bestimmten Zeitpunkt dar
+ Verhaltensdiagramme bilden Aktivitäten und Abläufe im System ab
  + sind dynamisch und orientieren sich am Zeitablauf

### Übersicht UML-Diagramme

| Name | Beschreibung | Bild |
| -- | -- | -- |
| **Klassendiagramm** (Class Diagram) | wichtigster Diagrammtyp der UML <br> beschreibt Klassen und stellt Beziehungen zwischen diesen dar <br> stellt Bauplan für Objekte des Programms dar | ![Alt Klassendiagramm](/LF08/images/uml-class.png) |
| **Objektdiagramm** (Object Diagram) | Spezifizierung des Klassendiagramms <br> stellt Beziehungen der tatsächlich erzeugten Objekte an bestimmten Zeitpunkt zur Laufzeit dar <br> können als ergänzung aufgefasst werden | ![Alt Objektdiagramm](/LF08/images/uml-object.png) |
| **Komponentendiagramm** (Component diagram) | zeigt Abhängigkeiten und Organisation der Funktionseinheiten einer Software <br> beschreibt nächsthöhere Ebene über Klassen | ![ alt Komponentendiagramm](/LF08/images/uml-comp.png) |
| **Anwendungsfalldiagramm** (Use Case Diagram) | stellt Beziehungen zwischen Akteuren und Aktionen, welche die Akteure auf einem System abrufen können, dar <br> verdeutlicht die grundlegenden Anwendungsszenarien des Systems | ![Alt Anwendungsfalldiagramm](/LF08/images/uml-case.png) |
| **Aktivitätsdiagramm** (Activity Diagram) | dient zur Beschreibung des Verhaltens einer Klasse/Komponente <br> beschreibt Ablauf von Aktionen <br> ist in Darstellungsmöglichkeiten sehr flexibel | ![Alt Aktivitätsdiagramm](/LF08/images/uml-ad.png) |
| **Sequenzdiagramm** (Sequence Diagram) | Fokus liegt auf Interaktionen zwischen Objekten <br> Nachrichtenfluss und Nachrichtenaustausch zwischen Objekten <br> zeitlicher Ablauf der Nachrichten spielt eine Rolle <br> keine Informationen über Beziehungen der Objekte untereinander | ![Alt Sequenzdiagramm](/LF08/images/uml-seq.png) |

[Hoch](#inhalt)

---
---
---

### Anwendungsfalldiagramm

**Notationselemente und Aufbau**

![Alt Andwendungsfalldiagramm](/LF08/images/uml-ucd.png)<br>
*Abb. Notation des Anwendungsfalldaigramms*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

+ **System** = Systemgrenze, umfasst alle Anwedungsfälle, welche das System bereitstellt; für Anwendungsfälle muss später das System die entsprechenden Funktionen bereitstellen
+ **Actor** = Anwender/Akteuer, beschreibt, welche externen Benutzer das System verwenden, auch möglich, dass das System mit anderen externen Systemen interagiert (dann Rechteck)
+ **Use Case** = Anwendungsfall, beschreibt Aktion(en), die vom System für Benutzer bereitgestellt werden
+ **Association** = Assoziation, Beziehung zwischen Akteuren und Anwendungsfällen
+ **include** = Include-Beziehung, unbedingte Einbindung der Funktionalität eines Anwendungsfalls in einen anderen Anwendungsfall, Bsp A --include--> B: A schließt B mit ien, wenn A ausgeführt muss auch B ausgeführt werden
+ **extends** = Extend-Beziehung, bedingte Einbindung der funktionalität eines Anwendungsfalls in einen anderen Anwendungsfall, Bsp: A <--extends--B Anwendungsfall A kann durch B unter Bedingungen erweitert werden
+ **Generalization** = Generalisierung/Spezialisierung, zeigt Bezeihung zwischen allgemeinen und spezialisierten Element

**Beispiel**

![Alt Beispiel Anwendungsfalldiagramm](/LF08/images/uml-ucd-ex.png)

### Klassendiagramm

**Notatoinselemente und Aufbau**

![Alt Klassendiagramm](/LF08/images/uml-cl.png)<br>
*Abb. Notation des Klassendiagramms*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

+ Beziehungen zwischen Klassen werden dargestellt:
  + **Assoziation**: gibt an, dass Verbindung zwischen den Objekten von zwei Klassen besteht
    + Bsp. Maschine erstellt ein Werkstück
    + Verbindung über einfache Linie zwischen den Objekten
  + **Aggregation**: Variante der Assoziation, einzelne Objekte können auch unabhängig voneinander existieren
    + Bsp. Auto-Räder
    + Verbindung mit nicht-ausgefüllter Raute
  + **Komposition**: Variante der Aggregation, erfordert starken Besitz über Teilobjekte
    + wird das Ganze gelöscht, sind die Teilobjekte nicht mehr verfügbar
    + Verbindung über gefüllte Raute
    + Bsp: Haus-Räume
  + **Vererbung**: Ableitung von neuen Klassen aus bestehender Klasse, Eigenschaften einer Oberklasse werden an zugehörige Unterklassen weitergegeben

**Multiplizität**
+ sowas wie Kardinalität

| Beispiel | Beschreibung |
| -- | -- |
| 1 | Es gibt genau ein Objekt |
| 1, 3, 8 | Es gibt entweder ein, drei oder acht Objekte |
| 2..7 | Die Anazhl der Objekte kann von zwei bis sieben variieren |
| 0 .. * oder * | Es kann eine beliebige Anzahl von Objekten geben |

**Beispiel**

![Alt Beispiel eines KLassendiagramms](/LF08/images/uml-class-ex.png)<br>
*Abb. Beispiel Klassendiagramms*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>


## Prüfungsaufgaben

### UML, Aufgabe 2, Sommer22

![alt UML, Aufgabe 2, Sommer22](/LF08/images/uml-so22-01.png)

[Hoch](#übersicht-zu-objektorientierte-softwarelösungenlf8)

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
