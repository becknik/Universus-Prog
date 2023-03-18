---
tags: practical-cs prog cpp
sources: https://www.cppstories.com/2021/concepts-intro/
cards-deck: Private::Prog::C++
completed: true
aliases: Concepts
linter-yaml-title-alias: Concepts
date-of-creation: 2023-03-01
mod-date: 2023-03-01
---

# Concepts

## Functions
- Generic types in [[Templates]] can be constrained by using the `requires <concept-"condition">` *clause*
	→ Predefined concepts are located in the `concepts` header
```cpp
template <typename T>
requires std::integral<T> || std::floating_point<T>
constexpr double get_average(const std::vector<T> &vec)
{
	const double sum = std::accumulate(vec.begin(), vec.end(), 0.0);        
    return sum / vec.size();
}
```
- Also, there exists a `requires`-*expression* to define advanced constrains by defining a required interface a type must fulfill
```cpp
template<typename T>
concept is_addable = (T t, int i) {
	{t+i} → <concept>; // eg std::same_as<int>
}
```
→ All with this `concept` constrained template must a function `isTrue`
- returns a `bool`, therefore can be `static_assert()`ed
```cpp
template<typename Iter>
struct S {
	static_assert(requires(Iter i){ ++i; }, "No increment")
}
```
→ The specified `operator++` is not executed tho
- Concepts without the `requires`-expression:
```cpp
template<typename T>
	concept POD = std::is_trivial<T>::value &&
	std::is_standard_layout::value;
```

## Abbreviations
```cpp
template<<concept> T>
double sum(const std::vector<T> vec) { }
// →
template <typenameT>
requires <concept><T>
double sum(const std::vector<T> vec)
```

## Constrained `auto`
→ [[Abbreviated Function Templates]]
- To constrain generic function templates, a constraining concept might be used in before the type declaration
```cpp
void func(const <concept> auto param) { }
// → 
<template T>
requires <concept><T>
void func(T param) { }
```

### Example
```cpp
void print(const std::ranges::range auto& rng)
{
	for(const auto& element : rng)
	{
		std::cout << element << ", ";
	}
}
```

## Advantages
- Nice error messages (to be compared with error messages on basic [[Templates]])
