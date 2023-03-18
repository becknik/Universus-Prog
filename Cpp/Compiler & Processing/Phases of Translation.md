---
tags: practical-cs prog cpp
sources: en.cppreference.com/w
cards-deck: Private::Prog::C++
completed: true
aliases: Phases of Translation
linter-yaml-title-alias: Phases of Translation
date-of-creation: 2022-12-17
mod-date: 2022-12-30
---

# Phases of Translation

## Phases

### Phase 1
- Byte-Mapping to uniform [Basic Source Character Set](https://en.cppreference.com/w/cpp/language/charset#Basic_source_character_set) - which seems to be a glyph subset of [[../../../../../Uni/Ro I/Zahlen & Kodierung/ASCII|ASCII]]
	→ Linke-Break characters are mapped to uniform ones
- C++23: All input files are mapped to UTF-8, whereas the supported files for this mapping is implementation specific
	→ Input files are decoded to a sequence of "UCS scalar values"

### Phase 2
- Unnecessary EOL Characters are deleted & replaced

### Phase 3
- Decomposition into comments, sequences of tabs/ whitespaces & *preprocessing tokens*, which are the following:
	- headers `<iostream>`, `"myfile.h"`
	- identifiers
	- preprocessing numbers
	- character & string literals
		→ Transformations from pahse 2 between `"`s are reverted
	- operators & punctruators
	- individual non-whitespace characters that do not fit in any other category

### Phase 4
- Execution of the preprocessor
- `#include`s go through Phase 1-4 recursively
- At the end of this phase preprocessor directives are removed from source

### Phase 5 + 6
- Concatenation of adjacent string literals by determining a common encoding prefix

### Phase 7
- Compilation: Each preprocessing token is converted to a token
- Tokens are syntactically & semantically analyzed & translated as a translation unit

### Phase 8
- Translation units produce a list of required template instantiations

## Phase 9
- Translation, instantiation units & library components needed to satisfy external references are collected into a program image which is needed for its execution environment
