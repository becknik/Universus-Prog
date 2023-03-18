---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Header Includes
linter-yaml-title-alias: Header Includes
date-of-creation: 2023-02-04
mod-date: 2023-03-09
---

# Header Includes

## Best Practice

### Detecting missing includes
- Header `#include`s should be ordered as the following:
1. Paired header files
2. Further headers from project
3. 3rd party library headers
4. `std` library headers

### General Best Practices
- Always make use of [[Header Guards]]
- Do not [[../Concepts/Declaration & Definition|define]] variables/ functions in header files
	→ Global constants are an exception tho
- Name them equally to a `.cpp` file, but with the file ending `.h` (or `.hpp` to mark difference from C header files)
	→ Don't include `*.cpp` files
- Each header should have *one specific job*
- Each header should generally be as independent as possible & every header should definitively *compile on it's own*
- Include as specific headers as explicit as possible
