---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: Structured Binding
linter-yaml-title-alias: Structured Binding
date-of-creation: 2023-03-18
mod-date: 2023-03-18
---

# Structured Binding

## Syntax
```cpp
	std::pair a{30, 'a'};
	auto& [var1,var2] {a};
	var1 = 12;
```

## What's behind
```cpp
// auto [a,b,c]{…}; ==
auto tempTuple = expression;
using a = tempTuple.first;
using b = tempTuple.second;
using c = tempTuple.third;
```

## Bindings
- Can be [[../Concepts/Weird/Initialization Types|Copy Initialized]] with an arrays
- Can be copy initialized with `std::tuple_size<>` and the `get<N>()` interface

## Examples
```cpp
if (auto [itelem, success] = mymap.insert(std::pair(‘a’, 100)); success)
{
    // Insert success
}
```

---
Source:
- [Cpp Stories](https://www.cppstories.com/2022/structured-bindings/)
