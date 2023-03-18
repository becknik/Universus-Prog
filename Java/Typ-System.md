---
tags: practical-cs
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: true
aliases: Typ-System
linter-yaml-title-alias: Typ-System
date-of-creation: 2022-10-10
mod-date: 2022-10-10
---

# Typ-System

## Dynamische Typen
- Ein spezialisierter dynamischer Typ bei un-spezialisierten statischen Typ lässt sich nicht an einen Bezeichner binden, der vom Typ den spezialisierten dynamischen Typ hat
```java
Event event = new Workout();
Workout workout = event; //BAM! → ein Type-Cast ist notwendig
```