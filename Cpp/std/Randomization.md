---
tags: practical-cs prog cpp
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Randomization
linter-yaml-title-alias: Randomization
date-of-creation: 2023-03-17
mod-date: 2023-03-17
---

# Randomization

## C++
- [Comprehensive blog entry](https://arvid.io/2018/06/30/on-cxx-random-number-generator-quality/)

### Mersenne Twister
- Has some issues, like predictability after 625 number generations
```cpp
	std::mt19937 mt{ std::random_device{}() };
	std::mt19937 mt{ static_cast<unsigned int>(
		std::chrono::steady_clock::now().time_since_epoch().count()
		) }; // steady_clock > high_resolution_clock ← can be modified by user
	std::random_device rd;
	std::seed_seq ss{ rd(), rd(), rd(), rd(), rd(), rd(), rd(), rd() }
	std::mt19937 mt{ ss };
```
→ [[../Concepts/Value Categories|Temporary Objects]]
- Using self-seeding variant wrapped inside a header file:
	→ The inline keyword also means we only have one global instance for our whole program
```cpp
#pragma once

#include <chrono>
#include <random>

namespace random_mt
{
	inline std::mt19937 init()
	{
		std::random_device rd;
		std::seed_seq ss{ static_cast<unsigned int>(std::chrono::steady_clock::now().time_since_epoch().count()),
			rd(), rd(), rd(), rd(), rd(), rd(), rd() };

		return std::mt19937{ ss };
	}

	/// Globally shared, initalized mt19937 instance
	inline std::mt19937 mt{ init() };

	/// Generate a random number between [min, max] (inclusive)
	inline int get(int min, int max)
	{
		std::uniform_int_distribution die{ min, max };
		return die(mt);
	}
};
```

## Modern

### Non-Cryptographic
- [Wyhash](https://github.com/wangyi-fudan/wyhash)
- [xoshiro](https://prng.di.unimi.it/)

### Cryptographic
- [ChaCha Family]()https://www.cryptopp.com/wiki/ChaCha20
