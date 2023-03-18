---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: Coroutines
linter-yaml-title-alias: Coroutines
date-of-creation: 2023-03-02
mod-date: 2023-03-02
---

# Coroutines
→ "nice little nugget buried underneath heaps of garbage that you have to wade through to access the nice part \[…\] the C++ standard library doesn’t actually supply the heap of garbage you need to access coroutines"

## Principle
- Methods which data are allocated on the heap
	- The methods stack however is initialized from a certain return point (with the local data) on the stack
- Instead of a "run" & "return" semantic of normal functions, there are also "start", suspend" & "terminate" semantic to make the function return from the point of it's last exit
	- The coroutine methods can be run on behave

---
Source:
- https://www.scs.stanford.edu/~dm/blog/c++-coroutines.html
