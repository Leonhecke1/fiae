# Speicherumrechnung

Inhalte für Speicherumrechnung (LF2)

[Zurück](/LF02/lf2.md)

## Inhalt

- [Grundgrößen](#grundgrößen)
- [Vielfache von Bit](#vielfache-von-bit)
- [Vielfache von Byte](#vielfache-von-byte)
- [Umrechnungen](#umrechnungen)

[Hoch](#speicherumrechnung)

---
---

## Grundgrößen

### Bit

- kleinste Einheit der Informatik
- kann zwei Stati annehmen: 0 oder 1

### Byte

- besteht aus genau 8 Bit
- kann genau 2⁸ Stati annehmen -> 256

[Hoch](#speicherumrechnung)

---
---

## Vielfache von Bit

- ein Bit kann vervielchfacht werden, dann enstehen KBit, MBit, ...
- wird bei Up-/Downloadgeschwindigkeiten häufig verwendet
- die Umrechnungszahl beträgt 1.000

Einheit | Ausgeschrieben | in Bit
-|-|-
Bit | Bit | 1
Kbit | Kilobit | 1.000
Mbit | Megabit | 1.000.000
Gbit | Gigabit | 1.000.000.000
Tbit | Terabit | 1.000.000.000.000
Pbit | Petabit | 1.000.000.000.000.000
Ebit | Exabit | 1.000.000.000.000.000.000

[Hoch](#speicherumrechnung)

---
---

## Vielfache von Byte

- man unterscheidet 2 Präfixformen:
  - Binärpräfixe (Basis 2)
  - Dezimalpräfixe (Basis 10)
- die Umrechnungszahlen betragen 1.024 (Binär) und 1.000 (Dezimal)

### Dezimalpräfix

Einheit | Ausgeschrieben | in Bit
-|-|-
Byte | Byte | 1
KB | Kilobyte | 1.000
MB | Megabyte | 1.000.000
GB | Gigabyte | 1.000.000.000
TB | Terabyte | 1.000.000.000.000
PB | Petabyte | 1.000.000.000.000.000
EB | Exabyte | 1.000.000.000.000.000.000

### Binärpräfix

Einheit | Ausgeschrieben | in Bit
-|-|-
Byte | Byte | 1
KiB | Kibibyte | 1.024
MiB | Mebibyte | 1.048.576
GiB | Gibibyte | 1.073.741.824
TiB | Tebibyte | 1.099.511.627.776
PiB | Pebibyte | 1.125.899.906.842.624
EiB | Exbibyte | 1.152.921.504.606.846.976

[Hoch](#speicherumrechnung)

---
---

## Umrechnungen

### Bit - Byte

- 1 Byte entspricht 8 Bit

Beispiele:

- Wie viel Bit sind 14 Byte?

```text
14 Byte * 8 = 112 Bit
```

- Wie viel Byte sind 64 Bit?

```text
64 Bit / 8 = 8 Byte
```

### Dezimalpräfix - Binärpräfix

- am einfachsten ist es jeweils auf Byte herunter zu rechnen und dann wieder hoch

Beispile:

- Wie viel MiB sind 12 MB ?

```text
12 MB * 1.000² = 12.000.000 Byte
12.000.000 Byte / 1024² =  11,44 MiB
```

- Wie viel GB sind 14,5 TiB

```text
14,5 TiB * 1.024⁴ = 1.5942919 * 10¹³ Byte
1.5942919 * 10¹³ Byte / 1.000³ = 15942.919 GB
```

#### Formeln zum direkten rechnen

- nach Binärpräfix:

```text
B... Binärpräfixvorsilbenexponent
D... Dezimalpräfixvorsilbenexponent

Binärpräfix = Dezimalpräfix / (1024^B/1000^D)
```

- nach Dezimalpräfix:

```text
B... Binärpräfixvorsilbenexponent
D... Dezimalpräfixvorsilbenexponent

Dezimalpräfix = Binärpräfix / (1000^D/1024^B)
```

[Hoch](#speicherumrechnung)

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
