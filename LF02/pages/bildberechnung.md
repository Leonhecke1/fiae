# Bildberechnung

Inhalte für Bildberechnung (LF2)

[Zurück](/LF02/lf2.md)

## Inhalt

- [Grundwerte](#grundwerte)
- [Einfache Speicherplatzberechnung](#einfache-speicherplatzberechnung)
- [Speicherplatzberechnungen mit dpi](#speicherplatzberechnungen-mit-dpi)
- [Komplexe Speicherplatzberechnungen](#komplexe-speicherplatzberechnungen)

[Hoch](#bildberechnung)

---
---

## Grundwerte

### Auflösung

```text
Die Auflösung gibt in der Digitaltechnik an, wie fein abgestuft eine ursprünglich analoge Größe digital dargestellt werden kann, die vor der Weiterverarbeitung mit einem Analog-Digital-Umsetzer digitalisiert wird.
```

Quelle: <https://de.wikipedia.org/wiki/Aufl%C3%B6sung_(Digitaltechnik)>

### Farbtiefe

```text
Die Farbtiefe bestimmt eine wesentliche Eigenschaft von Raster- und Vektorgrafiken: die Differenzierung aller Helligkeits- und Farbwerte.
```

Quelle: <https://de.wikipedia.org/wiki/Farbtiefe_(Computergrafik)>

### Punktdichte

```text
Die Punktdichte, genannt auch Auflösung, ist bei der Bildreproduktion ein Maß für die Detailgenauigkeit einer gerasterten visuellen Darstellung und damit einer der Qualitätsaspekte des technischen Wiedergabeverfahrens. Punktdichten werden beispielsweise im Vierfarbdruck oder bei einer Bildschirmwiedergabe angegeben.

Übliche Einheiten der Punktdichte in der Praxis sind:

dpi
dots per inch, englisch für „Punkte pro Zoll“
```

Quelle: <https://de.wikipedia.org/wiki/Punktdichte>

### Bildrate

```text
Die Bildfrequenz (präziser Bildwechselfrequenz), oder auch Bildrate ist ein Begriff aus der Film- und Videotechnik. Sie bezeichnet die Anzahl der Einzelbilder, die pro Zeitspanne aufgenommen oder wiedergegeben werden und wird meist in der Einheit fps (englisch: frames per second), seltener BpS (Bildrahmen/Bilder pro Sekunde) oder Hz (Hertz) angegeben. Hochgeschwindigkeitskameras können schon mehrere Millionen davon besitzen. Diese werden dann oft für Zeitlupen gebraucht.
```

Quelle: <https://de.wikipedia.org/wiki/Bildfrequenz>

[Hoch](#bildberechnung)

---
---

## Einfache Speicherplatzberechnung

- der benötigte Speicherplatz für ein Bild lässt sich aus [Auflösung](#auflösung) und [Farbtiefe](#farbtiefe) berechnen
- dazu muss folgendes gerechnet werden:

```text
Speicherplatz = Gesamtzahl der Pixel * Farbtiefe

mit

Gesamtzahl der Pixel = Höhe * Breite

Speicherplatz = Höhe * Breite * Farbtiefe
```

Beispiel:

- Ein Bild hat folgende Werte:
  - Auflösung: 1200 x 600 px
  - Farbtiefe: 16 Bit

```text
Speicher = 1200 * 600 * 16 Bit
Speicher = 11520000 Bit
Speicher = 1440000 Byte
Speicher = 1,44 MB
```

[Hoch](#bildberechnung)

---
---

## Speicherplatzberechnungen mit dpi

- der benötigte Speicherplatz für ein Bild lässt sich aus Höhe des Bildes, Breite des Bildes, [Punktdichte](#punktdichte) und [Farbtiefe](#farbtiefe) berechnen
- dazu muss folgendes gerechnet werden:

```text
Speicherplatz = Höhe * Punktdichte * Breite * Punktdichte * Farbtiefe

Achtung!:

Höhe und Breite in Zoll, wenn Punktdichte in DPI gegeben ist!

1 Zoll = 2,54 cm
1 cm = 0,394 Zoll

Zoll = Inch
```

Beispiel Zoll:

- Ein Bild hat folgende Werte:
  - Höhe: 5 Zoll
  - Breite: 8 Zoll
  - Punktdichte: 100 dpi
  - Farbtiefe: 16 Bit

```text
Speicher = 5 Zoll * 100 dpi * 8 Zoll * 100 dpi * 16 Bit
Speicher = 6400000 Bit
Speicher = 800000 Byte
Speicher = 800 KB
```

Beispiel cm:

- Ein Bild hat folgende Werte:
  - Höhe: 50 cm
  - Breite: 85 cm
  - Punktdichte: 100 dpi
  - Farbtiefe: 24 Bit

```text
Höhe in Zoll = 50 cm / 2,54 = 19,685 Zoll
Breite in Zoll = 85 cm / 2,54 = 33,465 Zoll

Speicher = 19,685 Zoll * 100 dpi * 33,465 Zoll * 100 dpi * 24 Bit
Speicher = 158102046 Bit
Speicher = 19762755,75 Byte
Speicher = 19,76 MB
```

[Hoch](#bildberechnung)

---
---

## Komplexe Speicherplatzberechnungen

- Als Rechenweg wird einer der beiden oberen Wege genutzt, je nach Aufgabe muss der Rechenweg ergänzt werden

Beispiel:

- Eine Kamerastation hat folgende Werte:
  - Überwachungszeit: 06:00 Uhr bis 22:00 Uhr
  - Anzahl der Kameras: 4
  - Bildauflösung pro Bild: 1200 x 800 px
  - Farbtiefe: 16 Bit
  - Bildrate: 10 FPS
- Wie groß ist der Speicherbedarf pro Tag?

```text
Speicherbedarf pro Bild:
Speicher = 1200 * 800 * 16 Bit
Speicher = 15360000 Bit
Speicher = 1,92 MB

Laufzeit Pro Tag:
Laufzeit = (22 Uhr - 6 Uhr) = 16h
Laufzeit = 16h * 60 * 60 = 57600s

Bilder Pro Tag:
Bilder = 4 Kameras * 10 FPS * 57600s
Bilder = 2304000

Speicher gesamt = 1,92 MB * 2304000 Bilder
Speicher gesammt = 4423680 MB
Speicher gesamt = 4,42 TB
```

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
