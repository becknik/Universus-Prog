---
tags: practical-cs prog cpp compiler
sources: learncpp.com
cards-deck: Private::Prog::C++
completed: true
aliases: Compiler Arguments
linter-yaml-title-alias: Compiler Arguments
date-of-creation: 2022-12-16
mod-date: 2023-03-09
---

# Compiler Arguments
-> My own [Compiler Explorer Preset](https://godbolt.org/#z:OYLghAFBqd5QCxAYwPYBMCmBRdBLAF1QCcAaPECAMzwBtMA7AQwFtMQByARg9KtQYEAysib0QXACx8BBAKoBnTAAUAHpwAMvAFYTStJg1DIApACYAQuYukl9ZATwDKjdAGFUtAK4sGIM6SuADJ4DJgAcj4ARpjEIADspAAOqAqETgwe3r7%2ByanpAiFhkSwxcYl2mA4ZQgRMxARZPn4BldUCtfUERRHRsQm2dQ1NOa1D3aG9pf3xAJS2qF7EyOwc5gDMocjeWADUJutuTgoExJisB9gmGgCC1zdMXkS7LEyhELO7ALSXu6EE9xM8Sst12YN2J3QIBQiwI%2B0OBzc%2BzMZgAEphaLRULsAOokWjoEwAVjcDHMZgOIJu4N2ZwISwYuw0lMB8QAIhx5rROETeH4OFpSKhOG5rNYIYtlphkeseKQCJpOfMANYgIkafScSR8xVCzi8BQgDUKgWc0hwWAwRAwlhJOixciUNC2%2B1xbaGYBcdUarAANzwKwAanhMAB3ADySUYnDlNFoBFihogUV1UVC9QAnjHeGnmMQM%2BGotoqia5c62IJwwxaFnTaQsK8jOI6/gztVfZhDXXMKoqk9VnL/hjdbQ8FFiJmPFhdac8Cxs/MqAZgApg2HI9HuLx%2BIIRGJ2FIZIJFCp1HXdAEDEYUGLLPox4bIPNUElHAIu19IQc2aZLNYzBo3zhmY3zAAaGIlhkLgMO4njNHowSTCUZR6CkaRvpkcE5FweToRkPTIf0OFtBhnTDFhfjERB7QMGREzFH0cTEeMIyUYMXQEYxEjzAokorNxmocLypD8oKwocLsqgABwAGxfDJki7O6Ri7F6AB0GgabsEC4IQJAylwsy8CaWizPMCDnFgcQfKQqrqoJ2qkPO9mibw4kGka8qKvMFrWs6dr0GQFAQP5rogJ6KL1pg/pBiGEZRvysZ0AmxBJimda5pm2akJl%2BaFsWDjZeWjAEFWNa6g2HrNoKraQR2XaCj2fYJtlQ7cnWo7jpOGCrIKs7zlui7LqucUbol26yHu4iHju8hKGouq6Os%2Bgejef53p1j42S%2BGEfl%2B6w/reFgAUBIFfGBtjURh0GwdkbGIQx0xMbhBSYXdqH5BhnFPXoJE1CxFG/Vd/0cUhXHMV0rG/eM30oYZCxLPx8PtcJrl6hJ0lyQpuzAMgyCqWYakgTp%2BBEMQBlGV5ppmQ5vDORqaPubYnkmUqtlqhq7XrDqdZM6zNPtWYPNifqVOmfMHapVBkhAA)

## Configs

### All-In
```bash
g++ -std=c++20 \
-Werror -Wall -Wextra -pedantic -Weffc++ -Wsign-conversion -Wshadow \
-flto -fuse-ld=mold -O -march=native -ggdb \
-I./headers -o main.o main.cpp
```

### Developement
```bash
g++ -std=c++20 \
-Werror -Wall -Wextra -pedantic -Weffc++ -Wsign-conversion -Wshadow \
-fuse-ld=mold -O2 -march=x86-64-v3 -ggdb \
-I./headers -o main.o main.cpp
```

### C++20 [[../Concepts/Modules|Modules]]
```bash
g++ -fmodule-header -std=c++20 -c <header>.hpp
g++ -fmodules-ts -std=c++20 -c -x c++-system-header <iostream>
g++ -fmodules-ts -std=c++20 main.cppm
```
- `-x` implies C++ header file
	- Options: `c++-header`, `c++-user-header`, `c++-system-header`
	- The later two search in include systems directories
- `-fmoldue-header` implies `-fmodule-ts`

### Extensive with diagnostics (works with `clang` only)
```bash
g++ -std=c++20  -march=native -O -fuse-ld=mold -flto  -ggdb  -Weverything -Wno-c++98-compat -Wno-c++-compat -Wno-c++98-compat-pedantic -Wno-newline-eof  -I./headers  <main>.cpp -o <main>.o
```

## Compiler Selection
- `g++` < `clang++` in therms of beauty, compiler warning & error output
- `clang++` < `g++` in therms of available CPU/[[../../../../../Uni/Ro I/CPU/Befehlssatz Architektur|ISA]] specific optimizations

## Arguments "Sections"
- Compiler & language standard: `clang++ -std=c++20`
- Optimization & debugging: `-march=native -mtune=native -O0 -fuse-ld=mold -flto  -ggdb`
- Trigger all errors & diagnostics: `-Weverything -Wno-c++98-compat -Wno-c++-compat -Wno-c++98-compat-pedantic -Wno-newline-eof`
- Trigger the most important errors: `-Werror -Wall -Wextra -pedantic -Weffc++ -Wsign-conversion -Wshadow`
- Header files in sub-folder: `-I ./headers`
- Selection of target & source files: `<main>.cpp -o <main>.o`

## Explanation

### Misc
- `-std=c++20`/ `-std=c++2b` - Using the newest standard, not supported by my current distros repos…
- `-mach=native` - Enables generation to subset of host CPU-specific assembly instructions
- `-mtune=native` - Produces code optimized for the host CPU under no constraint of ISA instruction subset ([source](https://gcc.gnu.org/onlinedocs/gcc/x86-Options.html))
	→ Optimizes e.g. for the loop branch heuristics of the hosts CPU, but the program should also run on other CPUs
- `-O0` - Turns of compiler optimization for better debugging experience, might be swapped with `-02` or even `-03` for performance testing/ release builds
- `-fuse-ld=mold` - Replaces GGCs `ldgold` and Clangs `lld` with the modern & fast `mold` linker!
- `-flto` - Perform link time optimization on LLVM/ ELF files for enhanced runtime performance in cost of a little link time

### Warnings
- `-ggdb` - For debugging infos, in this instance for the "extensive" informations GDB uses
	→ There seems to be `-g` which "only" produces the infos for the OSes native format & `-ggdb3` for further extra infos like macros [^1]
- `-Weverything` - Enable all available diagnostics [source](https://clang.llvm.org/docs/UsersManual.html?highlight=weverything#diagnostics-enable-everything)
- `-Werror` - Converts all warnings to errors
- `-Wall` - Warn about use of questionable CPP features
- `-Wextra` - Enable check for extra warnings
- `-pedantic`/`-pedantic-errors` - Warn/ error on use of compiler language extensions to go for strict ISO
- `-Weffc++` - Check for violations from a popular text book rules
- `-Wsign-conversion` - Warn about explicit conversions
- `-Wshadow ` - Warns about (global, local) variable shadowing
	→ Should be avoided using `g_` prefix for globs or generally avoid them

[^1]: [GCC](https://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/Debugging-Options.html#Debugging-Options)
