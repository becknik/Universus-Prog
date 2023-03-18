---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Gotchas
linter-yaml-title-alias: Gotchas
date-of-creation: 2023-01-01
mod-date: 2023-01-01
---

# Gotchas

## Fundamental Types
- [[Concepts/Data Models|Data Models]] have different sizes on different architectures

## Data Structures
- `std::array`:
	- Length queries naming is inconsistent (`.size()` instead of `.length()`)
	- Awkward syntax for creation for pre C++17 compilers (`std::arry<T, std::size_t>`)
	- Indexing & `size()` accepts *unsigned* `std::size_t`, which leads to `std::size_t` for run variables `i,j,k,…`
