# Hardware

Inhalte für Hardware (LF2)

[Zurück](/LF02/lf2.md)

## Inhalt

- [Prozessor](#prozessor)
- [Arbeitsspeicher](#arbeitsspeicher)
- [Massenspeicher](#massenspeicher)
- [Anschlüsse](#anschlüsse)

[Hoch](#hardware)

---
---

## Prozessor

```text
Ein Computer-Prozessor ist ein (meist stark verkleinertes und meist frei) 
programmierbares Rechenwerk, also eine elektronische Schaltung, die gemäß 
übergebenen Befehlen Aktionen ausführt, wie andere elektronische Schaltungen und 
Mechanismen zu steuern. Es handelt sich dabei um eine hochkomplexe Form integrierter 
Schaltkreise (ICs). Da diese Art von Prozessoren im Vergleich zu den ersten 
programmierbaren Rechenmaschinen dramatisch miniaturisiert wurden, wird synonym auch 
von „Mikroprozessoren“ gesprochen. Gleiches gilt für Mikrocontroller, bei denen es 
sich um Prozessoren handelt, die einen vollständigen Computer enthalten und nicht 
nur eine CPU sind.
```

- kurz: CPU -> **C**entral **P**rocessing **Unit**

Quelle: <https://de.wikipedia.org/wiki/Prozessor>

### Aufbau CPU

Ein Prozessorkern besteht aus:

- Registern
- Rechenwerk (ALU)
- Steuerwerk
- Datenleitungen (Busse)

### CPU Cache

```text
Moderne Prozessoren, die in PCs oder anderen Geräten eingesetzt werden, die eine 
schnelle Datenverarbeitung benötigen, sind mit sogenannten Caches ausgestattet. 
Caches sind Zwischenspeicher, die die zuletzt verarbeiteten Daten und Befehle 
zwischenspeichern und so die rasche Wiederverwendung ermöglichen. Sie stellen die 
zweite Stufe der Speicherhierarchie dar. Normalerweise besitzt ein Prozessor 
heutzutage bis zu vierstufige Caches:

Level-1-Cache (L1-Cache): Dieser Cache läuft mit dem Prozessortakt. Er ist sehr 
klein (etwa 4 bis 256 Kilobyte), dafür aufgrund seiner Position im Prozessorkern 
selbst sehr schnell abrufbar.
Level-2-Cache (L2-Cache): Der L2-Cache befindet sich meist im Prozessor, aber nicht 
im Kern selbst. Er umfasst zwischen 64 Kilobyte und 12 Megabyte.
Level-3-Cache (L3-Cache): Bei Mehrkernprozessoren teilen sich die einzelnen Kerne 
den L3-Cache. Er ist der zweit-langsamste der vier Caches, aber meist bereits sehr 
groß (bis zu 256 Megabyte).
Level-4-Cache (L4-Cache): Wenn vorhanden, dann meist außerhalb der CPU auf einem 
Interposer oder dem Mainboard. Er ist der langsamste der vier Caches (nur selten 
über 128 Megabyte).
→ Hauptartikel: Memory Management Unit
Die Memory Management Unit übersetzt die virtuelle Adressen der in Ausführung 
befindlichen Prozesse in reale Adressen, für alle Prozessorkerne gleichzeitig, und 
stellt die Cache-Kohärenz sicher: Ändert ein Kern einen Speicherinhalt, so muss 
sichergestellt werden, dass die anderen Caches keine veralteten Werte enthalten. 
Abhängig von ihrer genauen Ansiedlung beinhalten die Cache-Stufen Daten entweder 
bezüglich virtueller oder realer Adressen.
```

Quelle: <https://de.wikipedia.org/wiki/Prozessor#Aufbau_/_Funktionale_Einheiten>

### Funktionsweise CPU

```text
Die Befehlsbearbeitung eines Prozessorkerns folgt prinzipiell dem Von-Neumann-Zyklus.

„FETCH“: Aus dem Befehlsadressregister wird die Adresse des nächsten 
Maschinenbefehls gelesen. Anschließend wird dieser aus dem Arbeitsspeicher (genauer: 
aus dem L1-Cache) in das Befehlsregister geladen.
„DECODE“: Der Befehlsdecoder decodiert den Befehl und aktiviert entsprechende 
Schaltungen, die für die Ausführung des Befehls nötig sind.
„FETCH OPERANDS“: Sofern zur Ausführung weitere Daten zu laden sind (benötigte 
Parameter), werden diese aus dem L1-Cache-Speicher in die Arbeitsregister geladen.
„EXECUTE“: Der Befehl wird ausgeführt. Dies können zum Beispiel Operationen im 
Rechenwerk, ein Sprung im Programm (eine Veränderung des Befehlsadressregisters), 
das Zurückschreiben von Ergebnissen in den Arbeitsspeicher oder die Ansteuerung von 
Peripheriegeräten sein. Abhängig vom Ergebnis mancher Befehle wird das 
Statusregister gesetzt, das durch nachfolgende Befehle auswertbar ist.
„UPDATE INSTRUCTION POINTER“: Sollte kein Sprungbefehl in der EXECUTE-Phase erfolgt 
sein, wird nun das Befehlsadressregister um die Länge des Befehls erhöht, sodass es 
auf den nächsten Maschinenbefehl zeigt.
Gelegentlich unterscheidet man auch noch eine Rückschreibphase, in der eventuell 
anfallende Rechenergebnisse in bestimmte Register geschrieben werden (siehe 
Out-of-order execution, Schritt 6). Erwähnt werden sollten noch sogenannte 
Hardware-Interrupts. Die Hardware eines Computers kann Anfragen an den Prozessor 
stellen. Da diese Anfragen asynchron auftreten, ist der Prozessor gezwungen, 
regelmäßig zu prüfen, ob solche vorliegen und diese eventuell vor der Fortsetzung 
des eigentlichen Programms zu bearbeiten.
```

Quelle: <https://de.wikipedia.org/wiki/Prozessor#Funktionsweise>

[Hoch](#hardware)

---
---

## Arbeitsspeicher

```text
Random-Access Memory (der oder das englisch random[-]access memory, zu Deutsch: 
„Speicher mit wahlfreiem/direktem Zugriff“ = Direktzugriffsspeicher), abgekürzt RAM, 
ist ein Datenspeicher, der besonders bei Computern als Arbeitsspeicher Verwendung 
findet, meist in Form von mehreren Speicherbausteinen auf einem Speichermodul. Die 
gängigsten Formen gehören zu den Halbleiterspeichern. RAM wird als integrierter 
Schaltkreis hauptsächlich in Silizium-Technologie realisiert und in allen Arten von 
elektronischen Geräten eingesetzt.
```

Quelle: <https://de.wikipedia.org/wiki/Random-Access_Memory>

### Aufbau RAM

![Aufbau Ram](/LF02/images/ram_layout.png)

Quelle: <https://courses.engr.illinois.edu/cs225/fa2022/resources/stack-heap/>

### Stack

```text
In der Informatik bezeichnet ein Stapelspeicher oder Kellerspeicher (kurz Stapel oder Keller, häufig auch mit dem englischen Wort Stack bezeichnet) eine häufig eingesetzte dynamische Datenstruktur. Sie wird von den meisten Mikroprozessoren direkt mithilfe von Maschinenbefehlen unterstützt.
```

Quelle: <https://de.wikipedia.org/wiki/Stapelspeicher>

![Stack](/LF02/images/stack.png)

Quelle: <https://de.wikipedia.org/wiki/Stapelspeicher#/media/Datei:ProgramCallStack2_en.svg>

```text
Ein Stapel kann eine theoretisch beliebige, in der Praxis jedoch begrenzte Menge von 
Objekten aufnehmen. Elemente können nur oben auf den Stapel gelegt und auch nur von 
dort wieder gelesen werden. Elemente werden übereinander gestapelt und in 
umgekehrter Reihenfolge vom Stapel genommen. Dies wird auch 
Last-In-First-Out-Prinzip (LIFO) genannt.

Dazu werden folgende Operationen zur Verfügung gestellt:

push (auch „einkellern“)
legt das Objekt oben auf den Stapel.
pop („auskellern“)
liefert das oberste Objekt und entfernt es vom Stapel. Bei manchen Prozessoren wie 
dem MOS Technology 6502 wird diese Aktion dagegen pull („herunterziehen“) genannt.
peek („nachsehen“)
liefert das oberste Objekt, ohne es zu entfernen (zuweilen auch top genannt, also 
„oben“).
```

Quelle: <https://de.wikipedia.org/wiki/Stapelspeicher#Funktionsprinzip>

### Heap

```text
Der dynamische Speicher, auch Heap (engl. für ‚Halde‘, ‚Haufen‘), Haldenspeicher 
oder Freispeicher ist ein Speicherbereich, aus dem zur Laufzeit eines Programms 
zusammenhängende Speicherabschnitte angefordert und in beliebiger Reihenfolge wieder 
freigegeben werden können. Die Freigabe kann sowohl manuell als auch mit Hilfe einer 
automatischen Speicherbereinigung erfolgen. Eine Speicheranforderung aus dem Heap 
wird auch dynamische Speicheranforderung genannt. Sie dient den Programmen dazu, 
über den vom Programmcode selbst und den fix reservierten Datenfeldern und dem Stack 
(Stapelspeicher) belegten Speicher hinaus noch zusätzlichen Pufferspeicher zur 
Verfügung zu haben.

Für die Anwendungsentwicklung bedeutet die dynamische Speicherverwaltung einen 
erheblichen zusätzlichen Aufwand und bildet eine häufige Fehlerquelle, insbesondere 
für Speicherlecks. Ein typischer Fehler ist zum Beispiel, dass Referenzen auf 
dynamisch belegten Speicher unbeabsichtigt überschrieben werden und der ursprünglich 
referenzierte Bereich nicht mehr freigegeben werden kann. Umgekehrt können auch 
Referenzen auf bereits wieder freigegebenen Speicher bestehen bleiben. Solche 
Referenzen bezeichnet man als hängende Zeiger.
```

Quelle: <https://de.wikipedia.org/wiki/Dynamischer_Speicher>

```text
Der Unterschied zum Stack besteht darin, dass beim Stack angeforderte 
Speicherabschnitte in der umgekehrten Reihenfolge wieder freigegeben werden müssen, 
in der sie angefordert wurden. Dies schränkt die Wiederverwendung nicht länger 
benötigter Stackbereiche ein; ebenso muss eine Funktion ihre Stack-Speicheransprüche 
vor ihrer Rückkehr zu der aufrufenden Funktion aufgeben. Beim Stack spricht man auch 
von automatischer Speicheranforderung. Der Zeitaufwand bei einer automatischen 
Speicheranforderung zur Laufzeit ist in der Regel deutlich geringer als bei der 
dynamischen Speicheranforderung. Da für den Stack meist nur ein kleiner 
Speicherbereich reserviert wird, kann bei intensiver Nutzung durch sehr große oder 
sehr viele Anforderungen ein unerwünschter Programmabbruch wegen Stack-Überlaufes 
erfolgen.
```

Quelle: <https://de.wikipedia.org/wiki/Dynamischer_Speicher#Unterschied_zum_Stack>

[Hoch](#hardware)

---
---

## Massenspeicher

```text
Als Massenspeicher werden im IT-Bereich Speichermedien bezeichnet, die große Mengen
an Daten dauerhaft speichern. Es handelt sich damit um nichtflüchtige Datenspeicher
Flüchtige Speicher wie konventionelles RAM sind nach dieser Definition keine
Massenspeicher, unabhängig von ihrer Größe.
```

Quelle: <https://de.wikipedia.org/wiki/Massenspeicher>

### SSD

- Ausgeschrieben: **S**olid **S**tate **D**rive

```text
Ein Solid-State-Drive bzw. eine Solid-State-Disk, kurz SSD (aus dem Englischen
entlehnt), seltener auch Halbleiterlaufwerk oder Festkörperspeicher genannt, ist ein
nichtflüchtiger Datenspeicher der Computertechnik. Die Bezeichnung Drive (englisch
für Laufwerk) bezieht sich auf die ursprüngliche und übliche Definition für dieses
Medium von Computern. Weil die SSD u. a. in PCs großteils klassische Festplatten
ersetzte, wird sie manchmal auch als SSD-„Festplatte“ bezeichnet. Die Bauform und
die elektrischen Anschlüsse können den Normen für Laufwerke mit magnetischen oder
optischen Speicherplatten entsprechen, müssen dies aber nicht. Sie können zum
Beispiel auch als PCIe-Steckkarte ausgeführt sein. Wird eine magnetische Festplatte
(engl. Hard Disk Drive, HDD) mit einem Solid-State-Speicher zu einem Gerät
kombiniert, spricht man von einer Hybridfestplatte (engl. hybrid hard drive, HHD, 
bzw. engl. solid state hybrid drive, SSHD).
```

Quelle: <https://de.wikipedia.org/wiki/Solid-State-Drive>

- Max. Kapazität: 256 TB
- Lebensdauer: je nach Qulität 1.000 - 5.000.000 Schreibvorgänge je Zelle
- deutlich schneller als HDD:
  - bis zu 6.500 MB/s lesend
  - bis zu 4.000 MB/s schreibend

### HDD

- Ausgeschrieben: **H**ard **D**isk **D**rive

```text
Ein Festplattenlaufwerk (englisch hard disk drive, Abkürzung HDD), früher auch Festplatten-Speichersystem oder 
Festplatten-System[1], oft auch als Festplatte oder Hard Disk (abgekürzt HD) bezeichnet, ist ein magnetisches Speichermedium 
der Computertechnik, bei welchem Daten auf die Oberfläche rotierender Scheiben (auch englisch „Platter“ genannt) geschrieben 
werden. Zum Schreiben wird die hartmagnetische Beschichtung der Scheibenoberfläche entsprechend der aufzuzeichnenden 
Information berührungslos magnetisiert. Durch die Remanenz (verbleibende Magnetisierung) erfolgt das Speichern der 
Information. Das Lesen der Information erfolgt durch berührungsloses Abtasten der Magnetisierung der Plattenoberfläche.

Im Unterschied zu sequentiell adressierten Speichermedien wie Magnetband oder Lochstreifen werden Festplatten den 
direktadressierbaren Speichermedien (englisch direct access storage devices, DASD) zugerechnet, da kein linearer Durchlauf 
erforderlich ist, um zu einer bestimmten Speicherstelle zu gelangen. Vor der Nutzung im PC-Bereich ab den 1980er Jahren 
wurden Festplatten vor allem im Mainframe-Bereich genutzt. Die Daten können in unterschiedlichen Organisationsformen auf den 
Festplatten gespeichert sein. CKD (count key data) organisierte Festplatten enthalten je nach Satzformat unterschiedlich 
lange Datenblöcke. FBA (fix block architecture) organisierte Festplatten enthalten gleich lange Datenblöcke, die 
üblicherweise 512 oder 4096 Byte groß sind. Ein Zugriff muss immer eine ganze Zahl von Blöcken umfassen.
```

Quelle: <https://de.wikipedia.org/wiki/Festplattenlaufwerk>

- Kapazität bis: 24 TB

[Hoch](#hardware)

---
---

## Anschlüsse

### HDMI

- High-Definition Multimedia Interface
- Überträgt hochauflösende Audio- und Videosignale
- Unterstützt auch die Übertragung von 3D-Videosignalen und Ethernet-Daten

### Display Port

- Bietet eine hohe Bandbreite für die Übertragung von Audio- und Videosignalen
- Kann mehrere Monitore über eine einzige Verbindung unterstützen
- Bietet eine hohe Kompatibilität mit verschiedenen Geräten und Auflösungen

### RJ45

- Stecker für Ethernet-Verbindungen
- Wird häufig für kabelgebundene Netzwerkverbindungen verwendet
- Unterstützt hohe Datenübertragungsraten und ermöglicht stabile Internetverbindungen

### DVI

- Überträgt digitale Videosignale in hoher Qualität
- Unterstützt verschiedene Arten von Verbindungen, einschließlich Single-Link und Dual-Link
- Wird häufig in Computermonitoren und Grafikkarten verwendet

### VGA

- Einer der ältesten Anschlüsse für Computermonitore
- Überträgt analoge Videosignale mit einer maximalen Auflösung von 640x480 Pixeln
- Wird zunehmend durch modernere Standards wie HDMI und DisplayPort ersetzt

### USB

- Universalanschluss für verschiedene Arten von Peripheriegeräten
- Bietet eine schnelle Datenübertragung und Stromversorgung für angeschlossene Geräte
- Verwendet für eine Vielzahl von Geräten, einschließlich Tastaturen, Mäusen, Druckern, externen Festplatten und mehr

[Hoch](#hardware)

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_
von Jessica Hofmann, John Konitzer, Leon Hecke und Peter Koban

---
---
