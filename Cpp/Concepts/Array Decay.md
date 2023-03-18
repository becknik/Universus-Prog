---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Array Decay
linter-yaml-title-alias: Array Decay
date-of-creation: 2023-01-01
mod-date: 2023-01-01
---

# Array Decay
- Array implicitly getting converted to pointers, where as there are differences between arrays & pointers
	- An array holds the size of the array, not just the pointer
	- $\&$ converts arrays $T[n]$ to the type $T(*)[n]$ - pointers $T*$ to $T**$
		→ $T**$ zeigt an die Adresse des Pointers, $T*$ an die Adresse des Referenz-Objekts
	- In Methodenköpfen werden $T[]$ automatisch zu $T*$ konvertiert
		→ $T*$ ist über $T[]$ vorzuziehen
