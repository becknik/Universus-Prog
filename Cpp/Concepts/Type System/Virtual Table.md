---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Virtual Table
linter-yaml-title-alias: Virtual Table
date-of-creation: 2023-02-17
mod-date: 2023-02-17
---

# Virtual Table

## Principle
- The objects of every class containing [[Virtual Functions]] contain a implicit `*__cptr` to a *virtual table*
- This table is a `static const` array consisting (simplified) [[../Function Pointers]] to the most derived method the class has access to
- Example:
```cpp
class Base
{
public:
    VirtualTable* __vptr;
    virtual void function1() {};
    virtual void function2() {};
};

class D1: public Base
{
public:
    void function1() override {};
};

class D2: public Base
{
public:
    void function2() override {};
};
```
![](https://www.learncpp.com/images/CppTutorial/Section12/VTable.gif)

## Further Digging
- It seems like there is a way to implement virtual tables function-wise to avoid the extense of cache coldness when looking up in the classes function table
> The alternative is to have a virtual table for each function and switch function pointer on the type of the calling class. This works fine in practice and does save some of the overhead as the virtual table would be the same for all the calls in a single iteration of a group of objects.[^1]

[^1]:https://www.dataorienteddesign.com/dodmain/node17.html