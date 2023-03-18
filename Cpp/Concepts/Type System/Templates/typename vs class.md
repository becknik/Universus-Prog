---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: typename vs class
linter-yaml-title-alias: typename vs class
date-of-creation: 2023-03-17
mod-date: 2023-03-17
---

# typename vs class
- In the most cases `typename` & `class` are interchangable
- When accessing subtypes of a templated type, the `typename` keyword must be used
```cpp
template<typename T>
class Foo
{
    typedef typename T::bar sub_T;
};
```
- Explicit class initialization: `template class Foo<int>;`
- Pre #cpp17 :
```cpp
template<template<typename T1, typename T2> class SomeClass, typename T>
```