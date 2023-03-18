---
tags: practical-cs prog cpp cpp20
cards-deck: Private::Prog::C++
completed: true
aliases: span
linter-yaml-title-alias: span
date-of-creation: 2023-03-15
mod-date: 2023-03-19
---

# span
→ formerly known as `array_view`

## When not to use[^1]
- Arbitrary range or iterators is requested, like for all `std::algorithm` algorithms
	→ A `std::span` has stricter requirements than a iterator or range, `std::deque` is not acceptable for example
- A container is a better fit
	→ `std::span` is meant to be supplementary to those

## When to use[^1]
- Whenever a *non-owning* (reference type, rather than value type) `ptr + length` information without any container overhead is required
- Enables some static range checking
- Enables static debugging runtime bound checking

## Examples
```cpp
#include <iostream>
#include <span>

int main(int argc, const char* argv[])
{
    for (auto s : std::span { argv, static_cast<std::size_t>(argc) })
      std::cout << s << std::endl;
}
```
[^2]

[^1]: https://stackoverflow.com/questions/45723819/what-is-a-span-and-when-should-i-use-one
[^2]: https://stackoverflow.com/questions/62218832/how-to-use-span-to-wrap-up-command-line-args
