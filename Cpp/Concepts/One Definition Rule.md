---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - One Definition Rule
  - ODR
linter-yaml-title-alias: One Definition Rule
date-of-creation: 2022-12-22
mod-date: 2022-12-30
---

# One Definition Rule
1. Within a given *file*, a function, variable, type, or template can only have one definition.
	 → Compiler: redefinition error
2. Within a given *program*, a variable or normal function can only have one definition. This distinction is made because programs can have more than one file (we’ll cover this in the next lesson).
	→ Linker: redefinition error
3. Types, templates, inline functions, and inline variables are allowed to have identical definitions in different files. We haven’t covered what most of these things are yet, so don’t worry about this for now -- we’ll bring it back up when it’s relevant.
	→ Undefined Behavior

## Exceptions
- `structs` in Header files
- Function [[Forward Declarations]]in Header files
