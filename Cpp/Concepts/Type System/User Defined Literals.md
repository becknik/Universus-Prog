---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: User Defined Literals
linter-yaml-title-alias: User Defined Literals
date-of-creation: 2023-03-18
mod-date: 2023-03-18
---

# User Defined Literals
→ [[../../Literals|Literals]]

## Definition Syntax
```cpp
MyType operator""_myType(unsigned long long int value)
{
    return MyType{ value };
}
```
- Not all types are allowed as parameters:
	- `usingned long long int` for any integer representation
	- `long double` for floating point representation
	- `char` for char representation
	- `const char*` for string representation
	- `const char*, size_t` for string representation
- User defined types must start with a `_`
- Suffixes starting with a capital letter are allowed without a ` ` between `operator""` and the suffix
```cpp
MyType operator""_MyType(unsigned long long int value) // OK
{
    // …
}
MyType operator"" _MyType(unsigned long long int value) // NOT OK
{
    // …
}
MyType operator"" _myType(unsigned long long int value) // OK
{
    // …
}
```

---
Source:
- [Fluent{C++}](https://www.fluentcpp.com/2021/10/08/a-recap-on-user-defined-literals/)