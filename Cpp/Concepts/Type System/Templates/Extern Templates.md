---
tags: practical-cs prog cpp cpp11
cards-deck: Private::Prog::C++
completed: true
aliases: Extern Templates
linter-yaml-title-alias: Extern Templates
date-of-creation: 2023-03-17
mod-date: 2023-03-17
---

# Extern Templates

## Principle
- Reduces the instantiation of a template with the same type parameters in different translation units to just one[^2]
	→ leads to reduced compile time & binary size (which is automatically discarded on linking phase)
- The explicit specification of a template type is a bit of a pain, due to it being needed in all included files[^1]
	→ [[#Solution 2: Moving the definitions into the including files]]
	→ [[#Solution 1: Moving the definition to the templates `.cpp` file]] ← As of[^1] this seems to work, but I don't understand way

## Solution 1: Moving the definition to the templates `.cpp` file
→ External projects can't use your template with their own types
→ Also you are forced to explicitly instantiate all types
`MyTemplate.hpp`:
```cpp
#pragma once
template<class T>
struct MyTemplate {
    T f(T t);
};
```
`MyTemplate.cpp`:
```cpp
#include "MyTemplate.hpp"

template<class T>
T MyTemplate<T>::f(T t) { return t + 1; }

template class MyTemplate<int>; // Explicit instantiation
// Use in other files automatically use this definition
```

## Solution 2: Moving the definitions into the including files
→ Will be forgotten by the programmer
`MyTemplate.cpp`:
```cpp
#include "MyTemplate.hpp"

template class MyTemplate<int>; // Explicit instantiation
// Use in other files automatically use this definition
```
`main.cpp`:
```cpp
#include "MyTemplate.hpp"
#include "not_main.hpp"

#include <iostream>

// extern template declaration
extern template class MyTemplate<int>;

int main() {
    std::cout << not_main() + MyTemplate<int>().f(1) << std::endl;
}
```
`not_main.cpp`:
```cpp
#include "MyTemplate.hpp"
#include "not_main.hpp"

// extern template declaration
extern template class MyTemplate<int>;

int not_main() { return MyTemplate<int>().f(1); }
```
[^1]:[Stackoverflow←So comprehensive](https://stackoverflow.com/a/59614755)
[^2]: [Stackoverflow](https://stackoverflow.com/a/8131212)
