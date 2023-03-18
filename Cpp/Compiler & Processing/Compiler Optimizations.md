---
tags: practical-cs prog cpp compiler
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Compiler Optimizations
linter-yaml-title-alias: Compiler Optimizations
date-of-creation: 2022-12-29
mod-date: 2022-12-30
---

# Compiler Optimizations

## General
- Constant expressions are expressions which can be evaluated to compile time due to to compilations time known values
- Compile time constants are constant values known to compile time
	→ Compiler can substitute the call of those variables with their values to avoid fetching
	→ Detection of compile time consts (which are hard to detect) can be insured by using `constexpr`

## Constant folding
- Expressions of constant values in non constant context can be replaced by their salvation on compile time
```cpp
std::cout << 3 + 4 << '\n'; // this is a runtime expression
// if compiler implements constant folding, after compilance:
std::cout << 7 << '\n';
```

## [[../Concepts/Inline Functions|Inline Functions]]
- When the output of a (implicitly) inlinable function is not required in a *constant-expression context* & does not interact with the runtime, the compiler is free to decide for runtime or compile-time evaluation
```cpp
// To force a function to get compile-time evaluated:
consteval auto evaluate_to_compile_time(const auto function_return)
{
	return function_return; // Return by value does not matter
}
```
- `#include <type_trait>`: `std::is_constant_evaluated()` in function body

## Numeric promotion
- A category of informal type, value-preserving conversions of narrower numeric types (including `char`) to wider numeric promotions (typical `int` or `double`)
	→ Compilers do this without complaints
	→ Reduces to redundancy of similar operations on different types

## Name Mangling
- Compilers altering a functions name (e.g. `void fcn()` → `__fcn_v`) for the Linker & performance reasons

## Data Structure Alignment & Padding
- CPUs access the memory addresses block-wise (e.g. 32 Bit - 4 Byte at once), which are usually divisors of 2
- To allow the CPU the best access on data structures, compilers generally align small data types towards those borders to ensure the CPU must not fetch fragments of primitive types
- To enable the compiler the best possible alignment (reordering is not allowed) the largest type should be defined first in a data structure
	→ further descending
[source](https://en.wikipedia.org/wiki/Data_structure_alignment)

## Elision
```cpp
Fraction someFraction{ Fraction{5, 3} };
// Compiler swallows copy constructor call & performs a direct initialization
// Evaluates to
Fraction someFraction{ 5, 3 }
```