---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Asserts
linter-yaml-title-alias: Asserts
date-of-creation: 2023-03-17
mod-date: 2023-03-17
---

# Asserts
- `assert(true && "Descriptive message")` out of the `cassert` header
	→ Checks enabled by `NDEBUG` macro
	→ Internally calls [[Halts|std::abort]]
- `static_assert(true, "Descriptive message")`
- `std::unreachable` #Cpp23
