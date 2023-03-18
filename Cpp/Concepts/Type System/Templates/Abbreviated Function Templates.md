---
tags: practical-cs prog cpp
sources: https://www.cppstories.com/2021/concepts-intro/
cards-deck: Private::Prog::C++
completed: true
aliases: Abbreviated Function Templates
linter-yaml-title-alias: Abbreviated Function Templates
date-of-creation: 2023-03-01
mod-date: 2023-03-01
---

# Abbreviated Function Templates

## Example
- A basic template function, without abbreviation:
```cpp
template<typename T>
void print(const std::vector<T>& vec)
{
	for(const auto& element : vec)
	{
		std::cout << element << ", ";
	}
}
```
- The same function, abbreviated ( #cpp20 ):
```cpp
void print(const std::vector<auto>& vec)
{
	// …
}
```
