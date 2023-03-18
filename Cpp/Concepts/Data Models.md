---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Data Models
linter-yaml-title-alias: Data Models
date-of-creation: 2023-01-12
mod-date: 2023-01-12
---

# Data Models
- The choice of size of the fundamental data type primitives

## 32 Bit
- LP32 (`int` 2 Byte, `long` & pointer 4 Byte)
	→ Win16 API
- ILP32 (`int, long` & pointer 4 Byte)
	→ Win32, Unix(-like)

## 64 Bit
- LLP64 (`int,long` 4 Byte, pointer 8 Byte)
	→ Win64
- LP64 (`int` 4 Byte, `long` & pointer 8 Byte)
	→ Unix (-like)
