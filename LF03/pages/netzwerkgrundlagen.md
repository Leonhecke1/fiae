# Allgemeine Netzwerkgrundlagen

Inhalte zum Kapitel Netzwerkgrundlagen basierend auf dem Lehrbuch Kapitel LF3.

[zurück](/LF03/lf3.md)

## Inhalte

- [Allgemeine Netzwerkgrundlagen](#allgemeine-netzwerkgrundlagen)
  - [Inhalte](#inhalte)
  - [Übersicht über Netzwerkadressen](#übersicht-über-netzwerkadressen)
  - [MAC-Adressen](#mac-adressen)
  - [IP-Adressen](#ip-adressen)
    - [IPv4-Adressklassen](#ipv4-adressklassen)
    - [IPv4-Sonderadressen](#ipv4-sonderadressen)
    - [Berechnung Anzahl möglicher Clients in einem Netz](#berechnung-anzahl-möglicher-clients-in-einem-netz)
    - [Subnetting IPv4](#subnetting-ipv4)
  - [IPv6](#ipv6)
    - [Aufbau](#aufbau)
    - [Kürzung](#kürzung)
    - [Präfixe](#präfixe)
    - [Unicast-Adressen](#unicast-adressen)
      - [Globale Unicast-Adresse](#globale-unicast-adresse)
      - [Link-lokale Unicast-Adressen](#link-lokale-unicast-adressen)
    - [Subnetting IPv6](#subnetting-ipv6)
  - [OSI-Schichtmodell](#osi-schichtmodell)
  - [Netzwerkprotokolle](#netzwerkprotokolle)
    - [Domain Name System (DNS)](#domain-name-system-dns)
    - [Hypertext Transfer Protocol (HTTP)](#hypertext-transfer-protocol-http)
    - [File Transfer Protocol (FTP)](#file-transfer-protocol-ftp)
    - [Simple Mail Transfer Protocol (SMTP)](#simple-mail-transfer-protocol-smtp)
    - [Network File System (NFS)](#network-file-system-nfs)
    - [Server Message Block (SMB)](#server-message-block-smb)
    - [Internet Protocol Security (IPSec)](#internet-protocol-security-ipsec)
    - [Secure Shell (SSH)](#secure-shell-ssh)
    - [Telnet](#telnet)
    - [Dynamic Host Configuration Protocol (DHCP)](#dynamic-host-configuration-protocol-dhcp)
    - [Address Resolution Protocol (ARP)](#address-resolution-protocol-arp)
    - [Transport Layer Security (TLS)](#transport-layer-security-tls)
  - [Ports](#ports)
  - [Prüfungsaufgaben](#prüfungsaufgaben)
    - [IP, AP2 S022](#ip-ap2-s022)

## Übersicht über Netzwerkadressen

| Adresse | OSI-Layer | Adressaufbau | Bedeutung |
| -- | -- | -- | -- |
| MAC-Adresse | OSI-Layer 2 | 48 Bit <br> Schreibweise hexadezimal mit Trennzeichen <br> Bsp: AA-BB-CC-DD-EE-FF  | jedes Netzwerk-Interface hat eigene, eindeutige physikalische Interface-Adresse |
| IP-Adresse V4 | OSI-Layer 3 | 32 Bit <br> Schreibweise byteweise als Dezimalzahl mit Punkt als Trennzeichen zwischen den Bytes <br> Bsp: 10.255.0.1 | jeder Knoten im Netzwerk hat eine/mehrere IP-Adresse(n) |
| IP-Adresse V6 | OSI-Layer 3 | 128 Bit <br> Schreibweise 8 Wörter zu je 16 Bit in hexadezimal mit Doppelpunkt als Trennzeichen zwischen den Worten <br> Bsp: 2001:0123:5678:9ABC:DEF0:1234:5678:9ABC | jeder Knoten im Netzwerk hat mehrere eigene, eindeutige IPv6-Adressen |
| Ports | OSI-Layer 4 | 16 Bit <br> Schreibweise als Dezimalzahl <br> Bsp: 30123 | Ports adressieren Applikationen, Port 80 = http, Web-Server, Browser |

## MAC-Adressen

![Alt MAC-Adresse](/LF03/images/mac-adresse.png)<br>
*Abb. Aufbau einer MAC-Adresse*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

+ Adressen sind zweigeteilt in Herstellerkennung und fortlaufende Nummer des Herstellers
+ Schreibweise entweder mit Bindestrichen oder mit Doppelpunkten

**Besondere MAC-Adressen**
+ MAC-Broadkast-Adresse = FF-FF-FF-FF-FF-FF

## IP-Adressen

+ eine IPv4 Adresse besteht aus 4 gleich großen Teilen
+ diese 4 Teile bestehen aus 8 Bit welche dann in dezimaler Schreibweise angegeben werden
+ zweigeteilt in Netzwerkanteil und Host-Anteil
+ Trennung der Anteile erfolgt durch **Subnetzmaske**
  + Schreibweise der SM in CIDR = Slash-Notation, Präfix (/24, /16)
  + Schreibweise der SM in Dotted-Decimal-Notation = 255.255.255.0

### IPv4-Adressklassen

![Alt IP-Adressklassen](/LF03/images/adress-klassen.png)

**Private Adressbereiche**

+ Class A = 10.0.0.0 bis 10.255.255.255 /24
  + Anzahl Hosts = 2²⁴
+ Class B = 172.16.0.0. bis 172.31.255.255 /16
  + Anzahl Hosts = 2¹⁶
+ Class C = 192.168.0.0 bis 192.168.255.255 /8
  + Anzahl Hosts = 2⁸

### IPv4-Sonderadressen

| Bezeichnung | Adresse | Beschreibung |
| -- | -- | -- |
| Localhost / Loopback | 127.0.0.0 /8 | Adresse auf sich selbst <br> Ping auf eine Adresse aus diesem Bereich spricht den eigenen Rechner an |
| Net-ID | alle Host-Bits auf 0 | Net-ID von 10.1.2.3 /8 = 10.0.0.0 |
| Host-ID | Alle Net-Bits auf 0 | Host-ID von 10.1.2.3 /8 = 0.1.2.3 |
| Broadcast-ID | Alle Host-Bits auf 1 | Sendet an "alle" im Netz <br> Broadcast-ID von 10.1.2.3 /8 ist 10.255.255.255 |
| APIPA | eigener Bereich des Rechners <br> kommt vor, wenn DHCP nicht geht, oder statische Adresse bereits vergeben ist | 169.254.x.x |

### Berechnung Anzahl möglicher Clients in einem Netz


+ pro Oktet können "256" (2^8) IP-Adressen an Hosts vergeben werden
+ es müssen immer 2 Plätze vom Gesamtergebnis abgezogen werden, da die erste Adresse immer die Netzwerkadresse ist und die letzte Adresse immer die Brodcastadresse ist

```
Beispiel:

Netzwerkadresse: 192.168.12.0
Subnetzmaske: 255.255.255.0

-> es ist genau 1 Oktett als Geräteanteil verfügbar
-> Anzahl möglicher Clients = (2^8) - 2 = 256 - 2 = 254 Clients

Beispiel 2:

Netzwerkadresse: 192.168.15.0/20

-> 20 Bit sind der Netzwerkanteil
-> 32 - 20 = 12 Bit Netzwerkanteil
-> Anzahl möglicher Clients = (2^12)-2 = 4096 - 2 = 4094 Clients
```

### Subnetting IPv4

+ erhöht Anzahl verfügbarer Adressen
+ erhöhte Sicherheit durch übersichtliche Netze
+ bessere Netzwerkperformance

```
Beispiel:

Netzwerkadresse: 192.168.12.0
Subnetzmaske: 255.255.255.128

Anzahl der zu bildenden Subnetze: 2


-> Ein Oktett frei = 256 / 2(Anazhl der Subnetze) = 128
-> Zweites Subnetz fängt bei .128 an

Subnetz 1:
Subnetzadresse: 192.168.12.0
Brodcastadresse: 192.168.12.127
IP-Range: 192.168.12.1 - 192.168.12.126

Subnetz 2:
Subnetzadresse: 192.168.12.128
Brodcastadresse: 192.168.12.255
IP-Range: 192.168.12.129 - 192.168.12.254
```

```
Beispiel 2:

Netzwerkadresse: 192.168.12.0
Subnetzmaske: 255.255.255.192

Anzahl der zu bildenden Subnetze: 4


-> Ein Oktett frei = 256 / 4(Anzahl der Subnetze) = 64
-> Zweites Subnetz fängt bei .64 an
-> Drittes Subnetz fängt bei .128 an
-> Viertes Subnetz fängt bei .192 an

Subnetz 1:
Subnetzadresse: 192.168.12.0
Brodcastadresse: 192.168.12.63
IP-Range: 192.168.12.1 - 192.168.12.62

Subnetz 2:
Subnetzadresse: 192.168.12.64
Brodcastadresse: 192.168.12.127
IP-Range: 192.168.12.65 - 192.168.12.126

Subnetz 3:
Subnetzadresse: 192.168.12.128
Brodcastadresse: 192.168.12.191
IP-Range: 192.168.12.129 - 192.168.12.190

Subnetz 4:
Subnetzadresse: 192.168.12.192
Brodcastadresse: 192.168.12.255
IP-Range: 192.168.12.193 - 192.168.12.254

```

[Hoch](#netzwerkgrundlagen)

---

## IPv6

### Aufbau

+ eine IPv6-Adresse ist immer 128 Bit lang (Schreibweise kann gekürzt werden)
+ ein Block ist dabei immer 16 Bit lang
+ die Adresse ist Hexadezimal
+ die ersten 48 Bit (3 Blöcke) heißen **Standortpräfix**
+ die nächsten 16 Bit (1 Block) heißen **Teilnetz-ID**
+ die letzten 64 Bit (4 Blöcke) heißen **Schnittstellen-ID** oder **Token**

Beispiel:

```text
IPv6-Adresse: 2001:0db8:3c4d:0015:0000:0000:1a2f:1a2b

Standortpräfix:     2001:0db8:3c4d
Teilnetz-ID:        0015
Schnittstellen-ID:  0000:0000:1a2f:1a2b
```

### Kürzung

+ IPv6 Adressen können gekürzt werden:
  + alle führenden Nullen können weggelassen werden
  + Aufeinanderfolgende Blöcke mit Nullen können weggelassen werden dafür schreibt man dann `::`
  + **Dies kann nur 1 mal gemacht werden, am besten am längsten zusammenhängenden Block**
  + bei weiteren Null-Blöcken kann aus `:0000:0000:` `:0:0:` werden

Beispiel:

```text
Beispiel 1:
IPv6-Adresse:  2001:0db8:3c4d:0015:0000:0000:1a2f:1a2b

Gekürzte IPv6: 2001:db8:3c4d:15::12a2f:1a2b

Beispiel 2:
IPv6-Adresse:  4522:0db8:0000:0015:0000:0000:1a2f:1a2b

Gekürzte IPv6: 4522:db8:0:15::1a2f:1a2b

```

### Präfixe

+ Das Teilnetzpräfix umfasst immer 64 Bit. Diese Bit umfassen 48 Bit für das Standortpräfix, zusätzlich zu den 16 Bit für die Teilnetz-ID
+ Die folgenden Präfixe wurden für besondere Zwecke reserviert:
  + `2002::/16` -> Gibt an, dass ein 6to4-Routing-Präfix folgt
  + `fe80::/10` -> Gibt an, dass eine Link-lokale Adresse folgt
  + `ff00::/8`  -> Gibt an, dass eine Multicast-Adresse folgt

### Unicast-Adressen

+ IPv6 umfasst zwei unterschiedliche Unicast-Adresszuweisungen:
  + Globale Unicast-Adresse
  + Link-lokale Adresse
+ Der Typ einer Unicast-Adresse wird durch die linken (hochrangigen) Bit in der Adresse festgelegt, die das Präfix enthalten
+ Die Unicast-Adresse ist in der folgenden Hierarchie strukturiert:
  + Öffentliche Topologie
  + Standorttopologie (privat)
  + Schnittstellen-ID

#### Globale Unicast-Adresse

+ Die globale Unicast-Adresse ist weltweit einmalig im Internet

![Globale Unicast-Adresse](/LF03/images/global-uni-cast.png)


+ Öffentliche Topologie
  + Das Standortpräfix legt die öffentliche Topologie Ihres Netzwerks gegenüber einem Router fest
  + Sie beziehen das Standortpräfix für Ihr Unternehmen von einem ISP oder der Regional Internet Registry (RIR)
+ Standorttopologie und IPv6-Teilnetze
  + In IPv6 definiert die Teilnetz-ID ein administratives Teilnetz des Netzwerks und umfasst bis zu 16 Bit
  + Sie weisen die Teilnetz-ID während der Konfiguration eines IPv6-Netzwerks zu
  + Das Teilnetzpräfix legt die Standorttopologie für einen Router fest, indem es den Link angibt, dem das Teilnetz zugewiesen wurde
  + IPv6-Teilnetze gleichen konzeptuell IPv4-Teilnetzen, da jedes Teilnetz in der Regel einem Hardware-Link zugewiesen ist
  + IPv6-Teilnetz-IDs werden jedoch in hexadezimaler Notation, IPv4-Teilnetz-IDs hingegen in getrennter dezimaler Notation ausgedrückt
+ Schnittstellen ID
  + Die Schnittstellen-ID gibt eine Schnittstelle für einen bestimmten Knoten an
  + Eine Schnittstellen-ID muss innerhalb des Teilnetzes einmalig sein
  + IPv6-Hosts können das Neighbor Discovery-Protokoll verwenden, um eigene Schnittstellen-IDs automatisch zu erzeugen
  + Neighbor Discovery generiert basierend auf der MAC- oder der EUI-64-Adresse der Host-Schnittstelle automatisch die Schnittstellen-ID
  + Sie können Schnittstellen-IDs auch manuell zuweisen
  + Dies wird für IPv6-Router und IPv6-konforme Server empfohlen
  + Eine Anleitung zum manuellen Erstellen einer EUI-64-Adresse finden Sie in RFC 3513, Internet Protocol Version 6 (IPv6) Addressing Architecture

#### Link-lokale Unicast-Adressen

+ Die Link-lokale Unicast-Adresse kann nur auf dem lokalen Netzwerklink verwendet werden
+ Link-lokale Adressen sind außerhalb des Unternehmens ungültig und werden nicht erkannt
+ Das folgende Beispiel zeigt das Format einer Link-lokalen Adresse

![Link-lokale Unicast-Adresse](/LF03/images/link-lokale-unicast.png)

+ Ein Link-lokaler Präfix hat das folgende Format:
 + `fe80::Schnittstellen-ID/10`
+ `fe80`
  + Hexadezimale Darstellung des binären 10-Bit-Präfixes 1111111010
  + Dieses Präfix identifiziert den Typ der IPv6-Adresse als Link-lokal
+ Schnittstellen-ID
  + Hexadezimale Adresse der Schnittstelle, die in der Regel von der 48-Bit-MAC-Adresse abgeleitet wird

### Subnetting IPv6

[Hoch](#netzwerkgrundlagen)

---

## OSI-Schichtmodell
+ in Kommunikationstechnik Unterscheidung zwischen zwei Systemen
  + geschlossenes System = herstellerabhängiges System, welches individuelle firmenbezogene Protokolle, Zeichensätze, Übertragungssequenzen arbeitet
    + werden in der Regel vom Hersteller nicht veröffentlicht
    + Einbinden von Fremdsystemen nicht möglich
  + offenes System = Einhaltung bestimmter Richtlinien, die es erlauben, kompatible Geräte zu bauen, entsprechende Schnittstellenanpassungen zu schaffen
    + ermöglichen Einbindung
    + Herstellung eines einheitlichen Standards -> **Referenzmodell für die Kommunikation offener Systeme** -> ISO-Modell, OSI-Modell (Open System Interconnection)

> Die 7 Schichten des OSI-Referenzmodells standardisieren hardware- und softwaremäßig die Struktur der Kommunikation innerhalb eines offenen Kommunikationssystems

+ Schichten/Ebenen/Layer
+ jeder Schicht -> klar umrissene Aufgabe zugewiesen -> Zerlegung des komplexen Problems der Datenkommunikation innerhalb eines Kommunikationssystems in kleinere Probleme zerlegt
  + **Ebene 1-4** = transportorientierte Schichten
  + **Ebene 5-7** = anwendungsorientierte Schichten
  + Gesamtheit = Protokoll-Stapel

***Übertragung im OSI-Schichtenmodell**

![alt Übertragung im OSI-Schichtenmodell](/LF03/images/osi2.jpg) <br>

1. Vertikale Übertragung
   + durchläuft Paket jede einzelne Schicht -> vertikale Übertragung
   + jede Schicht fügt Protokollinformationen an Payload (Nutzdatenpaket) hinzu
     + wenn Informationen am Paketanfang -> Header
     + wenn Information am Paketende -> Trailer
   + Protokollinformationen einer höheren Schicht werden in niedrigeren Schicht als Nutzdaten betrachtet und transparent behandelt (werden nicht interpretiert)
   + auf Schicht 1 wird erzeugtes Nutzdatenpaket inklusive Protokollinformationen in technisch übertragbare Signale umgewandelt und über physikalisches Übertragungsmedium transportiert (Kupferkabel, LWL, Funk)
   + auf Empfangsseite durchläuft Paket umgekehrt die Schichten 1-7
   + auf Senderseite schichtweise hinzugefügte Protokollinformationen werden auf Empfängerseite wieder entfernt -> auf Empfängerseite in jeder Schicht interpretiert 
2. Horizontale Übertragung
   + jede Schicht der Senderseite knann nur mit ihr entsprechenenden Schicht auf Empfängerseite korrespondieren
   + rein logische Verbindung der Schichten, lediglich Schicht 1 ist physische Verbindung und Übertragung der Daten
   + jede Schicht erfüllt bestimmte Dienstleistungen (Services)
     + stellen eine Schicht der jeweils nächsten höheren zur Verfügung
     + hierbei wird auf Dienste der nächstniedrigeren Schicht zurückgegriffen
     + für Zugriffe sind Schnittstellen definiert, an denen bestimmte Dienste über Dienstzugangspunkte zur Verfügung gestellt werden
       + Service Access Points (SAP)

**Verortung der Geräte und Protokolle im OSI-Schichtenmodell**

![alt Geräte im OSI-Schichtenmodell](/LF03/images/osi.png)

| Schicht | Wesentliches Ziel der Schicht                                   |
|---------|-----------------------------------------------------------------|
| 7       | Anfragen werden von Anwendungen entgegengenommen und ausgeführt |
| 6       | Der Partner versteht die gleiche Sprache                        |
| 5       | Es werden Sitzungen zwischen Partnern durchgeführt.             |
| 4       | Nachrichten kommen (sicher) beim Partner(programm) an           |
| 3       | Nachrichten kommen im Zielrechner an                            |
| 2       | Nachrichten kommen sicher im Nachbarrechner an                  |
| 1       | Bits kommen im Nachbarrechner an                                |

[Hoch](#netzwerkgrundlagen)

---

## Netzwerkprotokolle

+ RFC-Standard = Request for comment; beschreiben Protokolle für viele Dinge 

![alt RFC-Standard](/LF03/images/rfc_standards.jpg)

1. TCP
   + Transmission Control Protocol
     + erlaubt Transport beliebiger Datenmengen in mehreren Paketen mit Absicherung und verkehrsabhängiger Flusskontrolle
     + verbindungsorientiertes Protokoll mit Phasen Verbindungsaufbau, Datenaustausch und Verbindungsabbaus
2. UDP
   + User Datagram Protocol
     + versendet "kleine Lieferungen" als einmalige Aufträge
     + verbindungsloses Protokoll

### Domain Name System (DNS)
+ Rechner im Internet mit Namen belegt und in Namensdomänen zusammengefasst
+ Name muss nur in einer solchen Domäne eindeutig sein
+ weltweit verteilte Datenbank
+ DNS läuft im Klartext und kann mitgelesen werden -> um Anfragen abzusichern, sollte DNS over TLS/HTTPS eingesetzt werden

> FQDN = Fully Qualified Domain Name; besteht aus TLD (Top Level Domain), Domain, Subdomain, Rechner

**Nameserver**
+ werden so konfiguriert, dass automatisch Update zum sekundären NS durchführen
+ verwaltet auch Adressen der für Domain zuständigen E-Mail-Server
+ lokale Nameserver bermindern Verkehrsaufkommen nach außen und entlasten Internetanbindung und übergeordnete Nameserver

### Hypertext Transfer Protocol (HTTP)
+ nimmt DNS zur Hilfe
+ am meisten eingesetzte Anwendungsprotokoll im Internet
+ mit HTTP erreichbare Teil des Internets = WEB
+ vereinfacht Internetkommunikation drastisch
+ auf Benutzer dargebotenen Dokumenten kann durch Mausklick auf Textstellen/Bilder zu weiteren Dokumenten verzweigt werden (Hypertext)
+ leichte Betätigung von Optionsschaltern, Ausfüllung von Datenfeldern
+ Dialog findet weitgehend in Klartext über TCP-Verbindung statt

| Status-Code | Bedeutung |
|-------------|-----------|
| 200 | OK (sieht man im Browser nie) |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 451 | Censored |

**HTTPS Hypertext Transfer Protocol Secure**
+ Kommunikationsprotokoll im WEB, um Daten abhörsicher zu übertragen
+ stellt Transportverschlüsselung dar
+ definiert zusätzliche Schicht zwischen HTTP und TCP

### File Transfer Protocol (FTP)
+ setzt auf TCP auf
+ realisiert Dienst ur Übertragung von DAteien zwischen verschiedenen Computersystemen mit unterschiedlichen Dateisystemen

### Simple Mail Transfer Protocol (SMTP)
+ dient zum Versand elektronischer Post
+ setzt auf TCP, Port 25 oder anderen zuverlässigen Transportsystemen auf (587, 2525, 3535)

**SMTPS Simple Mail Transfer Protocol Secure**
+ E-Mail-Transport via SMTP über SSL/TLS
+ ermöglicht Authentifizierung der Kommunikationspartner auf Transportebene, sowie Integrität und Vertraulichkeit der übertragenen Nachrichten
+ Port 465

### Network File System (NFS)
+ Verzeichnisse über Netz in andere Dateisysteme einzubinden
+ meist unter Unix zu finden

### Server Message Block (SMB)
+ Windows-Entsprechung von NFS
+ Netzprotokoll für Datei-, Druck- und Serverdienste
+ erlaubt Zugriff auf Dateien und Verzeichnisse, die sich auf anderen Computer befidnen
+ wird auch von Samba verwendet, um Kommunikation zwischen Unix und Windows zu ermöglichen

### Internet Protocol Security (IPSec)
+ Protokoll-Suite, die gesicherte Kommunikation über potentiell unsichere IP-Netze (z. B. Internet) ermöglichen soll 
+ arbeitet auf Vermittlungssicht
+ Ziel ist verschlüsselungsbasierte Sicherheit auf Netzwerkebene bereitzustellen
+ bietet durch verbindungslose Integrität, sowie Zugangskontrolle und Authentifikation der Daten Sicherheit
+ Gewährleistung der Vertraulichkeit sowie Authentizität der Paketreihenfolge durch Verschlüsselung

### Secure Shell (SSH)
+ kryptographisches Netzwerkprotokoll für sicheren Betrieb von Netzwerkdiensten über ungesicherte Netzwerke
+ macht entfernte Kommandozeile lokal verfügbar -> Fernwartung von entfernten Servern
+ neue Version SSH-2 bietet Datenübertragung per SFTP
+ Port: 22

### Telnet
+ veraltetes Netzwerkprotokoll
+ auf allen gängigen Betriebssystemen einsetzbar
+ nach Verbindungsaufbau wird Passwort abgefragt
+ Datenaustausch unverschlüsselt -> Passwort im Klartext
+ sollte nicht mehr genutzt werden

### Dynamic Host Configuration Protocol (DHCP)
+ ermöglicht Zuweisung der Netzwerkkonfiguration an Clients durch Server
+ Port 67, 68
+ ermöglicht angeschlossene Clients ohne manuelle Konfiguration der Netzschnittstelle in bestehendes Netz einzubinden
+ nötige Informationen (IP-Adresse, Netzmaske, Gateway, Name Server) werden automatisch vergeben

**Ablauf**
**D** Discover: Client schickt Discover-Paket man Broadcast, um verfügbare DHCP-Server zu lokalisieren
**O** Offer: DHCP schickt Paket mit freier IP-Adresse, MAC-Adresse des Clients, Subnetzmaske, IP-Adresse des DHCP
**R** Request: Client wählt aus erhaltenen Paketen seine gewünschten Datan aus, bestätigt frühere Parameter
**A** Ack(Acknowledged): DHCP übermittelt erneut das Paket und sendet weitere Parameter (DNS, SMTP, etc.)

### Address Resolution Protocol (ARP)
+ ermittelt zu Netzwerkadresse der Internetschicht die physische Adresse (Hardware-Adresse) der Netzzugangsschicht
+ speichert Zuordnung ggf. in ARP-Tabellen der beteiligten Rechner
+ Ermittlung von MAC-Adressen zu gegebenen IP-Adressen
+ bei IPv6 von Neighbor Discovery Protocol (NDP) ersetzt

### Transport Layer Security (TLS)
+ Vorgängerbezeichnung Secure Sockets Layer (SSL)
+ Verschlüsselungsprotokoll zur sicheren Datenübertragung im Internet
+ besteht aus TLS Handshake und TLS Record
  + Handshake = sicherer Schlüsselaustausch und Authentifizierung 
  + Reckord = Verwendung Schlüssel für sichere Datenübertragung

## Ports

| Port | Bezeichnung/Verwendung |
|------|------------------------|
| 20 | FTP-Datenübertragung |
| 21 | FTP-Verbindungsaufbau und Steuerung |
| 22 | SSH für verschlüsselte Fernwartung, Dateiübertragung und getunnelte Portweiterleitung |
| 23 | Telnet - unverschlüsseltes Textprotokoll z.B. für Fernwartung |
| 25 | Simple Mail Transfer Protocol (SMTP) E-Mail-Übermittlung zwischen E-Mail-Servern; Standard-MTA Port |
| 53 | Domain Name System (DNS) |
| 67/68 | Bootstrap Protocol (BOOTP) Server, Client; Bezug einer Netzwerkkonfiguration und eines Kernelnamens für einfache (etwa plattenlose) Geräte |
| 80 | Hypertext Transfer Protocol (HTTP); Datenübertragung auf Anwendungsschicht; Webseiten (Hypertext-Dokumente) aus dem WWW in einen Webbrowser zu laden |
| 110 | Post Office Protocol v3 (POP3); Abholen von E-Mails vom Provider; erlaubt nur Auflisten, Abholen und Löschen von E-Mails am E-Mail-Server |
| 143 | Internet Message Access Protocol (IMAP) - Mail-Management; Lesen und Verwalten von E-Mails; erweitert POP so, dass Benutzer Ordnerstrukturen und Einstellungen auf Server vornehmen/speichern können |
| 443 | Hypertext Transfer Protocol Secure over SSL/TLS (HTTPS); verschlüsselte Datenübertragung über ein Kommunikationsprotokoll im WWW; Daten sind abhörsicher; stellt Transportverschlüsselung dar |
| 465/587 | SMTP mit SSL/TLS; nur als MSA/für Mail-Clients, häufig mit STARTTLS (MSA = Mail Submission) |
| 993 | Internet Message Access Protocol over TLS/SSL (IMAPS) |
| 995 | Post Office Protocol 3 over TLS/SSL (POP3S) |

[Hoch](#netzwerkgrundlagen)

---

## Routing

+ Router verbinden zwei oder mehrere Netze miteinander
+ wertet netzwerk-Anteil der IP-Adresse aus
+ verfügen über **Routing-Tabellen** (=Weiterleitungstabellen) in denen ganze Adressbereiche hinterlegt sind

## Prüfungsaufgaben

### IP, AP2 S022

![Alt Aufgabe 1aa, Sommer22](/LF03/images/ip_so22-01.png)

[Hoch](#netzwerkgrundlagen)


---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
