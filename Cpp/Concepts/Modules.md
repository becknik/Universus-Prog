---
tags: practical-cs prog cpp
sources: https://en.cppreference.com/w/
cards-deck: Private::Prog::C++
completed: true
aliases: Modules
linter-yaml-title-alias: Modules
date-of-creation: 2023-03-02
mod-date: 2023-03-02
---

# Modules

## Properties
- Aiming to give an alternative to header files
- For importing modules of headers the `import <module/header>;` expression is used
- To make a function public available for importing modules, the `export <declaration>` method is used

## Syntax

### Global module fragment
```cpp
module;
// preprocessor-directives, notably for configuration
// …
export module <module_name.sth>;
```

### Module declaration
```cpp
export module <module_name.sth>;
```
- Creates a *module interface unit* where the `.sth` is meant to display hierarchy
- Must be the first declaration of the unit (excepting of a *global module fragment*)
- `module <module_name>` can be used for declaring *module implementation units*

#### Private
```cpp
export module <module_name.sth>;
// export sth();
// …
module : private;
// definition not reachable from importers of <module_name.sth>
```

### Partitions
```cpp
// A-B.cppm
export module A:B;
// …
// A-C.cppm
export module A:C;
// …
// A.cppm
export module A;
import :C;
export import :B;
// …
```
- Can be imported by the module units of the same named module
	→ Are only visible from within a named module

### Export
```cpp
export auto get_hello() → std::string_view { return "hello";}
export {
	auto one() → int {return 1;}
	auto two() → int {return 2;}
}
export namespace <namespace_name> {
	//…
}
```

## Import
```cpp
import <iostream>
export import <string_view>
```

---
Sources:
- [Cpp Reference](https://en.cppreference.com/w/cpp/language/modules)
- [PS PDF Kit](https://pspdfkit.com/blog/2020/cpp20-in-2020-modules/)
