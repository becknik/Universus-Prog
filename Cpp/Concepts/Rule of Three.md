---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - Rule of Three
  - Rule of Zero
  - Rule of Five
  - Rule of Five & a half
linter-yaml-title-alias: Rule of Three
date-of-creation: 2023-02-08
mod-date: 2023-02-19
---

# Rule of Three

## Definition
- "If a class requires a *user-defined constructor*, a *copy constructor* or a *copy assignment operator*, then it probably requires all three"
[Cite](https://www.learncpp.com/cpp-tutorial/the-copy-constructor/)

# Rule of Zero
- "Classes that have custom destructors, copy/move constructors or copy/move assignment operators should deal exclusively with ownership. Other classes should not have \[these\]"
[Cite - web.archive](https://web.archive.org/web/20121127171954/http://rmartinho.github.com/cxx11/2012/08/15/rule-of-zero.html)

# Rule of Five
- The *copy constructor*, *copy assignment operator*, *move constructor*, *move assignment operator* or *destructor* should all either be deleted or defined together
	→ [[Copy & Swap Idiom|Copy & Swap Idiom]]
	→ [[Value Categories|Value Categories]]
