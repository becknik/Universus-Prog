---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Promotions & Conversions
linter-yaml-title-alias: Promotions & Conversions
date-of-creation: 2023-03-17
mod-date: 2023-03-17
---

# Promotions & Conversions
- The basic lookup stepping for function overload resolution
	1. Direct Matches & [[#Trivial Conversions]]
	2. [[#Integral Promotion]]
	3. [[#Numeric Conversion]]
	4. User Defined Conversions

## Integral Promotion
→ [Cpp Reference](https://en.cppreference.com/w/cpp/language/implicit_conversion#Integral_promotion)
→ Considered safe
- Arithmetic operators don't accept types smaller than `int`
- Most types can be converted to `int` or `unisgned int` when their value range is higher as `int`
- `bool`s can be converted to `int` to `1` or `0` respective

## Numeric Conversion
- Converting `int`→ `double` strangely counts as numeric conversion too

### Narrowing
- Conversion that may lead to data loss
	→ Brace initialization disallows this
- **Compilers might not warn about `signed`→ `unsigned` conversions…**

## Arithmetic Conversion
- Priority list:
	- `long double` > `double` > `float` > `unsigned long long` > `long long` > `unsigned long` > `long` > `unsigned int` > `int`
		→ If one of the operands is on the list the other one is converted to this - if neither are both get promoted to `int`

## Trivial Conversions
- Converting from non-`const` → `const`
- Converting to or from a reference type
