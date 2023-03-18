---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Template Specialization
linter-yaml-title-alias: Template Specialization
date-of-creation: 2023-02-18
mod-date: 2023-02-18
---

# Template Specialization

## Partial
- Parts of the template-declaration are left out or replaced by more specialized types (like `T*`)

### Examples
- For pointers:
```cpp
template <typename T>
class Storage

tmeplate<typename T>
class Storage<T*>
```
- For a static array class:
```cpp
template<typename T, std::size_t size>
class StaticArrayBase {…}

// Polymorphy needed to partly specialize pure virtual member function
tmeplate<std::site_t size>
class StaticArray : public StaticArrayBase<double, size> {…}

// Specialization of member function to print doubles in scientific notation
tmeplate<std::site_t size>
class StaticArray<double, size> : public StaticArrayBase<double, size> {…}
```

## Full
- The specialized type of a method/class is specified
	→ Notation `template<>` & `Class<specialized_type>`

### Examples
```cpp
template <typename T>
class Storage

template <>
Storage<char*>::Storage(char* value)
```
