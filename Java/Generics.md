---
tags: practical-cs java
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: true
aliases: Generics
linter-yaml-title-alias: Generics
date-of-creation: 2022-10-10
mod-date: 2022-10-10
---

# Generics

## Invarianz:
- Klassen, die im Vererbungsbaum weiter oben stehen, können keine Kindtypen als Typparameter akzeptieren
	→ Beispielsweise ist der Typ `Rocket<Integer>` kein Untertyp von `Rocket<Number>`
- Ableitungsbeziehung zwischen Typen überträgt sich nicht auf generische Klassen
