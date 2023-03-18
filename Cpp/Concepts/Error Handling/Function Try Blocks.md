---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Function Try Blocks
linter-yaml-title-alias: Function Try Blocks
date-of-creation: 2023-02-19
mod-date: 2023-02-19
---

# Function Try Blocks

## Syntax
```cpp
class B : public A
{
	B(int x) try : A{x}
	{}
	catch(…)
	{
		std::cerr << "Failure…";
		// Must either throw or rethrow a exception
		throw;
	}
};
```

## Properties for Constructors
- The `catch`-block of a construtor must either throw a new exception or rethrow the catched exception
	→ Destructors/ other functions *function try block*'s `catch`-blocks can also resolve catched exceptions…
