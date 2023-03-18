---
tags: practical-cs prog cpp
cards-deck: 
completed: true
aliases: Literals
linter-yaml-title-alias: Literals
date-of-creation: 2022-12-20
mod-date: 2023-03-18
---

# Literals

## Default types
- Integral: `int`
- Boolean: `bool`
- Floating Point: `double`
- Character: `char`
- C-Style String: `const char[n]`
	→ E.g. `"Hello World"`

## Suffixes
→ Bes Practice: **UPPER CASE** to be preferred

### Integral
| Type                                   | Suffix                         |
| -------------------------------------- | ------------------------------ |
| unsigned `int`                         | `U`/`u`                        |
| `long`                                 | `L`/`l`                        |
| unsigned `long`                        | `Ul`/`UL`/`Lu`/`LU` (etc.)     |
| `long long`                            | `LL`/`ll`                      |
| unsigned `long long`                   | `ULL`/`Ull`/`LLu`/`LLU` (etc.) |
| signed version of `std::size_t` #Cpp23 | `z`/`Z`                        |
| `std::size_t` #Cpp23                   | `uz`/`UZ`                      |
→ Complete list: [LearnCpp](https://www.learncpp.com/cpp-tutorial/literals/)

### Floating Point
| Type       | Suffix  |
| ------------- | ------- |
| float         | `f`/`F` |
| `long double` | `l`/`L` |

### Strings
| Meaning            | Suffix |
| ------------------ | ------ |
| `std::string`      | `s`    |
| `std::string_view` | `sv`   |
→ `using namespace std::literals;`

| Meaning             | Prefix |
| ------------------- | ------ |
| UTF-8 string #cpp11 | `u8`   |

### Chars #cpp11
| Prefix  | Semantic   |
| ------- | ---------- |
| `u8'…'` | `char8_t`  | 
| `u'…'`  | `char16_t` |
| `U'…'`  | `char32_t` |

## Chrono
- Suffixes: `h`, `min`, `s`, `ms`, `us`, `ns`
