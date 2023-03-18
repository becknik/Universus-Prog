---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: noexcept
linter-yaml-title-alias: noexcept
date-of-creation: 2023-02-19
mod-date: 2023-02-19
---

# noexcept

## When to use
- Constructors, that are no-throw
- Overloaded assignment operators, that are no-throw
	→ Performance optimizations due to no need of stack unwinding
- Other functions to express a no-fail or no-throw guarantee
	→ Functions to be marked that they *must not* fail/ throw exceptions
	→ To be called by a destructor or other `noexcept` functions
- Do not, if unsure: removing `noexcept` is less crucial than adding it later
