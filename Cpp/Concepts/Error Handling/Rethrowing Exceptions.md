---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Rethrowing Exceptions
linter-yaml-title-alias: Rethrowing Exceptions
date-of-creation: 2023-02-19
mod-date: 2023-02-19
---

# Rethrowing Exceptions

## Problems
- The rethrowing copy-initializes the type to the catched exceptions type
	→ If the type in the catch-statement is `Base&`, the rethrown exception is copy-initialized/ sliced to `Base`
- Solution: just `throw;`
