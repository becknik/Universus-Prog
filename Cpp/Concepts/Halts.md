---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Halts
linter-yaml-title-alias: Halts
date-of-creation: 2023-03-17
mod-date: 2023-03-17
---

# Halts

## Ordinary
- Calling `std::exit()` explicitly early with a status code
	→ Does not clean up the call stack
	→ header: `<cstdlib>`
- Calling `std::aexit()` with a cleanup function
- In multithreaded environments:
	- `std::quick_exit()` leaves `static` variables untouched
		→ Other automatic cleanups not specified #TODO
	- `std::at_quick_exit()` plays the same role as `std::aexit()`

## Abnormally
- `std::abort()` doesn't do cleanup
- `std::terminate()` which is called implicitly by uncatched exceptions
	→ Internally calls `std::abort()`
