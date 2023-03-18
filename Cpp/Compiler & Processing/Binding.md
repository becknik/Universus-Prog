---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Binding
linter-yaml-title-alias: Binding
date-of-creation: 2023-02-17
mod-date: 2023-02-17
---

# Binding

## Early/ Static
- The compiler & linker can infer the called functions/ entities [[../../../../../Uni/Ro I/RISC-V/Problem Counter|PC]] address & substitute
	- The functions call must not being dependent on runtime actions
- The function is called directly by the compiler
```cpp
	int result {};
	switch (op)
    {
        // call the target function directly using early binding
        case 0: result = add(x, y); break;
        case 1: result = subtract(x, y); break;
        case 2: result = multiply(x, y); break;
    }
	std::cout << result;
```

## Late
→ Called *dynamic binding* in case of [[Virtual Functions]] name resolution
- The called function is not known by the compiler or linker when the call is actually be made
	→ The function to be called has to be determined at runtime
- E.g. used for [[../Concepts/Function Pointers]]:
```cpp
	int (*pFcn)(int, int) { nullptr };
    // Set pFcn to point to the function the user chose
    switch (op)
    {
        case 0: pFcn = add; break;
        case 1: pFcn = subtract; break;
        case 2: pFcn = multiply; break;
    }
	std::cout << pFcn(x, y);
```
