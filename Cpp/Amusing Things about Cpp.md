---
tags: prog cpp
cards-deck: 
completed: true
aliases: Amusing Things about Cpp
linter-yaml-title-alias: Amusing Things about Cpp
date-of-creation: 2022-12-18
mod-date: 2022-12-21
---

# Amusing Things about Cpp
The language, in which…
- The developers of the language encourage to not use unsigned integers, but include their use in the standard lib
	- Approximate citation from interview: "We were young and dumb"
- Language standards (from 2 years ago) exist, which the mayor compilers keep struggling to maintain, where as unofficial preprocessor features like `#predign once` (which will never be included to the standards) are compliant since tenths of years
- Uninitialized datatypes are getting the random value of the previous memory positioning
- Primitive datatypes are only ensued to have a minimum size of bytes they allocate, where as the actual size is made up by the machine the program is compiled for
- 3 ways of initializations exist, and all have different meanings
- compilation of programs making use of dependencies wouldn't compile unless a further preprocessing Programm would run before the compiler to do reformatting & copying the dependencies declaration into the files
- signed primitives are converted to unsigned primitives when using binary operators with signed primitives…
- you need to write guards for your forward definitions, so that they are not dasted more than once into compilation units & the compiler explodes
- Boolean values are 0 or 1. The language just won't accept true or false as user input, unless you specify. When you do so, 0 or 1 are not accepted any more
- for backwards compatibility reasons you can specify functions to have the parameter `void`
- the compiler may evaluate expressions in any order he might like, hence outside of order precedence & associativity rules
	→ Expressions should not depend of the order of evaluations
- `a || b && c || d` gets evaluated to ` (a || (b && c) ) || d`
- `int value{ add(x, ++x) }` might evaluate to `11` `12`, depending on compiler & architecture…
- The `extern` keyword which is used to make global variables globally(=for other files) read- and writable has two semantics. For a final `const` variable in the initializing file it indicates the variable to be used in external in the file of definition, in a header without any init it means the variable is defined somewhere else
	→ If you use the keyword on not initialized non-const variable the compiler thinks that this variable is defined somewhere else…
	→ `constexpr` variables cant be forward declarated
- You can externalize const variables as not const, leading to `segmentations fault`…
- Introduced a painless way for `fomat()` 35 years after it's first release (with c++20)...