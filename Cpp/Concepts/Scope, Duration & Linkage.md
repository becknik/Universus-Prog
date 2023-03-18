---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - Scope & Duration & Linkage
  - Scope
  - Duration
  - Linkage
linter-yaml-title-alias: Scope, Duration & Linkage
date-of-creation: 2022-12-22
mod-date: 2023-03-16
---

# Scope, Duration & Linkage
→ [[Declaration & Definition|Definition]] must not occur multiple times due to the [[One Definition Rule]]
→ Summary: [Learn Cpp](https://www.learncpp.com/cpp-tutorial/scope-duration-and-linkage-summary/)

## Scope
- The section of accessibility/availability of instances form variables, parameters or user type definitions
- *Local Scope*: Can be accessed from the point of definition to the end to the block
- *File/ Global Scope*: Can be accessed from the point of declaration to the end of the file

## Duration
- The section between creation and destruction of a variable, parameter or user type definition
- *Automatic duration*: Duration like scope
- *`static` duration*: Created when the program starts & destroyed on it's end
	→ Applies on `static` global & local variables
	→ **Best Practice**: Never use to alter control flow for enhanced readability
- *Dynamic duration*: Created & destroyed on programmers request
	→ Dynamically allocated variables `int* x { new int{} }`

## Linkage
- Determines if multiple declarations of an identifier refer to the same entity

### No Linkage
- A identifier only refers to itself
- Example: (`static`) *local variables* or user-defined type definitions in blocks

### Internal Linkage
- Theoretically accessible from everywhere inside the file, but *not exposed to the linker*
	→ The [[One Definition Rule|One Definition Rule]] doesn't apply here due to the missing compiler exposure

#### Examples
- `static` non-`const` global variables
	→ Non-`static` non-`const` global variables have external linkage by default
- `const`/`constexpr` global variables
- `static` *functions*
- declarations inside an *unnamed namespace*

### [[Modules|Module]] Linkage
- The declaration is "attached" to a named module, but its not `export`ed

### External Linkage
- Identifier can be accessed everywhere via [[Forward Declarations]]

#### Examples
- Functions
- Non-`const` global variables
- `extern const` global variables, uninitialized just as forward declaration
- `inline constexpr` global variables #cpp17
- User-defined type declarations inside a namespace or in global scope
