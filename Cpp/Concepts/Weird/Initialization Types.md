---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Initialization Types
linter-yaml-title-alias: Initialization Types
date-of-creation: 2023-02-26
mod-date: 2023-02-26
---

# Initialization Types

## Basic
- Default Initialization: `T t;`
- Copy Initialization: `T t = 5;`
	→ Deduces implicit [[Narrowing Conversion]]
	- Copy List Initialization: `T t = {5}`
- Direct Initialization: `T t(5);`
	→ Considered out of favor due to similarity to a method forward declaration
	→ Also may implicitly do a [[Narrowing Conversion]]
	- Direct List Initialization: `T t{5}`
		→ Also called Uniform/ Brace Initialization
		→ Compiler errors on implicit [[Narrowing Conversion]]
- Value initialization: `T t{}`
	→  Should be used when the value is only temporary
