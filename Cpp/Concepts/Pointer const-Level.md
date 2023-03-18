---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - Pointer const-Level
  - Top-Level
  - Low-Level
  - const-Level
linter-yaml-title-alias: Pointer const-Level
date-of-creation: 2022-12-27
mod-date: 2022-12-30
---

# Pointer const-Level
-> Confusing as hell: [Learn Cpp](https://www.learncpp.com/cpp-tutorial/type-deduction-with-pointers-references-and-const/)
→ Nomenclature applies equally to [[References & Pointers|References]]

## Non-`const`
- Non-`const` Pointer → Non-`const` lvalue: Assigned address & lvalue changeable
- Non-`const` Pointer → `const` lvalue: *Compilation error*

### Low-Level `const`
- Pointer to `cont` value → `const`/non-`const` lvalue: Assigned address changeable
```cpp
const T* pntr = {&x};
```

### Top-Level `const`
- `const` Pointer → non-`const` lvalue: Assigned lvalue changeable
- `const` Pointer → `const` lvalue: Neither changeable adress nor lvalue
	→ Basically a reference (?)
```cpp
T* const pntr = {&x};
```
