---
tags: practical-cs prog cpp
cards-deck: 
completed: true
aliases: xmake.lua
linter-yaml-title-alias: xmake.lua
date-of-creation: 2023-03-05
mod-date: 2023-03-05
---

# xmake.lua
→ [[Compiler & Processing/Compiler Arguments|Compiler Arguments]]
```lua
add_rules("mode.debug", "mode.release")

-- xmake settings
	set_policy("build.warning", true)
	set_warnings("allextra") -- , "error") -- -w execution parameter

-- Language settings
	set_languages("clatest", "cxx20") -- cxxlatest
	set_policy("build.c++.modules", true)
	set_policy("build.optimization.lto", true)

-- Compiler settings
	add_cxflags("-march=native") -- TODO Remove this
	add_cxxflags("-pedantic", "-Weffc++", "-Wsign-conversion", "-Wshadow")
	set_optimize("fast")

-- Dependencies etc.
add_requires("boost", {system = true})


target("ProPro_remastered_xmake")
	set_kind("binary")
	add_files("src/*.cppm")

target("test")
	set_kind("binary")
	add_files("src/*.cppm")
	add_packages("boost.test")

--	add_defines("NDEBUG", "_GNU_SOURCE=1")

--	add_includedirs("/usr/include", "/usr/local/include")

--	-- add link libraries and search directories
--	add_links("tbox")
--	add_linkdirs("/usr/local/lib", "/usr/lib")

--	-- add system link libraries
--	add_syslinks("z", "pthread")

--	-- add compilation and link flags
--	add_ldflags("-lpthread", {force = true})
```

## Not working due to compiler error
```lua
add_rules("mode.debug", "mode.release")

-- xmake settings:
	set_policy("build.warning", true)
	set_warnings("allextra") -- , "error") -- -w execution parameter

-- Language settings:
	set_languages("cxx20") -- "clatest", cxxlatest
	set_policy("build.c++.modules", true)
	--set_policy("build.optimization.lto", true) -- Turned off due to modules failing

-- Compiler settings:
	add_cxxflags("-pedantic", "-Weffc++", "-Wsign-conversion", "-Wshadow") -- , "-fmodules")
	add_cxflags("-march=native", "-fuse-ld=mold") -- TODO Remove this
	set_optimize("none") -- none fast faster fastest

-- Dependencies etc.:
	add_requires("boost", {configs = {shared = true}}) -- , {system = true})


target("<project_name>") -- TODO
	set_default(true)
	set_kind("binary")
	add_files("src/main.cppm", "src/base/*.cppm")


task("test")
	on_run( function()
		os.execute("xmake build -g test -j8")
		os.execute("xmake run -g test")
	end)

target("test_prep")
	set_group("test")
	set_kind("phony")
	add_files("src/base/*.cppm")
	-- Test Dependencies:
	add_packages("boost/test") -- Implicitly included on other test targets?

target("blackbox")
	set_group("test")
	set_kind("binary")
	add_files("src/test/blackbox.cppm")

--	add_defines("NDEBUG", "_GNU_SOURCE=1")

--	add_includedirs("/usr/include", "/usr/local/include")

--	-- add link libraries and search directories
--	add_links("tbox")
--	add_linkdirs("/usr/local/lib", "/usr/lib")

--	-- add system link libraries
--	add_syslinks("z", "pthread")

--	-- add compilation and link flags
--	add_ldflags("-lpthread", {force = true})
```

## last failing try before build2
```lua
add_rules("mode.debug", "mode.release", "mode.releasedbg")

-- xmake settings:
	set_defaultmode("debug") -- debug releasedbg release
	set_policy("build.warning", true)
	set_warnings("allextra", "error") -- -w execution parameter

-- Language settings:
	set_languages("c++20") -- "clatest", cxxlatest
	set_policy("build.c++.modules", true)
	--set_policy("build.optimization.lto", true) -- Turned off due to modules failing

-- Compiler settings:
	add_cxxflags("-pedantic", "-Weffc++", "-Wsign-conversion", "-Wshadow") -- , "-fmodule-header")
	add_cxflags("-march=native") -- TODO Remove this
	set_optimize("fast") -- none fast faster fastest

-- Dependencies etc.:
	add_requires("boost", {configs = {shared = true}}) -- , {system = true})


target("project")
	set_default(true)
	set_kind("binary")
	add_files("src/main.cpp", "src/base/*.cpp")


task("test")
	on_run( function()
		os.execute("xmake build -g test -j8")
		os.execute("xmake run -g test")
	end)

target("blackbox")
	set_default(false)
	set_kind("binary")
	set_group("test")
	add_packages("boost/test")
	add_files("src/base/*.cpp", "src/test/*.cpp")

--	add_defines("NDEBUG", "_GNU_SOURCE=1")

--	add_includedirs("/usr/include", "/usr/local/include")

--	-- add link libraries and search directories
--	add_links("tbox")
--	add_linkdirs("/usr/local/lib", "/usr/lib")

--	-- add system link libraries
--	add_syslinks("z", "pthread")

--	-- add compilation and link flags
--	add_ldflags("-lpthread", {force = true})
```
