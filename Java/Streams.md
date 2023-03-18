---
tags: java api functional
cards-deck: 
completed: true
aliases: Streams
linter-yaml-title-alias: Streams
date-of-creation: 2022-07-14
mod-date: 2022-09-11
mod-date: 2022-07-14
---

# Streams

## Eigenschaften:
- Beschreibt deklarativ durch die Fluent-API, **was** das Ergebnis sein soll
	- Das **wie** (z.B. ob parallel oder nicht) ist erstmal egal
- Da die *interne Implementierung* nicht angegeben wird, kann die Implementierung selbst bestimmen und dahingehend *optimieren*
- Setzen sich aus **Intermediär- und Terminaloperationen** zusammen:
- Verarbeitungsschritte:
	- *Filterung*
	- *Abbildung*
	- *Reduktion/ Komprimierung*: Terminieren den Stream durch die Reduktion auf einen Wert (z.B. die Summe)
- Intermediäroperationen sind [[../../Konzepte/Lazy]], Terminaloperationen [[../../Konzepte/Eager|Eager]]
	→ Alle (Intermediär-) Operationen werden so lange aufgeschoben, bis das Ergebnis von einer Terminal-Operation gebraucht wird
- Wie beim funktionalen Programmierparadigma sollten Intermediäroperationen **keine Seiteneffekte** aufweisen
- Streams sind *nicht strikt funktional*, da Terminaloperationen und auch manche Intermediäroperationen Zustände und damit Seiteneffekte aufweisen

## Schnittstelle - Quelloperationen:
- *Arrays.stream(T[] array)*
- *Stream.of(T… values)*: Macht intern dasselbe wie *Arrays.stream(…)*
- *Stream.generate(Supplier<T> s)*: Produziert einen endlosen Stream
- *Stream.iterate(…)*: Erzeugt einen (endlosen) Stream aus einer Funktion und einem Basiswert, wobei die Länge durch einen überladenes Prädikat begrenzt werden kann
	→ Beispiel: `Stream.iterate( BigInteger.valueOf(10_000_000), BigInteger i → i.isProbablyPrime(10), BigInteger i → i.add(BigInteger.ONE) )`
- *parallelStream()*: Nutzt die *Fork-&-Join-Framework*
	→ Bringt nicht immer einen Performance-Vorteil

## Schnittstelle - Intermediäroperationen Ohne Status:
- *peek(Consumer)*: Jedes Element wird "*einmal angeschaut*"
- *filter(Predicate)*: Nur Daten dürfen *passieren*, die das Prädikat *erfüllen*
	→ *takeWhile(Predicate)*, *dropWhile(Predicate)*: Nimm/ Lasse fallen solange Prädikat gilt:
	`Stream.of( 1, 2, -1, 3, 4, -1, 5, 6 ).dropWhile(i → {i > 0} ).skip(1).takeWhile( i → {i > 0} ).forEach( System.out::println ); // 3 4`
- *map(Function)*, *mapTo[Int,Long,Double]*: Der Bildmengen-Typ der Abbildung muss nicht gleich dem Eingangstyp sein
- *flatMap""*: Erzeugt inter einen Unter-Strohm aus den Eingangs-Strohm für eine Abbildung

## Schnittstelle - Intermediäroeprationen Mit Status:
- *limit(long)*, *skip(long)*
- *distinct()*: löscht alle doppelten Elemente
- *sorted(…)*: sortiert den Stream (mit oder ohne Comparator)

## Schnittstelle - Reduktionsoperationen:
- `T reduce(T, BinaryOperator<T>)`: Reduziert alle Paare des Streams schrittweise über den BinaryOperator, beginnend mit *T* und dem 0-ten Element des Streams

## Schnittstelle - Terminaloperationen:
- *forEach()*, *forEachOrdered*
	→ Hat im Vergleich zu einer existierenden Schleife kein *break* oder kann keine lokalen Variablen beschreiben
	→ Es sollte versucht werden, **Seiteneffekte** mit *forEarch* zu **unterlassen**
- *findFirst()*, *findeAny()*
- *allMatch*, *anyMatch*, *noneMatch*: Liefert ein boolean

## Schnittstelle - Terminaloperationen in Datenstrukturen:
- *Collector.of(…)*: baut einen Collector auf, der an *stream.collect()* übergeben werden kann
	→ *Collector* bietet standardmäßig eine Menge Collectoren, z.B. *toUnmodifiable()*, *toList()*, *joining()* für Strings …
	→ Gruppierende Methoden von Collectors sind *schrecklich* …
- `<R> R collect(Supplier<R>, BiConsumer<R, ? super T>, BiConsumer<R, R>)`:
	→ Supplier baut einen Container auf, BiConsumer fügt das Element in den Container(, Zusammenführung bei Parallelisierung)
- *toArray(IntFunction<A[]> generator)*: z.B. `.toArray( String[]:new )`
- *iterator()*
