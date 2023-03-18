---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Escape Characters
linter-yaml-title-alias: Escape Characters
date-of-creation: 2023-03-16
mod-date: 2023-03-16
---

# Escape Characters

## Advanced
| Symbol              | Meaning                                         |
| ------------------- | ----------------------------------------------- |
| `\a`                | Alert                                           |
| `\b`                | Backspace                                       |
| `\f`                | Formfeed: Moves the cursor to next logical page |
| `\r`                | Return: Moves cursor to beginning of line       |
| `\v`                | Vertical Tab                                    |
| `\n`$\in\mathbb{N}$ | Translate $n$ into octal represented `char`     |
| `\xn`$"$            | Translate $n$ into hex  represented `char`      | 

## Examples
```cpp
	std::cout << "6F in hex is char '\x6F'\n"; // 6F in hex is char 'o'
	std::cout << "Bad\b\b\bNice\n"; // Nice
	std::cout << "Important line\rTrollololol\n"; // Trollolololine
	std::cout << "\v";
```