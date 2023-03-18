---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - const* Keywords
  - constexpr
  - constval
  - constinit
linter-yaml-title-alias: const* Keywords
date-of-creation: 2023-02-27
mod-date: 2023-02-27
---

# const* Keywords

## `constexpr`
- Defines an expression which can be evaluated at compile time
- Implicitly ensures `const`
- Indicate that functions can be called to produce constant expression

## `consteval`
- Forces compile-time evaluation of funtions
	→ Also called *immediate function*
	→ Can be seen als alternative of function-type macros

## `constinit`
- Used for initializing `static` or `thread-local` variables
- Does not ensure const destruction or *const-qualification*
- Can't be used in constant expression
- Ensures precompiled \& static ordering, rather than dynamic initialization and linking order

---
Sources:
- [cppreference: constinit](https://en.cppreference.com/w/cpp/language/constinit)
- [cppstories](https://www.cppstories.com/2022/const-options-cpp20/)
