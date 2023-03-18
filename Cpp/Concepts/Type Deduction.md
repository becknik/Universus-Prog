---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Type Deduction
linter-yaml-title-alias: Type Deduction
date-of-creation: 2022-12-29
mod-date: 2022-12-29
---

# Type Deduction

## Dropped References
- Are implicitly (when not specified other) dropped by type deduction
- If references weren't dropped, there would be no way for the type deduction to deduce to the type `T` from `&T`
```cpp
const std::string& getConstRef(); // some function that returns a const reference

int main()
{
    auto ref1{ getConstRef() };        // std::string (top-level const and reference dropped)
    const auto ref2{ getConstRef() };  // const std::string (const reapplied, reference dropped)

    auto& ref3{ getConstRef() };       // const std::string& (reference reapplied, low-level const not dropped)
    const auto& ref4{ getConstRef() }; // const std::string& (reference and const reapplied)
}
```

## Dropped Pointers
- Are not implicitly dropped by type deduction
- If pointers where dropped, `*pntr_to_T` would cause a error
- `auto*` must be a pointer to satisfy the compiler
```cpp
std::string* getPtr(); // some function that returns a pointer

int main()
{
    auto ptr3{ *getPtr() };      // std::string (because we dereferenced getPtr())
    auto* ptr4{ *getPtr() };     // does not compile (initializer not a pointer)
	
	const auto ptr1{ getPtr() };  // std::string* const
    auto const ptr2 { getPtr() }; // std::string* const

    const auto* ptr3{ getPtr() }; // const std::string*
    auto* const ptr4{ getPtr() }; // std::string* const
}

const std::string* const getConstPtr(); // some function that returns a const pointer to a const value

int main_brainfuck()
{
	auto ptr1{ getConstPtr() };  // const std::string*
    auto* ptr2{ getConstPtr() }; // const std::string*

    auto const ptr3{ getConstPtr() };  // const std::string* const
    const auto ptr4{ getConstPtr() };  // const std::string* const

    auto* const ptr5{ getConstPtr() }; // const std::string* const
    const auto* ptr6{ getConstPtr() }; // const std::string*

    const auto const ptr7{ getConstPtr() };  // error: const qualifer can not be applied twice
    const auto* const ptr8{ getConstPtr() }; // const std::string* const
}
```
