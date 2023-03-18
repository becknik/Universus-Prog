---
tags: practical-cs java
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: false
aliases: Ausnahmen
linter-yaml-title-alias: Ausnahmen
date-of-creation: 2022-10-10
mod-date: 2022-10-10
---

# Ausnahmen

## Geprüft:
→ Nicht-`Runtime-Exceptions`
- Fehler, die unter gewissen Umständen auftreten können
	→ z.B. wenn sich der Aufrufer nicht an einen Vertrag hält
- Fehler, die nicht innerhalb des Programmes liegen
- Signalisieren, dass ein Fehler behoben und das Programm normal fortgesetzt werden kann

## Ungeprüfte Ausnahmen
→ `RuntimeException`
- Liegen i.d.R. einem Programmierfehler zugrunde
	→ "Selbst-Schuld-Fehler"
- Fliegen ohne verpflichtetes Auffangen durch Methodenkopf, sollten aber in JavaDoc angegeben werden !!!
- Große, moderne Frameworks arbeiten fast ausschließlich mit RuntimeExceptions, denn wenn es einen Fehler gibt, dann lässt sich hier schwer etwas beheben oder behandeln
	→ `NullPointerException` in größer
