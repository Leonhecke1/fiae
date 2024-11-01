# Datenbankdiagramme(LF8)

Inhalte zum Kapitel Datenbankdiagramme

Inhalte basierend auf dem Unterricht von Herrn Burggraf

[zurück](/LF08/lf8.md)

## Inhalte

- [Datenbankdiagramme(LF8)](#datenbankdiagrammelf8)
  - [Inhalte](#inhalte)
  - [Entity-Relationship-Modell - ERM](#entity-relationship-modell---erm)
    - [Grundelemente](#grundelemente)
  - [Relationales Datenbankmodell](#relationales-datenbankmodell)
    - [Wichtige Grundbegriffe](#wichtige-grundbegriffe)
    - [Normalisierung](#normalisierung)
  - [Überführung von ERM in RDM](#überführung-von-erm-in-rdm)
    - [Transformationsregeln](#transformationsregeln)

## Entity-Relationship-Modell - ERM

+ Grundlage für Datenbankentwurf
+ Planung, wie Datenbankstruktur aufgebaut und funktionieren soll
+ gängiger Standard für Datenmodellierung
+ Typisierung von Objekten, ihrer relationalen Beziehung untereinander und überführenden Attribute

### Grundelemente

![alt ERM ](/LF08/images/erm.png)
*Abb. Entity-Relationship-Modell* <br>
<sub>Datenbanken verstehen für Anfänger und Profis. </sub>

+ Entität = individuell identifizierbares Objekt der Wirklichkeit
+ Beziehung = Verknüpfung / Zusammenhang zwischen zwei / mehreren Entitäten
+ Attribut = Eigenschaft, die im Kontext zu Entität steht
+ Kardinalität = beschreibt Beziehung zwischen Attributen (1:1, 1:n, m:n)

**1:1**
+ jeder Datensatz in Tabelle A wird genau einem Datensatz in Tabelle B zugeordnet und umgekehrt
+ sollte in Modellierung vermieden werden, da solche Informationen meistens auch in einer Tabelle sein können
+ wird nur verwendet, um Tabelle aufgrund von Komplexität zu teilen, oder um Teil der Tabelle aus Gründen der Zugriffsrechte zu isolieren

**1:n**
+ häufigster Beziehungstyp in Datenbanken
+ einem Datensatz aus Tabelle A können mehrere passende Datensätze in Tabelle B zugeordnet sein
+ einem Datensatz in Tabelle B kann nur einem Datensatz in A zugeordnet sein

**m:n**
+ jedem Datensatz in Tabelle A mehrere passende Datensätze in Tabelle B zugeordnet und umgekehrt
+ können nur über eine dritte Tabelle *Verbindungstabelle C* realisiert werden
+ Verbindungstabelle enthält in der Regel nur Fremdschlüssel der anderen Tabellen
+ Primärschlüssel der Verbindungstabelle wird aus diesen beiden Fremdschlüsseln gebildet

![alt ERM-Beispiel ](/LF08/images/erm-example.png)
*Abb. Beispiel eines Entity-Relationship-Modells* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

[Hoch](#datenbankdiagrammelf8)

---
---

## Relationales Datenbankmodell

+ Sammlung von Tabellen (Relationen), die miteinander verknüpft (in Beziehung) sind

**Tabelle**
+ besteht aus Tabellennamen (Relationsname) sowie Spalten (Attribute, Felder) und Datensätzen (Zeilen, Tupel)

**Datensatz**
+ besteht aus Datenfeldern (= entsprechend der Spaltenbezeichnung)
+ in Datenfeld wird bestimmte Eigenschaft (Attributwert) des Objekts beschrieben

![alt Zwei Beispiele der Darstellung von Tabellen ](/LF08/images/reldatenmodell.png)
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Schlüssel**
+ Primary Key ist minimale Kombination von Spalten
  + dadurch lässt sich Datensatz eindeutig identivizieren
  + jede Tabelle benötigt genau einen Primärschlüssel
  + muss folgende Bedingungen erfüllen:
    + Eindeutigkeit: Werte des Schlüssels müssen eindeutig sein
    + Minimalität: sollte aus so wenig wie möglich Spalten bestehen (i.d.R. eine)
    + Unveränderbarkeit: Werte des Schlüssels sollten sich nicht ändern
+ Foreign Key ist Spalte einer Tabelle, die auf Primärschlüssel einer anderen/oder gleichen Tabelle verweist
  + Werte des Primärschlüssels werden in diese Spalte eingetragen
  + muss vom gleichen Datentyp wie Primärschlüssel sein
  + Tabelle kann einen/mehreren Fremdschlüssel besitzen

![alt Primär-/Fremdschlüssel im RDM](/LF08/images/rdm_keys.png)
*Primär-/Fremdschlüssel im RDM* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

### Wichtige Grundbegriffe

**Datenredundanz**
+ besteht, wenn dieselbe Information mehrfach in Datenbank vorhanden
+ Speicherplatzverschwendung
+ Gefahr, dass in Dateninkonsistenz resultiert

**Dateninkonsistenz**
+ Korrektheit der gespeicherten Daten 
+ Daten sind konsistent wenn widerspruchsfrei -> zeugt von hoher Qualität des Datenbestandes
+ Datenanomalien = Datenbestände sind nicht konsistent
+ können durch Datenredundanz verursacht werden (im Einzelnutzerbetrieb)
+ können durch Anomalien im Mehrbenutzerbetrieb entstehen

| Bezeichnung | Beschreibung |
|-|-|
| Änderungsanomalie | wenn Datenredundanz vorliegt und Daten geändert werden sollen, können beim Ändern einige Datensätze vergessen werden (nicht an allen Stellen geändert) |
| Einfügeanomalie | wenn bestimmte Daten nur in Verbindung mit anderen erfasst werden können <br> soll Mitarbeiter erfasst werden, muss er auch Abteilung zugewiesen werden |
| Löschanomalie | wenn beim Löschen ungewollt andere Daten auch gelöscht werden |

**Referenzielle Integrität**
+ besagt, dass Werte des Fremdschlüssels der Fremdschlüsseltabelle auch als Werte beim Primärschlüssel der Primärschlüsseltabelle vorhanden sein müssen
+ Vermeidung von Dateninkonsistenz
+ Datensatz muss erst mit einem entsprechenden Wert in der Tabelle mit Primärschlüssel vorhanden sein bevor Wert in Tabelle mit Fremdschlüssel eingetragen wird
  + mein Löschen -> umgekehrt: zuerst alle Datensätze aus Fremdschlüsseltabelle entfernt deren Wert mit dem des Primärschlüssels im Datensatz der Primärschlüsseltabelle übereinstimmt

[Hoch](#datenbankdiagrammelf8)

---
---

### Normalisierung
+ Verfahren zur Verringerung von Datenredundanz
+ verbunden mit den Zielen Anomalien zu vermeiden, Datenkonsistenz zu erhöhen
+ Nachteile:
  + viele kleine Tabellen, die die Leistung der Datenbank negativ beeinflussen können
  + viele künstliche Schlüssel und erforderliche zusätzliche Verknüpfungen -> System wird komplexer und somit größere Fehleranfälligkeit
  + zusätzliche Schlüssel erfordern zusätzlichen Speicherplatz, stellen Art von Redundanz dar

![alt Beispiel für Normalisierung](/LF08/images/normalisierung_ex.png)
*Beispiel für Normalisierung* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Erste Normalform**
> eine Tabelle liegt dann in der ersten Normalform vor, wenn alle Attribute der Tabelle nur einfache Werte aufweisen, d.h. die Werte atomar vorliegen

+ Tabelle darf keine Aufzählung von Werten enthalten
+ für jeden Wert muss neue Spalte angelegt werden

![alt Tabelle in der ersten Normalform](/LF08/images/normalform1.png)
*Tabelle in der ersten Normalform* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Zweite Normalform**
> eine Tabelle liegt dann in der zweiten Normalform vor, wenn sie der ersten Normalform genügt und alle Nichtprimärschlüsselattribute vom gesamten Primärschlüssel abhängig sind

+ angewandt, wenn Tabelle zusammengesetzten Primärschlüssel besitzt

![alt Tabelle in der zweiten Normalform](/LF08/images/normalform2.png)
*Tabelle in der zweiten Normalform* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Dritte Normalform**
> eine Tabelle liegt dann in der dritten Normalform vor, wenn sie der zweiten Normalform genügt und kein Nichtschlüsselattribut transitiv abhängig ist
+ transitive Abhängigkeiten = vermittelte/berechnete Abhängigkeiten (z.B. zwischen Nett-/Bruttopreis)

![alt Tabelle in der dritten Normalform](/LF08/images/normalform3.png)
*Tabelle in der dritten Normalform* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

[Hoch](#datenbankdiagrammelf8)

---
---

## Überführung von ERM in RDM

### Transformationsregeln

1. Ein Entitätstyp wird mit all seinen Attributen zu eweils einer Tabelle zusammengefasst
2. jede Tabelle erhält einen Primärschlüssel aus einem Attribut oder einer Kombination aus Attributen, welche im ERM gekennzeichnet wurden. Sind solche Attribute nicht vorhanden, dann wird ein künstlicher Primärschlüssel eingeführt.
3. Jede m:n-Beziehung wird in einer eigenen Tabelle abgebildet. Diese Tabelle enthält die Primärschlüssel der beteiligten Entitätstypen als Fremdschlüssel und die Attribute, welche der Beziehung direkt zugeordnet sind.
4. Die Umsetzung der 1:n-Beziehungen erfolg, indem der Primärschlüssel der einen Tabelle als Fremdschlüssel in die andere Tabelle eingefügt wird. 

![Alt Zweites Beispiel ERM](/LF08/images/erm-example2.png)
*Abb. Zweites Beispiel ERM* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

+ Abbildung zeigt Entitäten "Abteilung", "Mitarbeiter", "Projekt" mit entsprechenenden Attributen
+ pro Abteilung mehrere Mitarbeiter
+ pro Mitarbeiter mehrere Projekte -> m:n-Beziehung

**Schritte zur Erstellung des RDM**

1. Aus jedem Entitätstyp des ERM wird Tabelle mit entsprechenden Namen erstellt. <br> Die Attribute der einzelnen Entitätstypen werden zu Attributen der jeweiligen Tabelle.
2. Die Primärschlüssel werden festgelegt. Diese können in diesem Fall aus dem ERM übernommen werden.
3. Die 1:n-Beziehung zwischen Abteilung und Mitarbeiter wird ohne Veränderung übernommen. <br> Der Primärschlüssel AbtNr ist schon als Attribut in der Mitarbeitertabelle vorhanden und wird zum Fremdschlüssel.
4. Die m:n-Beziehung zwischen Mitarbeiter und Projekt wird aufgelöst und in zwei 1:n-Beziehungen überführt. <br> Dazu wird die m:n-Beziehung und deren Attribute in einer neuen Tabelle dargestellt (Kreuztabelle).

![Alt Fertiges RDM](/LF08/images/rdm-example.png)
*Abb. Fertiges RDM* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 2. Jahr. Westermann Verlag Braunschweig 2020. </sub>

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
