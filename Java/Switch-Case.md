---
tags: practical-cs
sources: Algorithmen und Datenstrukturen
cards-deck: Private::Books::Algorithmen und Datenstrukturen
completed: true
aliases: Switch-Case
linter-yaml-title-alias: Switch-Case
date-of-creation: 2022-09-11
mod-date: 2022-09-11
---

# Switch-Case

## Eigenschaften:
- Der `default`- Zweig wird immer dann ausgeführt, wenn *keine passende Verzeigung* gefunden wurde
- Ohne ein `break;` in den Case-Zweigen wird der nachfolgende Case-Zweig ausgeführt, als würde es sich um ein zusammenhängenden Programmblock handeln ("fall trough")
	→ Ab *Java SE 13*[^1] lässt sich das überflüssige `break;` umgehen, indem man `case → {…}` anstelle von `case: {…}` schreibt
- Ab *Java SE 14*[^2] lässt sich der *Switch-Case* Ausdruck auf die *reche Seite einer Zuweisung* schreiben, wobei der Ausdruck, der der Entität zugewiesen werden soll, am besten mit `yield …;` angegeben werden sollte
	→ Beispiele:
```java
	int number = switch(day) { … case THURSDAY, SATURDAY → {sout(8); yield 8;} };
	int number = switch(parameter) { case "One" → 1; … };
```

[^1]: [Oracle Docs](https://docs.oracle.com/en/java/javase/13/language/switch-expressions.html)
[^2]:Saake, G., Sattler, K.: Algorithmen und Datenstrukturen: Eine Einführung mit Java. 6. Auflage dpunkt-Verlag, 2021. S.101
