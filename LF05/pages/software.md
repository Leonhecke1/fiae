# Software zur Verwaltung von Daten anpassen

Inhalte zum Kapitel Software zur Verwaltung von Daten anpassen

Inhalte basierend auf dem Lehrbuch Kapitel LF5 

[zurück](/LF05/lf5.md)

## Inhalte

- [Software zur Verwaltung von Daten anpassen](#software-zur-verwaltung-von-daten-anpassen)
  - [Inhalte](#inhalte)
  - [Overview](#overview)
    - [Softwareentwicklung](#softwareentwicklung)
  - [Darstellung von Algorithmen und Programmen](#darstellung-von-algorithmen-und-programmen)
    - [Sortieralgorithmen](#sortieralgorithmen)
  - [Prüfungsaufgaben](#prüfungsaufgaben)
    - [Bubblesort, AP1 SO22](#bubblesort-ap1-so22)

## Overview

> **Softwaredefinition nach IEEE Standard 610.12** <br>
> umfasst alle Programme, vorgeschriebene Abläufe, Dokumentation und Daten, die zum Betrieb eines Rechnersystems erforderlich sind

+ Systemsoftware: unterstützt/ermöglicht Ausführen von Anwendungssoftware (Betriebssysteme, Treiber)
+ Unterstützungssoftware: helfen bei der Entwicklung, oder erbringen nicht anwendungsspezifische Leistungen (Compiler, Editoren)
+ Anwendersoftware: umfasst alle Programme, die betriebwirtschaftliche, wissenschaftliche, technische oder branchenbezogene Anwendungen unterstützen (Lern- und Unterhaltungssoftware, Buchhaltungsprogramme)

### Softwareentwicklung

> Neuentwicklung oder Verbesserung und Anpassung von Softwaresystemen und die damit verbundenen Prozesse

**Customizing**
+ Anpassen von Standardsoftware an individuelle Wünsche des Kunden
+ Quellcode wird nicht verändert
  + Konfiguration: Anpassung der Software durch Auswahl und Konfiguratoin von entsprechenden Modulen
  + Parametrisierung: Anpassung der Software auf benötigten Funktionsumfang durch Setzen von Parametern; Teile der Software werden aktiviert/deaktiviert

**Erweiterungsprogrammierung**
+ Anpassung von Standardsoftware, wenn Möglichkeiten von Customizing nicht ausreichen
+ Erweiterung durch individuell entwickelte Programmteile, welche über definierte Schnittstellen mit Hauptprogramm verbunden werden

**Neuentwicklung**
+ Software wird komplett neu als Individualsoftware entwickelt

**Datenmigration**
+ Ersetzung eines vorhandenen Systems zur Verwaltung von Daten durch ein neues
+ Übertragung der Daten vom Altsystem aufs neue 

## Darstellung von Algorithmen und Programmen

> **Algorithmus** ist eine definierte und endliche Vorgehensweise, mit der ein Problem gelöst werden kann <br>
> besteht aus Anweisungen, welche Schritt für Schritt in definierten Reihenfolge abgearbeitet werden

### Sortieralgorithmen

**Blubbesort**

+ Sortieren durch Aufsteigen -> größte wird nach oben/hinten geschoben
+ Array wird immer paarweise von links nach rechts in einer "Bubble-Phase" durchlaufen
+ erste Zahl wird genommen und mit direktem Nachbarn verglichen
+ wenn nicht in Richtiger Reihenfolge -> werden miteinander getauscht
+ danach wird direkt nächstes Paar miteinander verglichen
+ solange bis Array vollständig durchlaufen, dann wiederholt

``` 
Pseudocode

funktion Bubblesort(A)
    Für jedes i von A.länge-1 bis 1
        Für jedes j von 0 bis i-1
            Wenn A[j+1] < A[j]
                vertausche A[j] und A[j+1]
```

```python
Python

def sorting(liste):

    size_count = len(liste)
    for i in range(1, size_count):
        for k in range(0, size_count-i):
            if (liste[k] > liste[k+1]):
                print(liste)
                swap(liste, k, k+1)
        print(liste)


def swap(liste, start, end):
    tmp = liste[end]
    liste[end] = liste[start]
    liste[start] = tmp


sorting_list = [5, 2, -1]

sorting(sorting_list)
print(sorting_list)
```

**Insertion Sort**

+ Sortieren durch Einfügen
+ durchläuft Array und entnimmt dabei aus unsortierten Eingabefolge ein Element und setzt es an entsprechend richtiger Stelle wieder ein
+ restliche Elemente des Arrays müssen hinter dem neu eingefügten Wert verschoben werden

```
Pseudocode

funktion Insertionsort(A)
    Für jedes i von 1 bis A.länge-1
        j := i
        einzufügen := A[i]
        Solange j > 0 && A[j-1] > einzufügen
            A[j] := A[j-1]
            j := j - 1;
        A[j] := einzufügen

```

```python
Python

def insertionSort(arr):
    n = len(arr)  # Get the length of the array
      
    if n <= 1:
        return  # If the array has 0 or 1 element, it is already sorted, so return
 
    for i in range(1, n):  # Iterate over the array starting from the second element
        key = arr[i]  # Store the current element as the key to be inserted in the right position
        j = i-1
        while j >= 0 and key < arr[j]:  # Move elements greater than key one position ahead
            arr[j+1] = arr[j]  # Shift elements to the right
            j -= 1
        arr[j+1] = key  # Insert the key in the correct position
  
# Sorting the array [12, 11, 13, 5, 6] using insertionSort
arr = [12, 11, 13, 5, 6]
insertionSort(arr)
print(arr)

```

**Quicksort**

```
Pseudocode

funktion Quicksort(A, links, rechts)
    Wenn links < rechts
        i := links
        j := rechts - 1
        p := rechts
 
        Solange i < j
            Solange A[i] <= A[p] && i < j
                i := i + 1
            Solange A[j] >= A[p] && i < j
                j := j - 1
            Wenn A[i] > A[j]
                vertausche A[i] und A[j]
 
        Wenn A[p] < A[i]
            vertausche A[p] und A[i]
            p := i
 
        Quicksort(A, links, p-1)
        Quicksort(A, p+1, rechts)
```

```python
Python

# Function to find the partition position
def partition(array, low, high):
 
    # choose the rightmost element as pivot
    pivot = array[high]
 
    # pointer for greater element
    i = low - 1
 
    # traverse through all elements
    # compare each element with pivot
    for j in range(low, high):
        if array[j] <= pivot:
 
            # If element smaller than pivot is found
            # swap it with the greater element pointed by i
            i = i + 1
 
            # Swapping element at i with element at j
            (array[i], array[j]) = (array[j], array[i])
 
    # Swap the pivot element with the greater element specified by i
    (array[i + 1], array[high]) = (array[high], array[i + 1])
 
    # Return the position from where partition is done
    return i + 1
 
# function to perform quicksort
 
 
def quickSort(array, low, high):
    if low < high:
 
        # Find pivot element such that
        # element smaller than pivot are on the left
        # element greater than pivot are on the right
        pi = partition(array, low, high)
 
        # Recursive call on the left of pivot
        quickSort(array, low, pi - 1)
 
        # Recursive call on the right of pivot
        quickSort(array, pi + 1, high)
 
 
data = [1, 7, 4, 1, 10, 9, -2]

size = len(data)
 
quickSort(data, 0, size - 1)
 
print('Sorted Array in Ascending Order:')
print(data)

```

**Selectionsort**

+ Sortieren durch Auswahl
+ entweder kleinstes, oder größtes Element auswählen

```
Pseudocode

funktion Selectionsort(A)
    Für jedes i von 0 bis A.länge-2
        min := i
        Für jedes j von i+1 bis A.länge-1
            Wenn A[j] < A[min]
                min := j
        Wenn min != i
            a := A[i]
            A[i] := A[min]
            A[min] := a

```

```python
Python

def selectionSort(array, size):
    
    for ind in range(size):
        min_index = ind
 
        for j in range(ind + 1, size):
            # select the minimum element in every iteration
            if array[j] < array[min_index]:
                min_index = j
         # swapping the elements to sort the array
        (array[ind], array[min_index]) = (array[min_index], array[ind])
 
arr = [-2, 45, 0, 11, -9,88,-97,-202,747]
size = len(arr)
selectionSort(arr, size)
print('The array after sorting in Ascending Order by selection sort is:')
print(arr)

```

[Hoch](#software-zur-verwaltung-von-daten-anpassen)

---


## Prüfungsaufgaben

### Bubblesort, AP1 SO22

![Alt Bubblesort, AP1 SO22](/LF05/images/bubblesort_so22-1.png)

---
---

@_Prüfungsvorbereitung für die Abschlussprüfung 2024_

von Jessica Hofmann, Leon Hecke und Peter Koban

---
---
