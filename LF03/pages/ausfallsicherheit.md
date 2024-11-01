# Ausfallsicherheit
Inhalte zum Kapitel Ausfallsicherheit basierend auf dem Lehrbuch Kapitel LF3.

[zurück](/LF03/lf3.md)

## Inhalte

- [Ausfallsicherheit](#ausfallsicherheit)
  - [Inhalte](#inhalte)
  - [RAID-Systeme](#raid-systeme)
    - [RAID 0](#raid-0)
    - [RAID 1](#raid-1)
    - [RAID 4](#raid-4)
    - [RAID 5](#raid-5)
    - [RAID 6](#raid-6)
    - [RAID 01](#raid-01)
    - [RAID 10](#raid-10)
    - [RAID 51](#raid-51)
    - [RAID-Arten](#raid-arten)
    - [Neue Bezeichnung](#neue-bezeichnung)
    - [Berechnung der Leserate/Datendurchsatzrate](#berechnung-der-leseratedatendurchsatzrate)
    - [Hot-Spare-Platten](#hot-spare-platten)
    - [weitere Systeme, die mit RAID in Zusammenhang gebracht werden](#weitere-systeme-die-mit-raid-in-zusammenhang-gebracht-werden)
  - [Backup-Strategien](#backup-strategien)
    - [Möglichkeiten der Datensicherung](#möglichkeiten-der-datensicherung)
    - [Sicherungsarten](#sicherungsarten)
  - [Prüfungsaufgaben](#prüfungsaufgaben)
    - [RAID, AP1 SO-22](#raid-ap1-so-22)
    - [RAID, AP1 WS-22](#raid-ap1-ws-22)
    - [RAID, AP1 SO-23](#raid-ap1-so-23)
    - [Backup, AP1 SO-22](#backup-ap1-so-22)
    - [Backup, AP1 WS-22](#backup-ap1-ws-22)
    - [Backup, AP1 SO-23](#backup-ap1-so-23)

## RAID-Systeme

+ Redundant Array of Independant Discs (RAID) = redundantes Festplattenarray
+ Zusammenschaltung von zwei oder mehreren Festplatten
  + erscheinen systemseitig wie eine Platte
+ Daten werden gleichzeitig von mehreren Platten gelesen
  + verringert Ladezeit
  + erhöht Datendurchsatz beim gleichzeitigen Schreiben
  + Ausfallsicherheit durch Hinzufügen von Prüfsummen (Parität)
+ genormte Level = 0 bis 6
+ 1. Software-Raid
   + Zusammenwirken der Festplatten wird vom Betriebssystem gesteuert und überwacht
   + kein spezieller RAID-Controller erforderlich
   + zusätzliche Belastung der Systemressourcen (CPU, Bussysteme)
2. Hardware-Raid
   + separater RAID-Controller auf dem Motherboard
     + arbeitet CPU-unabhängig, erfordert keine zusätzlichen Systemressourcen
   + auch als Direct Attached Storage (DAS) bezeichnet -> wenn Controller und Festplatten im Anwender-Rechner eingebaut

![ALT RAID-Übersicht](/LF03/images/raid.jpg)

### RAID 0

![Alt RAID 0](/LF03/images/raid0.png)<br>
*Abb. RAID 0* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Alternative Bezeichnung**
Stripe Set

**Beschreibung**
+ beliebig große Festplatten oder Partitionen werden zu einem Volume zusammengeschalten
+ Daten auf mehrere Festplatten verteilt
+ höhere Datenrate beim Lesen/Schreiben

**Sicherheit**
+ keine Sicherheit
+ bei Ausfall einer Platte ist gesamtes Volume beschädigt

### RAID 1

![Alt RAID 1](/LF03/images/raid1.png)<br>
*Abb. RAID 1* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Alternative Bezeichnung**
Mirroring

**Beschreibung**
+ zwei Platten miteinander gespiegelt
+ einfache Schreibgeschwindigkeit
+ doppelte Lesegeschwindigkeit

**Sicherheit**
+ eine Platte kann ausfallen ohne Datenverlust

### RAID 4

![Alt RAID 4](/LF03/images/raid4.png)<br>
*Abb. RAID 4* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Alternative Bezeichnung**

Stripe Set with Parity

**Beschreibung**

+ mindestens drei Platten
+ eine Platte ist separate Paritätsplatte
+ Paritätsplatte wird stark beansprucht, da sie beim Schreiben auf jede einzelne Platte beschrieben wird

**Sicherheit**

+ eine Platte kann ausfallen ohne Datenverlust

### RAID 5

![Alt RAID 5](/LF03/images/raid5.png)<br>
*Abb. RAID 5* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Alternative Bezeichnung**

Stripe Set with Parity

**Beschreibung**

+ mindestens drei Platten
+ Parität der Paritätsplatte wird auf alle Platten verteilt
+ alle Platten gleichmäßig beansprucht

**Sicherheit**
+ eine Platte kann ausfallen ohne Datenverlust

### RAID 6

![Alt RAID 6](/LF03/images/raid6.png)<br>
*Abb. RAID 6* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Alternative Bezeichnung**

Stripe Set with Parity

**Beschreibung**

+ mindestens vier Platten
+ zwei Platten für verteilte Prüfsummen

**Sicherheit**
+ zwei Platten können ausfallen ohne Datenverlust

### RAID 01

![Alt RAID 01](/LF03/images/raid01.png)<br>
*Abb. RAID 01* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Beschreibung**

+ zwei RAID 0 werden mit einem RAID 1 gespiegelt

**Sicherheit**

+ jedes RAID 0 hat doppelte Ausfallwahrscheinlichkeit
+ durch Spiegelung darf 1 RAID 0 ausfallen

### RAID 10

![Alt RAID 10](/LF03/images/raid10.png) <br>
*Abb. RAID 10* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Beschreibung**

+ zwei Spiegelsysteme mit je zwei Platten über RAID 0 zusammengeschalten

**Sicherheit**

+ in jedem RAID 1 darf eine Platte ausfallen ohne Datenverlust
+ fallen 2 Platten in RAID 1 aus -> alle Daten verloren

### RAID 51

![Alt RAID 51](/LF03/images/raid51.png)<br>
*Abb. RAID 51 mit 6 Platten* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

**Beschreibung**

+ zwei RAID 5 über ein RAID 1 gespiegelt

**Sicherheit**

+ extrem hohe Ausfallsicherheit
+ ein RAId-5-Block kann komplett ausfallen
+ bei zweitem Block kann eine weitere Platte ausfallen
+ im Beispiel werden 6 Platten verbaut, jedoch nur Kapazität von 2 Platten verwendet

[Hoch](#ausfallsicherheit)

---

### RAID-Arten

> **Hardware-RAID**<br>
> Erweiterungskarte auf Mainboard verfügt über mehrere Festplattenanschlüsse<br>
> RAID-Funktionen werden auf spezialisierter Hardware bereitgestellt<br>
> Erweiterungskarte wird vom Betriebssystem wie einzige Festplatte gesehen<br>
> Vorteile: hohe Geschwindigkeit und meist zusätzlicher Festplattencache<br>
> Nachteile: Kosten für Controller

> **Software-RAID**<br>
> kann durch mehrere Betriebssysteme hergestellt werden<br>
> Rechner muss üer genügend Festplattenanschlüssen verfügen<br>
> Vorteile: Kosteneinsparung, da kein zusätzlicher Controller benötigt wird
> Nachteile: höhere CPU-Last

[Hoch](#ausfallsicherheit)

---

### Neue Bezeichnung

+ nicht mehr nach RAID-Level bezeichnet, sondern Anzahl benutzter Platten + Parity-Platten

> **Beispiel**<br>
> RAID(5,2)/RAID 5+2 = insgesamt fünf Platten, zwei Platten dürfen ausfallen <br>
> entspricht also RAID 6 mit fünf Platten

+ allgemeine Bezeichnung = RAID(n,m) / RAID n+m
  + n = Anzahl Platten gesamt
  + m = Anzahl Platten, die ohne Datenverlust ausfallen dürfen 

### Berechnung der Leserate/Datendurchsatzrate

+ Leserate/Datendurchsatzrate = n + Leserate Einzelplatte
+ Schreibrate gesamt = (n - m) * Schreibrate Einzelplatte
+ Gesamtspeicherkapazität des RAID-Systems = (n - m) * Einzelkapazität

> **Beispiel**<br>
> Ein RAID 5 besteht aus vier Platten zu je 1 TByte Kapazität. Die Gesamtkapazität ist die Summe der Kapazität von drei Platten, also 3 TByte, da die Kapazität von einer Platte für die Sicherheit benötigt wird. Der Datendurchsatz beim lesen ist viermal so groß wie bei einer Einzelplatte. Der Durchsatz beim Schreiben ist dreimal so groß wie bei einer Einzelplatte.

[Hoch](#ausfallsicherheit)

---

### Hot-Spare-Platten

+ Feature eines RAID-Controllers
+ zusätzliche Platten, die nicht vom RAID benötigt werden
+ wenn eine Platte defekt -> zusätzliche Platte wird automatisch in RAID-Verband integriert
+ fehlende Daten werden aus vorhandenden Daten berechnet und auf Reserveplatte geschrieben
+ während Schreibprozess -> erhöhte Zugriffszeiten auf RAID

### weitere Systeme, die mit RAID in Zusammenhang gebracht werden

+ JBOD - Just a Bunch of Disks
+ NRAID - NotRAID
  + verbinden mehrere Platten zu größeren, virtuellen Festplatte
  + keine Datenverteilung auf Platten
  + Platten werden der Reihe nach gefüllt
  + kein Geschwindigkeitsvorteil
  + keine Ausfallsicherheit

[Hoch](#ausfallsicherheit)

---

## Backup-Strategien

### Möglichkeiten der Datensicherung

| Bezeichnung | Beschreibung | Anwendung |
|--|--|--|
| Off-Premises Backup | Daten auf anderes Datacenter kopieren <br> Datacenter sollten mindestens 3 km voneinander entfernt sein <br> auch für große Datenmengen geeignet | sinnvoll bei Betrieben mit mehreren Niederlassungen/Rechenzentren |
| Bandsicherung | Daten auf Band sichern <br> Bandroboter nimmt sich bis zu vier Bandkassetten und steckt sie in Bandlaufwerke <br> Bänder können bei Bedarf wieder beschrieben werden <br> Backup-Schema: vier Tagesbänder, Montag bis Donnerstag -> wöchentlich überschrieben <br> vier Wochenbänder, die immer freitags überschrieben werden <br> Zwölf Monatsbänder, die immer am letzten Freitag des Monats überschrieben werden <br> Bänder sollten außerhalb des Serverraumes in Safe aufbewahrt werden | sinnvoll für Betriebe mit nur einer Niederlassung |
| Cloud-Backup | Daten auf Cloud-Speicher im Internet kopieren <br> preiswerter, einfacher, beliebter <br> Cloud-Anbieter übernimmt Schutz vor Datenverlust, Serverwartung, Klimaanlage, Stromversorgung| für alle Größenordnungen praktikabel |

### Sicherungsarten

**Speicherabbild-Backup, Image-Backup**
+ alle Datenblöcke einer Festplatte werden gespeichert
+ Inhalts-unabhängig
+ Dateisystem mit gesichert
+ gelöschte Dateien, die physisch noch auf Platte sind werden mitgesichert
+ verwendet von Ermittlungsbehörden in Computer-Forensik

**Voll-Backup, Komplettsicherung**
+ alle Dateien einer Platte werden gesichert

**Differenzielles Backup**
+ alle Dateien, die sich seit letzten Vollsicherung geändert haben
+ geänderte Dateien sind auf jedem Backup enthalten
+ zum Rücksichern wird letzte differenzielle Sicherung oder letzte vollbackup benötigt
+ Datenvolumen und Backup-Zeit steigen

**Inkrementelles Backup**
+ Alle Dateien, die sich seit letzten Vollsicherung oder inkrementellen geändert haben
+ nur Dateien der letzten Teilsicherung auf Band
+ beim Rücksichern werden alle Bänder benötigt
+ viele Bänder mit relativ wenig Daten, Backupzeit ist kurz

![Alt Backupverfahren](/LF03/images/backup.png)<br>
*Abb. Backupverfahren* <br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

[Hoch](#ausfallsicherheit)

---

## Prüfungsaufgaben

### RAID, AP1 SO-22

![Alt RAID, AP1 SO-22](/LF03/images/raid_so22-01.png)


**Lösung**

Aufgabe aa\)<br>
+ Größe des Cache - z.B. 1024 MiB
+ Durchsatz des Controllers - z. B. 6 Gbit/s
+ Art der Schnittstelle - z. B. PCIe Gen3
+ Anzahl HDD-Anschlüsse - z. B. 16 Festplatten

Aufgabe ab\)<br>
+ RAID 10

Aufgabe ac\)<br>
+ RAID 5

Aufgabe ad\)<br>
+ nichtbenötigte Dienste und Programme beenden
+ in einem separaten Netzwerk testen
+ fehlerfreie Test-Umgebung sicherstellen
+ praxisgerechte Tests auswählen

### RAID, AP1 WS-22

![Alt RAID, AP1 WS-22](/LF03/images/raid_ws22-01.png)

![Alt RAID, AP1 WS-22-02](/LF03/images/raid_ws22-02.png)

![Alt RAID, AP1 WS-22](/LF03/images/raid_ws22-03.png)

**Lösungen**

![Alt RAID, AP WS-22_lösung](/LF03/images/raid-ws22-lösung1.png)

Aufgabe da\)
+ 30 GiB * 0,4 (60 % Kompressionsrate) * 12 Monate * 10 Jahre = 1440 GiB gesamt in 10 Jahren

Aufgabe db\)
+ 1024 GiB/(30 GiB * 0,4 * 12 Monate) = 1024 GiB / 144 GiB/Jahr = 7,1 Jahre
+ Antwort: Der reservierte Speicher reicht für sieben Jahre (hier gab es einen Punkt für den Antwortsatz)

### RAID, AP1 SO-23

![Alt RAID, AP1 SO-23](/LF03/images/raid-so23-01.png)

![Alt RAID, AP1 SO-23-02](/LF03/images/raid-so23-02.png)

![Alt RAID, AP1 SO-23-03](/LF03/images/raid-so23-03.png)

**Lösung**

![Alt RAID, AP1 So-23-lösung01](/LF03/images/raid-so23-lösung01.png)

Aufgabe bb\)

```
12 Festplatten
10 * 1 TiB Festplatten für Daten
2 * 1 TiB Festplatten für Parität

```

Aufgabe bc\)
+ Hot-Spare-Festplatte ist eine in einem RAID-Verbund nicht verwendete Festplatte
+ fällt eine Festplatte aus, übernimmt die Hot-Spare-Festplatte im laufenden Betrieb die Rolle der defekten Festplatte

### Backup, AP1 SO-22

![Alt Backup, AP1 SO-22](/LF03/images/backup_so22_01.png)

![Alt Backup, AP1 SO-22_02](/LF03/images/backup_ss22_02.png)

**Lösungen**

Aufgabe d\)
```
copy *2022040?.log X:\debug
oder
copy *2022040*.log X:\debug
```

Aufgabe ea\)
+ Nur die erste inkrementelle Datensicherung bezieht sich auf das letzte vorhergegangene Vollbackup. Alle weiteren inkrementellen Datensicherungen beziehen sich jeweils auf die letzte vorhergegangene inkrementelle Datensicherung.
+ Bei der differenziellen Datensicherung beziehen sich jeweils alle differentiellen Datensicherungen auf das letzte vorhergegangene Vollbackup

Aufgabe eb\)
+ Die Pfadangabe ist unzureichend, deshalb kann das Program nicht gefunden werden.
+ Entsprechend die Pfadangabe beim Programmaufuruf mit angeben oder Umgebungsvariable %path um C:\Backup ergänzen.

### Backup, AP1 WS-22

![Alt Backup, AP1 WS-22](/LF03/images/backup_ws22-01.png)

![Alt Backup, AP1 WS-22_02](/LF03/images/backup_ws22-02.png)

**Lösungen**

![Alt Backup, AP1 WS-22_lösung](/LF03/images/backup_ws22-lösung01.png)

Aufgabe c\)
+ V2 & D3 & D5
+ letzte Vollsicherung wird immer benötigt. Da aufgrund des Fehlers am Mittwoch fälschlicherweise eine inkrementelle Sicherung stattfand, wurde das Archivbit aller gesicherten Dateien auf 0 gesetzt. Daher sichert die differenzielle Sicherung am Donnerstag nur die Dateien, die von Mittwoch auf Donnerstag geändert oder neu erzeugt wurden und deren Archivbit auf 1 steht

### Backup, AP1 SO-23

![Alt Backup, AP1 SO-23](/LF03/images/backup-so23-01.png)
![Alt Backup, AP1 SO-23-02](/LF03/images/backup-so23-02.png)

**Lösungen**

![Alt Backup, AP1 SO-23-lösung01](/LF03/images/backup-so23-lösung01.png)

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
