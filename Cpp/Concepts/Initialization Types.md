---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Initialization Types
linter-yaml-title-alias: Initialization Types
date-of-creation: 2023-02-08
mod-date: 2023-02-08
---

# Initialization Types

## Copy Initialization
```cpp
Fraction someFraction = Fraction(6);
//→ 
Fraction someFraction (Fraction(6));
//→ (*)
Fraction someFraction(6);
```
- (\*): [[../Compiler & Processing/Compiler Optimizations#Elision|Compiler Optimizations > Elision]] is not guaranteed prior to C++17
	→ Use should be avoided
