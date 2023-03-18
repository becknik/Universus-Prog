---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: volatile
linter-yaml-title-alias: volatile
date-of-creation: 2023-03-04
mod-date: 2023-03-04
---

# volatile

## Why does it exist
- Hint the compiler not to make only-read-once optimizations to the declared variable, due to the variable being written to by other entities [^1]
	→ Every time the variable is accessed in the source code, this variable actually gets read by the instructions generated by the compiler
- May be useful for accessing a variable another entity is constantly writing

## Use Cases
- Memory mapped I/O
- Something on [[../../../../../../Uni/SysKon/Betriebssystem/Funktionen/System Calls|ISRs]]

---
Source:
- [Reddit](https://www.reddit.com/r/embedded/comments/omrog5/when_to_use_volatile_word_in_c_c_project/) (04.03.2023)
- [Linux Doc](https://www.kernel.org/doc/html/v5.5/process/volatile-considered-harmful.html) (04.03.2023)