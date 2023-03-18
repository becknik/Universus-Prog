---
tags: practical-cs prog cpp
sources: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines
cards-deck: Private::Prog::C++
completed: true
aliases: Casting
linter-yaml-title-alias: Casting
date-of-creation: 2023-02-27
mod-date: 2023-03-16
---

# Casting
→ Don't use C-style `(T) expr` or functional style `T(expr)` casts

## `dynamic_cast`
- [[Downcasting]]

## `reinterpret_cast`
- Tells the compiler to treat the *cast-type* as the *new-type*
	→ Purely compile-time due to only affecting the type representation
- Can't cast away `const`-ness or `volatile`

## `const-cast`
- Can cast away `const`-ness and `volatile`
	→ Don't ever cast away `const`

### When to use `static_cast` or `dynamic_cast`
- `static_cast`: Unless [[../Concepts/Type System/Downcasting|down casting]]
	→ Even on down casting side it can be used if 100% sure the types fit
