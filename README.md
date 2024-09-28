# Infrastructure for C/C++ Programming

This repo has sample `.editorconfig` files and `.clang-format` files for C/C++,
and also a Universal Makefile.

Everything here is dual-licensed under Public Domain (CC0) and MIT, so you can
choose what fits best for you.

## How to use the Makefile

The Makefile in this repo automatically detects every `.c` and `.cpp` file
recursively in a defined source folder, creates a rule for a corresponding
object file in a defined target folder and a rule for linking the final
executable. Also, it manages release and debug build profiles.

The targets that you should use are just `target`, `debug`, and `clean`. The
target `target` is the default and builds the "release mode". The `debug` builds
the "debug mode", and `clean` removes the directory with objects and the
binaries.

### Configuring the Makefile

Optionally set variables in the `config.mk` file. It works if that file doesn't
even exist, so no worry, everything has a sane default.

### Variables

- **SRC (path)**: Directory with source files. Defaults to `src/`.
- **BUILD_TARGET (path)**: Directory with object files. Defaults to `build/`.
- **TARGET (path)**: Executable to create. Defaults to `a.out`.
- **DEBUG_SUFFIX (string)**: Will be appended to all objects and the target
  before extension, as to compile the versions with debug symbols. Defaults to
  `-debug`.
- **CPP_EXTENSION (string)**: File extension (without dot) to consider as C++
  files, as some may use `.cpp` and some `.cc`. Defaults to `cpp`.
- **CC (path)**: Default C compiler to use. If this variable is set and the
  compiler does not exist in PATH, it autodetects between the following
  compilers (in this order): `clang`, `gcc`, `cc`.
- **CPP (path)**: Same as `CC` but for C++. Autodetects between `clang++`, `g++`,
  and `c++`.
- **FORCE_CC (bool)**: If this variable is set, refuses to try compiling with a
  different compiler than the default set with `CC`. Does nothing without `CC`
  being set.
- **FORCE_CPP (bool)**: Same as `FORCE_CC` but for C++.
- **CFLAGS (list)**: Default C compiler flags. Defaults to `-Wall -Wextra`.
- **C_DEBUG_FLAGS (list)**: Additional C compiler flags for debug build mode.
  Defaults to `-Og -g`.
- **C_RELEASE_FLAGS (list)**: Additional C compiler flags for release build mode.
  Defaults to `-O2`.
- **CPPFLAGS (list)**: Same as `CFLAGS` but for C++. Same defaults.
- **CPP_DEBUG_FLAGS (list)**: Same as `C_DEBUG_FLAGS` but for C++. Same defaults.
- **CPP_RELEASE_FLAGS (list)**: Same as `C_RELEASE_FLAGS` but for C++. Same
  defaults.
- **LD_FLAGS (list)**: Flags to pass when linking. Defaults to none (unset).
