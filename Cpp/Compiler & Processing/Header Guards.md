---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Header Guards
linter-yaml-title-alias: Header Guards
date-of-creation: 2022-12-17
mod-date: 2023-03-09
---

# Header Guards
```cpp
// example1.hpp
#ifdef <HEADER_NAME>_H
#define <HEADer_NAME>_H
<#include …>
<int add(int a, int b);…>
#endif

// ---
// example2.hpp
#pragma once
<#include …>
<int add(int a, int b);…>
```
- Guarantee, that the contents of a header file is not included twice into the same `.cpp` file
- Naming scheme for large projects, where equally named header files might cause bad stuff: `<PROJECT>_<PATH>_<FILE>_H`, `<FILE>_<LARGE RANDOM NUMBER>_H`, `<FILE>_<CREATION DATE>_H`
