---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Side Effects causing Undefined Behavior
linter-yaml-title-alias: Side Effects causing Undefined Behavior
date-of-creation: 2023-03-16
mod-date: 2023-03-16
---

# Side Effects causing Undefined Behavior
- C++ does not define any evaluation order for function arguments or operands on operands
- *Warning*: Never use more than once side-effected variables in one statement!
```cpp
	int a{6};
	std::cout << "The result of add(a,++a)? " << ::add(a, ++a) << '\n';
	// gcc delivers 14, clang 13 & might also be 12 xD
```
