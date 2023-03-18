---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases:
  - Classes
  - Things to keep in mind for C++ classes
linter-yaml-title-alias: Classes
date-of-creation: 2023-03-16
mod-date: 2023-03-16
---

# Classes

## Virtual destructors
- If a class is intended to be inherited from, make it's destructors `virtual`
- Else make the class declaration `final`
	- Or (~*Herb Shutter*): "A base class destructor should be either public and virtual, or protected and nonvirtual."

## Delete `operator=`
- Value assignments with `operator=` to a base class cause implicit slicing of the assigned object due to the default `operator=` not being `virtual`
	→ `virtual void operator=(Class class) const = delete;` - [[../Concepts/Copy & Swap Idiom|also see: Copy & Swap Idiom]]
- Example:
```cpp
    Derived d1{ 5 };
    Derived d2{ 6 };
    Base& b{ d2 };

    b = d1; // this line is problematic
```
