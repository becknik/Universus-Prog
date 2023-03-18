---
tags: practical-cs
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: true
aliases: Extended Language Features
linter-yaml-title-alias: Extended Language Features
date-of-creation: 2022-10-08
mod-date: 2022-10-08
---

# Extended Language Features

## \*\*\*
- Ein Platzhalter für die primitiven Datentypen???

## Manuelle Nullung
- Der Compiler mach das automatisch mit den Werten `0`, `false` oder `null`

## Umgehen einer privaten Variable:
```java
public class Candy {  
	private String name;  
	
	// snip
	public boolean hasSameName(Candy that) {  
		return this.name.equals(that.name);  
	}
}
```
