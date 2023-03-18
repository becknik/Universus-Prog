---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: References & Pointers
linter-yaml-title-alias: References & Pointers
date-of-creation: 2022-12-27
mod-date: 2022-12-30
---

# References & Pointers
→ [[Pointer const-Level]]

## References
→ Are generally (outside of dangling references) considered safe
- Provide implicit indirect access to another object
- Initialization by `T& ref{t_entity}`
	→ Must be initialized, when they are non-`const`
- A `const`-reference is eligible to reference modifiable, not-modifiable & [[Value Categories|rvalue]] variables
- To get a memory address from a reference `&ref` must be called
- Can't be reseated, due to statically binding to an object

## Pointers
→ Are chosen for flexibility
- Provide implicit access to a objects storage address
- Initialization by `T* pntr{&t_entity}`
	→ May not be initialized, hence might cause unexpected behavior
- Pointed objects value is accessed explicitly by deferring with `*pntr`
- On what is pointed can be changed & may point to nothing
- Have complicated [[Pointer const-Level|const level]] rules 
