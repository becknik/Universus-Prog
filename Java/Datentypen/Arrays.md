---
tags: practical-cs java
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: true
aliases: Arrays
linter-yaml-title-alias: Arrays
date-of-creation: 2022-10-08
mod-date: 2022-12-22
---

# Arrays

## API
- `static <T> List<T> asList(T… a)`
	→ Auch mit einem `(T[] a)` überladen

## Warum nicht in Java verwenden:
- *Java* ist eine *dynamische Sprache* und deshalb nicht auf den Umgang mit Arrays angepasst
- Initialisierung wird zur Laufzeit durchgeführt
	→ Laufzeit- und Heapspeicher-intensiv
	- Exceptions, die von der Größe des Arrays abhängen, werden zur Laufzeit ausgewertet
		→ `array[-42] = 1;` wird erst zur Laufzeit geprüft & wirft eine `RuntimeException`…
	→ Bytecode der einzelnen Methoden darf durch JVM nur begrenzt lang sein (!!!), weshalb die Initialisierung von großen Arrays problematisch werden kann:
```java
int[] primes = {1,2,3};
// Code, der zur Lafzeit ausgewertet wird...:
primes[0] = 1;
primes[1] = 2
primes[2] = 3;
```
- Die Referenzierung eines geboxten Arrays durch ein ungeboxtes schlägt fehl
- Arrays können nicht ohne Umwege von generischen Typen (ohne Raw-Type) gebildet werden
	→  `new` funktioniert nicht
- Können auf Grund der statischen Initialisierung nicht dynamisch wachsen/ schrumpfen
	→ Durch das dynamische Sprache-Design von Java können hier leicht Fehler passieren
	→ Arrays kommen weniger als Datenstruktur, sondern eher bei variable Argumentlisten zum Einsatz
- Arrays sind weder richtiges Java-Objekt, noch primitiver Datentyp
	→ Liegen wie alle Objekte auf dem Heap, bieten aber keine Operationen an
- Man kann (nicht über ineﬀiziente und unschöne Umwege) keine Arrays von Typen mit gesetzten Typ-Parameter bilden
- Es existieren Datenstrukturen, die Collection erweitern & von Arrays abstrahieren

## Kovarianz:
- In Arrays von einem in der Klassenhierarchie weiter oben liegenden Klasse können auch Werte von spezialisierten Typen liegen
```java
Number[] arrayOfNumbers = new Number[3];
arrayOfNumbers[0] = Integer.valueOf(42);
arrayOfNumbers[1] = Double.valueOf(2.12d);
arrayOfNumbers[2] = Long.valueOf(Integer.MAX_VALUE+1);
```
