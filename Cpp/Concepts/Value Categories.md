---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - Value Categories
  - rvalue
  - reference to rvalue
  - lvalue
  - reference to lvalue
  - Temporary Objects
linter-yaml-title-alias: Value Categories
date-of-creation: 2022-12-27
mod-date: 2023-03-17
---

# Value Categories
→ In C++, all expressions has a *type* & a *value category*
→ [CppReference](https://en.cppreference.com/w/cpp/language/value_category)

## `lvalue`

### Definition
- An expression evaluating to an identifiable object or function, hence an entity
	→ A entity with an identity can be differentiated from other similar entities by comparing addresses
	→ Historically first appear left-sided of an assignment expression
- [[Scope, Duration & Linkage|Duration]] lasts further than the expression
- Can be refined into *modifiable & un-modifiable* `lvalue`

### References
- A reference to a `lvalue` can't be reseated (= change the referenced `lvalue`)
- *Special rule*: When a `const lvalue` reference is bound to a temporary object, the lifetime of the temporary object is extended to match the reference
	→ This enables function parameters to receive `lvalue`, `const lvalue` & `rvalue`
```cpp
{
const int& ref{ 7 /* ← temporary object */ }
std::cout << ref << '\n';
} // ref & temporary object go out of space right here
```
- Will be be optimized away, therefore might not be objects/ allocate space - unlike *pointers* do
	→ Because containers only hold objects which also needs to be re-assignable, references can't be stored in them → `std::reference_wrapper`
```cpp
int x { 5 };
int& ref { x }; // lvalue reference
```

## `rvalue`

### Definition
- Everything what is not a `lvalue`
- An expression consisting out e.g. call-by-value (overloaded) function returns or literals like C-style-strings
	→ Produce temporary values which are not identifiable & are therefore discarded at the end of the expression
	→ Historically appearing right-sided
- Refined in `prvalues` and `xvalues`, where `xvalue` seem to be movable

### References
```cpp
int x{5};
int& lvalue_ref{x};
int&& rvalue_ref{5};
```
- Can not bind `(const) lvalue` expressions
- Can modify the bound `rvalue` expressions, when not being `const`
- Expanding the lifetime of the bound `rvalue`
```cpp
int&& rref{ 5 }; // temporary object with value 5 is created here
rref = 10;
std::cout << rref << '\n';
```
- Can be used to overload `const int &lvalue_ref` with `int &&rvalue_ref`
	→ However: when `rvalue` references are used in an expression, they become `lvalue`s, due to `int&& ref` is a `lvalue` of the type `int&&`!
- *Special Rule*: Automatic objects returned by value by a function can be moved, even if they are `lvale`

### Examples
```cpp
#include <iostream>
int return5() { return 5; }

int main() {
    int x{ 5 }; // 5 is an rvalue expression
    const double d{ 1.2 }; // 1.2 is an rvalue expression

    int z { return5() }; // return5() is an rvalue expression (since the result is returned by value)

    int w { x + 1 }; // x + 1 is an rvalue expression
    int q { static_cast<int>(d) }; // the result of static casting d to an int is an rvalue expression

	w = z; // impicit conversion from lvalue to rvalue

    return 0;
}
```

## Anonymous Objects
```cpp
int add(int a, int b)
{
	sum{a+b};
	return /* sum */ a + b; // ← Annonymous object created for storing the expressions evaluaton to be returned
}
```
- Creating a anonymous object from a class: `Cents{7}`
	→ Have no name
- Have expression-[[Scope, Duration & Linkage|scope]]
