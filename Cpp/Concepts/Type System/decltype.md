---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: decltype
linter-yaml-title-alias: decltype
date-of-creation: 2023-03-02
mod-date: 2023-03-02
---

# decltype

## Semantics
- `decltype(…)` resolves the type of a *entity* or *expression*:
	1. *Declared Type*: If the argument resolves to a local or namespace variable, a static variable or a function parameter
	2. *[[../Value Categories|Value Categories]]* Otherwise
		- [[../Value Categories#`lvalue`|lvalue]]: `T&`
		- [[../Value Categories|xvalue]]: `T&&`
		- [[../Value Categories|prvalue]]: `T`
	3. `decltype(auto)`: Resolves to the initialisier type, preserving the [[../Value Categories|Value Categorie]]

## Examples
```cpp
const int&& foo();
const int bar();
int i;
struct A { double x; };
const A* a = new A();
decltype(foo()) x1; // type is const int&&
decltype(bar()) x2; // type is int
decltype(i) x3; // type is int
decltype(a→ x) x4; // type is double
decltype((a→ x)) x5; // type is const double&, due (a→ x) is a lvalue expression
```

---
Sources:
- [Wikipeida](https://en.wikipedia.org/wiki/Decltype#Semantics) - 02.03.2023
