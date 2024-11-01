# SQL - Grundlagen

Inhalte zum Kapitel SQL-Grundlagen

Inhalte basierend auf dem Lehrbuch Kapitel LF5 

siehe auch [Datenbanken-und-Diagramme](/LF08/pages/database-diagrams.md)

[zurück](/LF05/lf5.md)

## Inhalte

- [SQL - Grundlagen](#sql---grundlagen)
  - [Inhalte](#inhalte)
  - [Overview](#overview)
  - [Syntaktische Grundlagen](#syntaktische-grundlagen)
  - [Datentypen](#datentypen)
  - [Wichtige Befehle im Überblick](#wichtige-befehle-im-überblick)
    - [Anlegen einer Datenbank](#anlegen-einer-datenbank)
    - [Anlegen einer Tabelle](#anlegen-einer-tabelle)
    - [Ändern einer Tabelle: Spalte hinzufügen](#ändern-einer-tabelle-spalte-hinzufügen)
    - [Ändern einer Tabelle: Datentyp einer Spalte ändern](#ändern-einer-tabelle-datentyp-einer-spalte-ändern)
    - [Ändern einer Tabelle: Spalte löschen](#ändern-einer-tabelle-spalte-löschen)
    - [Ändern einer Tabelle: Spalte löschen](#ändern-einer-tabelle-spalte-löschen-1)
    - [Löschen einer Tabelle](#löschen-einer-tabelle)
    - [Einfügen von Datensätzen](#einfügen-von-datensätzen)
    - [Ändern von Daten](#ändern-von-daten)
    - [Löschen von Datensätzen](#löschen-von-datensätzen)
    - [Datenabfrage mit SELECT](#datenabfrage-mit-select)
  - [Prüfungsaufgaben](#prüfungsaufgaben)
    - [Datenbank, AP1 SO22](#datenbank-ap1-so22)

## Overview

> Datenbanksprache, mit der in relationalen Datenbanken die Datenstrukturen definiert und die Datenbestände bearbeiten bzw. abgefragt werden können

| Sprache | Beschreibung |
| -- | -- |
| Datendefinitionssprache | umfasst alle Anweisungen, die verwendet werden, um Datenstrukturen und verwandte Elemente zu beschreiben/ändern/entfernen <br> Erzeugen/Verändern von Tabellen <br> Bsp: CREATE TABLE, DROP VIEW | 
| Datenbearbeitungssprache | umfasst alle Anweisungen, die dazu dienen, grundlegende Operationen an Datensätzen auszuführen <br> Auswählen/Einfügen/Löschen von Datensätzen <br> Bsp: SELECT, UPDATE, INSERT INTO |
| Datenüberwachungssprache | enthält Befehle, um an Nutzer der Datenbank Berechtigungen zu vergeben/zu entziehen <br> Bsp: GRANT, REVOKE |
| Transaktionsüberwachungssprache | stellen Datenintegrität sicher, indem logisch zusammenhängende anweisungen entweder komplett oder gar nicht ausgeführt werden <br> Bsp: COMMIT, ROLLBACK |

**Relationale Datenbanken**
+ MySQL
+ PostgreSQL
+ MariaDB
+ SQLite

**Nicht-Relationale Datenbanken**
+ MongoDB
+ Cassandra
+ Redis

## Syntaktische Grundlagen

+ nicht case-sensitive, jedoch Capslock = üblicher Standard
+ mit Semikolon beendet

| Sprachelement | Beschreibung |
| -- | -- |
| Anführungszeichen und Hochkommata | werden immer dann genutzt, wenn in Anweisung Zeichenketten enthalten <br> entsprechender Text erscheint in einfachen Hochkommata/Anführungszeichen <br> bsp: WHERE Name = "Maier" / WHERE Name = 'Maier' |
| Vergleichsoperatoren | kommen hauptsächlich in WHERE-Klauseln vor <br> beschreiben die Bedingungen, unter denen SQL Anweisung ausgeführt wird <br> =; >; >=; <; <=; <> |
| Logische Operatoren | auch bevorzugt in WHERE-Klauseln verwendet <br> können mithilfe von Klammern zu logischen Einheiten gebündelt werden <br> AND; OR; NOT |
| Rechenoperatoren | können an verschiedenen Stellen angewendet werden <br> durch Klammern wird mathematischer Ausdruck gezielt beschrieben |
| Zuweisungsoperator | ist identisch mit Vergleichsoperator <br> hauptsächlich genutzt, um Werte einer Spalte zu ändern |
| NULL | Wert NULL steht für nicht definierter Wert <br> wird verwendet um zu testen, ob Spalte einen nicht definierten Wert enthält <br> bsp: WHERE Ort IS NULL |

[Hoch](#sql---grundlagen)

---


## Datentypen

| ANSI-SQL-Datentyp | Beschreibung |
| --- | --- | 
| INTEGER, BIGINT | Ganze Zahlen |
| NUMERIC, NUMBER(n, m) | Festkommazahlen |
| FLOAT, DOUBLE | Gleitkommazahlen |
| VARCHAR(n) | Zeichenkette variabler Länge |
| CHAR(n), CHARACTER(n) | Zeichenkette fester Länge |
| DATE, TIME, TIMESTAMP | Datums- und Zeitangaben |
| BOOLEAN | Wahrheitswert |

## Wichtige Befehle im Überblick

### Anlegen einer Datenbank

**Syntax**

```
CREATE DATABASE Datenbankname;
```

### Anlegen einer Tabelle

**Syntax**

```
CREATE TABLE Tabellenname 
(
  Spaltenname1 Datentyp1 [ NOT NULL ] [ AUTO_INCREMENT ] [ PRIMARY KEY ]
  Spaltenname2 Datentyp2 [ FOREIGN KEY REFERENCES ]
  ...
);
```

**Erläuterung**

NOT NULL = Wert der Spalte darf nicht NULL sein <br>
AUTO_INCREMENT = Zahl wird bei jedem neuen Datensatz automatisch um eines erhöht <br>
PRIMARY KEY = Spalte wird zum Primärschlüssel <br>
FOREIGN KEY = Spalte wird zum Fremdschlüssel <br>
REFERENCES = Verknüpfung mit dem Primärschlüssel einer anderen Tabelle

[Hoch](#sql---grundlagen)

---

### Ändern einer Tabelle: Spalte hinzufügen

**Syntax**

```
ALTER TABLE Tabellenname ADD COLUMN Spaltenname Datentyp Optionen;
```

**Erläuterung**

Optionen = Angaben von zusätzlichen Optionen wie NOT NULL, FOREIGN KEY etc.

**Beispiel**

```
CREATE TABLE Person (PersonID INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Vorname VARCHAR(50),
    Groesse FLOAT,
    Gewicht FLOAT,
    Geburtsdatum DATE,
    OrtID INT,
    FOREIGN KEY (ORTID) REFERENCES Wohnohrt (ORTID));

```
[Hoch](#sql---grundlagen)

---

### Ändern einer Tabelle: Datentyp einer Spalte ändern

**Syntax**

```
ALTER TABLE Tabellenname MODIFY COLUMN Spaltenname Datentyp;
```
**Beispiel**

```
ALTER TABLE Person ADD COLUMN Bemerkungen VARCHAR(30);
```

### Ändern einer Tabelle: Spalte löschen

**Syntax**

```
ALTER TABLE Tabellenname DROP COLUMN Spaltenname
```
**Beispiel**

```
ALTER TABLE Person DROP COLUMN Bemerkungen;
```
[Hoch](#sql---grundlagen)

---

### Ändern einer Tabelle: Spalte löschen

**Syntax**
```
ALTER TABLE Tabellenname DROP COLUMN Spaltenname;
```

**Beispiel**
```
ALTER TABLE Person DROP COLUM Bemerkungen;
```
[Hoch](#sql---grundlagen)

---


### Löschen einer Tabelle 

**Syntax**

```
DROP TABLE Tabellenname;
```

**Beispiel**

```
DROP TABLE Person;
```
[Hoch](#sql---grundlagen)

---


### Einfügen von Datensätzen


**Syntax**

```
INSERT INTO Tabellenname (Spalte1, Spalte2, ...) VALUES (Wert1, Wert2, ...);
```

**Beispiel**

```
INSERT INTO Person (Vorname, Name, Gewicht) VALUES ("Hans", "Müller", 80.5);
```
[Hoch](#sql---grundlagen)

---

### Ändern von Daten

**Syntax**

```
UPDATE Tabellenname SET Spalte = Wert WHERE Bedingungen;
```

**Beispiel**

```
UPDATE Person SET Gewicht = 79.25 WHERE PersonID = 10;

/ Löschen von Werten eines Datensatzes:

UPDATE Person SET Gewicht = NULL WHERE PersonID = 21 OR PersonID = 43;
```
[Hoch](#sql---grundlagen)

---

### Löschen von Datensätzen


**Syntax**

```
DELETE FROM Tabellennamen WHERE Bedingungen;
```

**Beispiel**

```
DELETE FROM Person WHERE Name IS NULL;
```
[Hoch](#sql---grundlagen)

---


### Datenabfrage mit SELECT

![alt Datenabfrage über SELECT](/LF05/images/sql-select.png)
*Abb. Datenabfrage über SELECT* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Syntax**

```
SELECT [DISTINCT] Spalte1 [AS Alias], Spalte2, ... . FROM Tabelle1 [Alias], Tabelle2 [Alias] ... [WHERE Bedingungen] [GROUP BY Spalte [HAVING Bedingung]] [ORDER BY Spalte 1 [ASC | DESC], Spalte 2 ...]; 
```

**Beispiel**

```
SELECT Person.Name, Person.Vorname, Person.Geburtsdatum FROM Person;

alternativ:

SELECT P.Name, P.Vorname, P.Geburtsdatum FROM Person P;
```

+ mit "DISTINCT" können die Ergebnisse reduziert werden, sodass mehrfach auftretende Werte nur einmal angezeigt werden

```
SELECT DISTINCT Person.Name FROM Person
```

+ Abfragen mit Bedingungen

```
SELECT P.Name, P.Vorname FROM Person P WHERE P.Groesse > 1.80 AND P.Gewicht < 100 AND P.Name = 'Müller';

SELECT P.Name, P.Vorname FROM P WHERE P.Groesse BEWEEN 1.60 AND 1.80;
```

**Platzhalter**

+ `%` = steht für kein Zeichen, ein Zeichen oder mehrere Zeichen
+ `_` = repräsentiert immer genau ein Zeichen

```
SELECT P.Name, P.Vorname FROM Person P Where P.Name LIKE '%m%';

P.Name LIKE 'm%' = Name beginnt mit einem "m"
P.Name LIKE '_m%' = Name hat an zweiter Stelle ein "m"
P.Name LIKE '%m' = Name endet mit einem "m"
P.Name LIKE 'st_m%' = Name beginnt mit "st", dann folgt ein beliebiges Zeichen, darauf ein "m", gefolgt von beliebigen Zeichen
```

**Rechnungen**

```
SELECT P.Name, P.Vorname, (P.Gewicht / (P.Groesse * P.Groesse)) AS BMI FROM Person P;
```

**Sortieren der Ergebnismenge**

```
SELECT P.Name, P.Vorname FROM Person P ORDER BY P.Name DESC;
```

**Aggregatfunktionen und Gruppen**

| Aggregatfunktion | Bedeutung | Beispiel |
| -- | -- | -- |
| COUNT (Spalte) | liefert Anazahl der datensätze, die in Spalter einen definierten Wert enthalten <br> Werte die NULL sind werden nicht gezählt | `SELECT COUNT (P.PersonID) FROM Person P` |
| SUM (Spalte) | liefert Summe der Werte der Spalte | `SELECT SUM (P.Gewicht) FROM Person P` |
| MIN (Spalte) | liefert kleinsten Wert der Spalte | `SELECT MIN (P.Gewicht) FROM Person P` |
| MAX (Spalte) | liefert größten Wert der Spalte | `SELECT MAX (P.Groesse) FROM Person P` |
| AVG (Spalte) | liefert Durchschnittswert über alle Werte der Spalte | `SELECT AVG (P.Groesse) FROM Person P` |

**Gruppieren von Ergebnismengen**

**Syntax**

```
SELECT ... . FROM ... GROUP BY Spalte HAVING Bedingungen;
```

**Beispiel**

```
SELECT AVG (P.Groesse) FROM Person P GROUP BY P.OrtID;
```

**Der JOIN-Befehl - Abfragen über mehrere Tabellen**

![Alt Abfragen über mehrere Tabellen](/LF05/images/join.png)
*Abb. JOIN-Befehl - Abfragen über mehrere Tabellen* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Beispiele**

```
/ Beispiel ohne INNER JOIN

SELECT P.Name, P.Vorname, O.Name FROM Person P, Wohnort O Where O.OrtID = P.OrtID AND O.Name = 'Hamburg';

/ Beispiel mit INNER JOIN

SELECT P.Name, P.Vorname, O.Name FROM Person P INNER JOIN Wohnort O ON P.OrtID = O.OrtID WHERE O.Name = 'Hamburg';
```

**Datums- und Zeitfunktionen**

| Funktion | Beschreibung |
| -- | -- |
| date(timestring, modifier, ...) | gibt Datum im Format YYYY-MM-DD zurück |
| time(timestring, modifier, ...) | gibt Zeit in Format HH:MM:SS zurück |
| datetime(timestring, modifier, ...) | gibt Datum und Zeit im Format YYYY-MM-DD HH:MM:SS zurück |

**Beispiel**
```
SELECT date('now'); / gibt aktuelles Datum zurück
SELECT date('now', 'start of month', '+1 month', '-1 day'); / gibt den letzten Tag des aktuellen Monats zurück
```
[Hoch](#sql---grundlagen)

---

## Prüfungsaufgaben

### Datenbank, AP1 SO22

![Alt Datenbank, AP1 SO22](/LF05/images/sql_so22_01.png)

![Alt Datenbank, AP2 SO22_2](/LF05/images/sql_so22_02.png)

**Lösungen**

![Alt Datenbank, AP2 SO22_3](/LF05/images/sql_so22_lösung.png)

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
