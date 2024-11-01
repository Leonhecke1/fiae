# Netzwerksicherheit
Inhalte zum Kapitel Netzwerksicherheit basierend auf dem Lehrbuch Kapitel LF3.

[zurück](/LF03/lf3.md)

## Inhalte

- [Netzwerksicherheit](#netzwerksicherheit)
  - [Inhalte](#inhalte)
  - [Proxy](#proxy)
  - [Reverse Proxy](#reverse-proxy)
  - [Firewall / DMZ](#firewall--dmz)
  - [Systemverfügbarkeit](#systemverfügbarkeit)
    - [Ausfallwahrscheinlichkeit p](#ausfallwahrscheinlichkeit-p)
    - [Erhöhen der Systemverfügbarkeit](#erhöhen-der-systemverfügbarkeit)


## Proxy

![Alt Proxy](/LF03/images/proxy.png)<br>
*Abb. Forward and Reverse Proxy*<br>
<sub>https://kinsta.com/wp-content/uploads/2020/08/Forward-Proxy-vs-Reverse-Proxy-Servers.png</sub>

+ schützt Benutzer und Netzwerk vor Angriffen aus dem Internet
+ geht als stellvertretendes Gerät für einzelne Rechner ins Internet 
+ bietet Möglichkeit zur Einrichtung von Sperrlisten für Seiten, die nicht besucht werden dürfen
  + Blacklisting
+ speichern meist Internetseiten
  + schnellerer, erneuter Aufruf der Seite
  + spart Datenverkehr mit Internet
  + beschleunigt das Surfen
+ einzelne Unternehmensrechner sind von außen nicht sichtbar -> nur Proxy ist sichtbar
  + verändert Datenpaket auf Layer 3
  + tauscht Source-IP-Address aus
  + inspiziert Datenpakete aus dem Internet und ersetzt Destination-Address wieder mit der des Clients
  + muss dafür Liste führen, welcher Client mit welchem externen Rechner eine Datenverbindung hat

## Reverse Proxy
+ verteilt Anfragen aus dem Internet an mehrere interne Server
+ verwaltet Virenscanner/Paketfilter
+ schützt Webserver und Anwendungen vor direkten Angriffen aus dem Internet
+ verbessert Leistung, indem er statische Inhalte cacht und Lastenausgleich durchführt

## Firewall / DMZ

+ schützt Rechner und Netzwerk vor Angriffen
+ inspiziert die ankommenden Pakete nach vorher festgelegten Regeln
  + können Herkunft anhand IP-Adresse, TCP/UDP-Ports, Pakete auf Inhalt prüfen
+ Pakete auf nicht geöffnete Ports werden verworfen
+ DMZ = Demilitarisierte Zone

## Systemverfügbarkeit

+ wichtige Kenngröße
+ Wahrscheinlichkeit mit der ein Gerät/Baugruppe ausfällt, ermöglicht Abschätzung wie betriebssicher ein System ist

![Alt Verfügbarkeiten](/LF03/images/verfuegbarkeiten1.png)<br>
*Abb. Systemverfügbarkeiten*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

![Alt Verfügbarkeiten2](/LF03/images/verfuegbarkeiten2.png)<br>
*Abb. Systemverfügbarkeiten2*<br>
<sub>Gratzke, J. (Hg.): IT-Berufe. Grundstufe 1. Jahr. Westermann Verlag Braunschweig 2020. </sub>

### Ausfallwahrscheinlichkeit p
+ Wahrscheinlichkeit von 1 bedeutet, dass Ereignis zu 100% eintritt

> **Beispiel** Wenn 100 Festplatten im Betrieb sind und im Laufe eines Jahres eine kaputt geht, dann ist die Ausfallwahrscheinlichkeit 1/100, p = 0,01 = 1 %

### Erhöhen der Systemverfügbarkeit
+ durch Redundanz = mehrfaches Vorhandensein einer Baugruppe/Systems wird Verfügbarkeit erhöht
  + erhöht zwar Wahrscheinlichkeit, dass ein Gerät ausfällt, verringert jedoch Wahrscheinlichkeit, dass beide ausfallen

>**Beispiel** Ein Netzteil hat eine Ausfallwahrscheinlichkeit von 0,001 (also 0,1 %). Wenn zwei Netzteile parallel betrieben werden, ist die Wahrscheinlichkeit, dass ein netzteil davon ausfällt 2 * 0,001 = 0,2 %. Die Wahrscheinlichkeit, dass beide gleichzeitig ausfallen ist aber 0.001 * 0.001 = 0,00001%. Damit ist das System um den Faktor 1000 besser geworden. Die Ausfallwahrscheinlichkeit des Systems wird damit um den Faktor 1000 reduziert.

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
