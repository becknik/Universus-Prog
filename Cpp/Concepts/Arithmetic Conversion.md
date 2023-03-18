---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Arithmetic Conversion
linter-yaml-title-alias: Arithmetic Conversion
date-of-creation: 2022-12-26
mod-date: 2022-12-26
---

# Arithmetic Conversion

## Usual conversion rules
→ Operands in lower category are converted to the $\max$ of all Operands
-   long double (highest)
-   double
-   float
-   unsigned long long
-   long long
-   unsigned long
-   long
-   unsigned int
-   int (lowest)
- $\langle$all other operands$\rangle$ will be converted to `int` due to *integral promotion*