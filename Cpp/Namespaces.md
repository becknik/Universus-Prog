---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Namespaces
linter-yaml-title-alias: Namespaces
date-of-creation: 2023-03-16
mod-date: 2023-03-16
---

# Namespaces

## `Inline`
- Marks a namespace as preferred over other namespaces when calling a function without the namespace resolution operator
```cpp
#include <iostream>

inline namespace v1 {
    void doSomething() {
        std::cout << "v1\n";
    }
}

namespace v2 {
    void doSomething() {
        std::cout << "v2\n";
    }
}

int main() {
    v1::doSomething();
    v2::doSomething();
    doSomething(); // calls the inline version of doSomething()

    return 0;
}
```
