---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Lambdas
linter-yaml-title-alias: Lambdas
date-of-creation: 2023-01-22
mod-date: 2023-01-22
---

# Lambdas
- Basic Lambda Syntax:
```c++
auto lambda_identifier {
	[<(captures)>](<parameters>) <(mutable)> → <return_type>{
		<function>
	}
};
```

## Captures
- Basic captures: `[variable](<…>) → void {std::cout << variable}`
	→ Clones [[Value Categories|rvalue]] on lambda initialization & uses cloned value inside the lambda function body
- Modifiable basic capture: `[variable](<…>) → void {variable++}`
	→ Clones & modifies clone in lambda function body
- Capture by reference: `[&variable](<…>) → void {variable++}`
	→ Might cause undefined behavior on dangling references
- Multiple captures: `[var1,var2,&var3]…`
- Default captures: capture all variables mentioned in the lambda by default
	- By value: `[=](<…>) → void {<…>}`
	- By reference: `[&](<…>) → void {<…>}`
- Declarative capture: `[new_variable{var1 * var2}]() → void {std::cout << new_variable}`
	→ Should only be used if the declaration is short & the type is obvious…

## Avoiding copying when passing to function
- A function awaiting a lambda object as parameter (like `void myInvoke(const std::function<void()>& fn)`) actually receives a copy of the lambda
- To avoid copying the lambda object, the lambda object might be wrapped in `std::ref()`
	→ The reference gets copied instead of the underlying lambda object, which is partly ensured by the `std::function` type
