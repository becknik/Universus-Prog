---
tags: practical-cs prog cpp
cards-deck: Private::Prog::C++
completed: true
aliases: cmake
linter-yaml-title-alias: cmake
date-of-creation: 2023-03-09
mod-date: 2023-03-13
---

# cmake

## Example
`<project_root>/CMakeList.txt`:
```bash
cmake_minimum_required(VERSION 3.24)


set(YES_PLEASE_GIVE_ME_WARNINGS ON) # Enables advanced compiler warning output
set(ENABLE_IWYU OFF) # Enable the include-what-you-use analyzer
set(ENABLE_CCACHE OFF)


# Automated setup of mold & GNU gold linker if detected
if (UNIX)
	execute_process(COMMAND ${CMAKE_C_COMPILER} -fuse-ld=mold -Wl,--version ERROR_QUIET OUTPUT_VARIABLE mold_version_info)
	execute_process(COMMAND ${CMAKE_C_COMPILER} -fuse-ld=gold -Wl,--version ERROR_QUIET OUTPUT_VARIABLE gold_version_info)
	if ("${mold_version_info}" MATCHES "mold")
		message(STATUS "Setting mold as linker")
		set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -fuse-ld=mold -Wl,--disable-new-dtags")
		set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -fuse-ld=mold -Wl,--disable-new-dtags")
	elseif ("${gold_version_info}" MATCHES "GNU gold")
		message(STATUS "Setting GNU gold as linker")
		set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -fuse-ld=gold -Wl,--disable-new-dtags")
		set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -fuse-ld=gold -Wl,--disable-new-dtags")
	else ()
		message(STATUS "Using default linker. Neither mold nor GNU gold linker were found.")
	endif ()
endif ()

if (YES_PLEASE_GIVE_ME_WARNINGS)
	message(STATUS "Enabling advanced compiler warning flags")
	add_compile_options(-Wall -Wextra -pedantic -Weffc++ -Wsign-conversion -Wshadow)
endif ()

# Automated ccache setup
if (ENABLE_CCACHE)
	find_program(CCACHE_FOUND ccache)
	if (CCACHE_FOUND)
		message(STATUS "Enabling ccache support")
		set_property(GLOBAL PROPERTY CMAKE_CXX_COMPILER_LAUNCHER ccache)
		#set_property(GLOBAL PROPERTY CMAKE_CXX_LINKER_LAUNCHER ccache) # Linking doesn't benefit from ccache
	endif ()
endif ()

# Automated include-what-you-use setup
if (ENABLE_IWYU)
	#if (CMAKE_CXX_COMPILER_ID MATCHES "Clang") # Doesn't work...
	find_program(IWYU_EXE include-what-you-use)
	if (${IWYU_EXE})
		#message(STATUS "Found 'include-what-you-use' - your compiler is Clang!")
		message(STATUS "Enabling 'include-what-you-use' analyzer")
		set(CMAKE_CXX_INCLUDE_WHAT_YOU_USE "${IWYU_EXE}")
	else()
		message(STATUS "'include-what-you-use' analyzer not found on system")
	endif()
	#endif()
endif ()

## Project configuration

project(snake VERSION 0.1 LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 20)

# Library setup

find_package(spdlog REQUIRED)
find_package(fmt REQUIRED)
#add_library(fmt SHARED IMPORTED)
#set_target_properties(fmt PROPERTIES IMPORTED_LOCATION /lib/libfmt.so)

find_package(Qt6 REQUIRED COMPONENTS Core Widgets)
qt_standard_project_setup()

## Target setup

file(GLOB EXE_INCLUDE_FILES ${PROJECT_SOURCE_DIR}/src/*.?pp*) # include .cpp, .hpp, .mpp & .cppm files
add_executable(snake ${EXE_INCLUDE_FILES})
target_link_libraries(snake PRIVATE Qt6::Widgets fmt)

# Test setup

enable_testing()
add_subdirectory(${PROJECT_SOURCE_DIR}/test)

```
`<project_root>/test/CMakeList.txt`:
```bash
include(CTest)

# Library setup

find_package(Boost REQUIRED COMPONENTS unit_test_framework)
#set(Boost_THREADAPI pthread)

# Target setup

include_directories(${PROJECT_SOURCE_DIR}/src)
file(GLOB RELATIVE UNIT_TEST_FILES *.[c,h]pp*)

add_executable(unit_tests ${UNIT_TEST_FILES})
target_link_libraries(unit_tests PRIVATE Boost::unit_test_framework)

add_test(NAME unit_tests COMMAND unit_tests)

#add_executable(<…>_unit_tests <…>_test.cpp ../src/<…>)
#target_link_libraries(<…>_unit_tests PRIVATE Boost::unit_test_framework)
#add_test(NAME <…>_unit_tests COMMAND unit_tests)

```

## [[Concepts/Modules|Modules]] "Support"
```bash
set(CMAKE_CXX_STANDARD 20)

# https://www.kitware.com/import-cmake-c20-modules/
# CMake 3.25
set(CMAKE_EXPERIMENTAL_CXX_MODULE_CMAKE_API "3c375311-a3c9-4396-a187-3227ef642046")
# CMake 3.26
#set(CMAKE_EXPERIMENTAL_CXX_MODULE_CMAKE_API "2182bf5c-ef0d-489a-91da-49dbc3090d2a")

# https://gitlab.kitware.com/cmake/cmake/-/blob/master/.gitlab/ci/cxx_modules_rules_gcc.cmake
set(CMake_TEST_CXXModules_UUID "a246741c-d067-4019-a8fb-3d16b0c9d1d3")

set(CMAKE_EXPERIMENTAL_CXX_MODULE_DYNDEP 1)
string(CONCAT CMAKE_EXPERIMENTAL_CXX_SCANDEP_SOURCE
	"<CMAKE_CXX_COMPILER> <DEFINES> <INCLUDES> <FLAGS> -E -x c++ <SOURCE>"
	" -MT <DYNDEP_FILE> -MD -MF <DEP_FILE>"
	" -fmodules-ts -fdep-file=<DYNDEP_FILE> -fdep-output=<OBJECT> -fdep-format=trtbd"
	" -o <PREPROCESSED_SOURCE>")
set(CMAKE_EXPERIMENTAL_CXX_MODULE_MAP_FORMAT "gcc")
set(CMAKE_EXPERIMENTAL_CXX_MODULE_MAP_FLAG "-fmodules-ts -fmodule-mapper=<MODULE_MAP_FILE> -fdep-format=trtbd -x c++")
```

---
Further Sources:
- https://github.com/Kitware/CMake/blob/master/Help/dev/experimental.rst
