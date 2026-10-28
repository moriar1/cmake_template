# Requirements

- Unix-like OS
- clang
- clang-format
- clang-tidy
- lld
- git
- ninja
- cmake

**Debian**:

```sh
sudo apt update && sudo apt upgrade -y
sudo apt install -y git clang clangd clang-tidy clang-format llvm-19 cmake ninja-build build-essential
```

**Arch Linux**:

```sh
sudo pacman -Syu
sudo pacman -S git clang lld ninja cmake base-devel llvm20 
```

**FreeBSD**:

```sh
sudo pkg update && sudo pkg upgrade -y
sudo pkg install -y git cmake ninja llvm21
```

# Usage

## CMakePresets
```sh
git clone https://github.com/moriar1/c_template
cp -ir c_template/cmake_template MyProject
cd MyProject
cmake --preset clang-debug
cmake --build --preset clang-debug
./build/clang-debug/MyProject
```

## CMake
 
```sh
git clone https://github.com/moriar1/c_template
cp -ir c_template/cmake_template MyProject
cd MyProject
md build
cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=1 -DCMAKE_C_COMPILER=clang -DCMAKE_C_CLANG_TIDY=clang-tidy -G Ninja -B build -S .
cmake --build build
./build/MyProject

# Optional:

# for clangd
ln -s build/compile_commands.json .

# custom targets
cmake --build build --target run-tidy-full
cmake --build build --target build-info
cmake --build build --target check-format
cmake --build build --target format

# Tests
cmake --preset clang-debug
cmake --build --preset clang-debug
ctest --preset clang-debug
```

# TODO


## Macros

Not really usefull macros: see `./misc/custom.h` file

## Cmake

- targets: doc, uninstall
- CI/CD
- clang-tidy: https://github.com/jenisys/explore.clang-tidy

https://gitlab.kitware.com/cmake/community/-/wikis/FAQ

https://github.com/airbus-seclab/c-compiler-security/blob/master/clang_compilation.md
