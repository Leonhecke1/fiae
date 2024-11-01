# Zahlensysteme

Inhalte zum Kapitel Zahlensysteme basierend auf dem Lehrbuch Kapitel LF2.

[zurück](/LF02/lf2.md)

## Inhalte
- [Adressen im Netzwerk unterscheiden](#zahlensysteme)

## Overview

![Alt Umrechnungen](/LF02/images/umrechnungen.png)<br>
*Abb. Umrechnung der Zahlensysteme*

## 1. Binär in Dezimal
Bsp:
1001 1111(2)
+ am Besten von rechts nach links
+ 1\*2^0 + 1\*2^1 + 1\*2^2 + 1\*2^3 + 1\*2^4 + 0\*2^5 + 0\*2^6 + 1\*2^7
+ = 1 + 2 + 4 + 8 + 16 + 128
+ = 159(10)

## 2. Dezimal in Binär
+ Dezimalzahl durch zwei rechnen und Rest übernehmen
+ Rest von unten nach oben ergibt Binärzahl

Bsp: 131(10)
```
131 / 2 = 65 R 1
 65 / 2 = 32 R 1
 32 / 2 = 16 R 0
 16 / 2 =  8 R 0
  8 / 2 =  4 R 0
  4 / 2 =  2 R 0
  2 / 2 =  1 R 0
  1 / 2 =  0 R 1
= 1000 0011(2)
```

## 3. Dezimal nach Hexadezimal
+ ähnlich wie Dezimal in Binär, nur dass man durch 16 rechnet

**Hexadezimalsystem**

| Dezimal | Hexadezimal |
|---------|-------------|
| 0       | 0           |
| 1       | 0           |
| 2       | 0           |
| 3       | 0           |
| 4       | 0           |
| 5       | 0           |
| 6       | 0           |
| 7       | 0           |
| 8       | 0           |
| 9       | 0           |
| 10      | A           |
| 11      | B           |
| 12      | C           |
| 13      | D           |
| 14      | E           |
| 15      | F           |
| 16      | 10          |
| 17      | 11          |
| 18      | 12          |
| 19      | 13          |
| 20      | 14          |
| 21      | 15          |
| 22      | 16          |
| 23      | 17          |
| 24      | 18          |
| 25      | 19          |
| 26      | 1A          |
| 27      | 1B          |
| 28      | 1C          |
| 29      | 1D          |
| 30      | 1E          |

Bsp: 247
```
247 / 16 = 15 R 7
 15 / 16 =  0 R 15 entspricht F
 Lösung: F7(16)
```

## 4. Hexadezimal nach Dezimal

Bsp: EF02C(16)

```
    E*16^4 + F*16^3  + 0*16^2 + 1*16^1 + C*16^0
=  14*16^4 + 15*16^3 + 0*16^2 + 1*16^1 + 12*16^0
=   917504 + 61440   + 0      + 32     + 12
=   978988(10)
```

## 5. Hexadezimal in Binär
+ Hexadezimalzahl in Blöcke aufteilen und einzelne Blöcke in Binär umrechnen

Bsp: 2BCE1(16)

```
 2    B    C    E    1
10 1011 1100 1110 0001
```

## 6. Binär nach Hexadezimal
+ Umkehrung von Hexa nach Binär

Bsp: 10 1011 1100 1110 0001

```
  10   1011 1100 1110 0001
= 2    11=B 12=C 14=E    1
= 2BCE1
```

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
