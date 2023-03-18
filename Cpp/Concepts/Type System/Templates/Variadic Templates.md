---
tags: practical-cs prog cpp cpp17
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Variadic Templates
linter-yaml-title-alias: Variadic Templates
date-of-creation: 2023-03-18
mod-date: 2023-03-18
---

# Variadic Templates

## Fold expressions
```cpp
template<typename… Values>
auto sum(Values const&… values)
{
    return /* necessary → */(0 + values + …)/* ← necessary */;
}
```
- The associativity is based on the side of the `…`
- The `(0 +` causes the compiler to not fail on 0 arguments

---
Source
- [Fluent{C++}](https://www.fluentcpp.com/2021/03/12/cpp-fold-expressions/)
