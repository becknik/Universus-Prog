---
tags: 
cards-deck: 
completed: true
aliases: char & wchar_t
linter-yaml-title-alias: char & wchar_t
date-of-creation: 2023-03-16
mod-date: 2023-03-16
---

# char & wchar_t
→ https://stackoverflow.com/a/402918

## Summarizing
- On Windows `wchar_t` & `std::wstring` should be preferred over `char` & `std::string`
	→ On Linux character encoding is implicit in Unicode, therefore `std::wstring` is not needed
