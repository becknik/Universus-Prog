---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Inline Functions
linter-yaml-title-alias: Inline Functions
date-of-creation: 2022-12-22
mod-date: 2022-12-22
---

# Inline Functions
→ [[Forward Declarations]]

## Principle
- Inline the content of a function into the place of calling
	→ In combination with [[../Compiler & Processing/Compiler Arguments|Constant Folding]], some calculations might be made on compile time
- May cause the executables to grow larger on multiple calls
- Best suitable for simple & short functions which are called more than once
- The therm historically evolved from the `inline` hint keyword on for compiler optimization
	→ `inline` is now used to display that a (function/) variable can have multiple definitions, as long as they are identical

## Taxonomy of Functions
- Must be expanded
	→ Functions inside classes, structs or union type definitions
	→ `constexpr` & `constval` functions
- May be expanded
	→ The compiler decides
- Can't be expanded
