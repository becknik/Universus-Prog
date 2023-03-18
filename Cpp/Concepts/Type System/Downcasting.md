---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - Downcasting
  - dynamic_cast
linter-yaml-title-alias: Downcasting
date-of-creation: 2023-02-17
mod-date: 2023-02-27
---

# Downcasting
→ Don't use `static_cast` to downcast

## When `dynamic_cast` fails
- With `protected` or `private` class inheritance
- For classes that do not declare or inherit any virtual functions
	→ Thus don’t have a [[Virtual Table]]
- In certain cases involving *virtual base classes*
	→ see [this page](https://msdn.microsoft.com/en-us/library/cby9kycs.aspx) for an example of some of these cases, and how to resolve them
- On *casts of references* & the type hierarchy is broken (exception)
- GCCs `-fno-rtti` (=Run-Time Type Information) [[../../Compiler & Processing/Compiler Arguments|Compiler Argument]] for some space-optimizations
