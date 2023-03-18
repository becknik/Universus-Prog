---
tags: practical-cs java api struct
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: true
aliases: Collections
linter-yaml-title-alias: Collections
date-of-creation: 2022-07-14
mod-date: 2022-10-08
---

# Collections

## Collections
→ Utility Klasse für die *Collection* API

## Collection

### API:
- `default boolean removeIf(Predicate<? super E> filter)`
	→ Löscht alle Elemente, auf die das Prädikat zutrifft
- `boolean removeAll(Collection <? super E> coll)`
	→ Löscht $\text{c1}~\cap~\text{c2}$
- Optional: `boolean retainAll`
	→ Behält $\text{c1}~\cup~\text{c2}$

## List

### Nützliches:
- Schnell eine Liste erzeugen:
```java
List list = Arrays.asList("0 1 2 3 4 5".split(" "))
```
→ Ist mit einem *Vararg* überladen
→ Intern aufgebaut wie ein Array-Slice in Rust
```java
Points[] point = list.toArray( new Point[list.size()])
```
→ überträgt die Elemente einer Liste in ein vorgefertigtes Array

### API:
- `static <E> List<E> of(E… elements)`
	→ Erzeugt eine unmodifizierbare Liste aus den übergebenen Elementen
- `static <E> List<E> copyOf(Collection<? extends E> coll)`
	→ Liefert eine *unmodifizierbare* Kopie der Liste
- `boolean remove(Object o)` verwendet inter `equals(…)`
- `List<E> sublist(int fromIndex, int endIndex)`
	→ Liefert eine Referenz auf den angegebenen Abschnitt der Liste
	→ Mit `sublist.clear()` können Sequenzen aus der Liste gelöscht werden
- `default replaceAll(UnaryOperator<E> operator)`
	→ Ruft den Operator auf jedem Element der Liste auf

## Navigable Set

### Schnittstelle:
- `E lower(E e)`, `E heigher(E e)`, `E ceiling(E e)`, `E floor(E e)`
- `headSet(E toElement)`, `tailSet(E fromElement)`
- `subSet(…)`
- *pollLast(…)*, *pollFIrst(…)*
