# Helium

**Helium** is a lightweight, statically typed programming language and compiler written as an experimental and educational project.
> **Note:** Helium is still in a very early stage of development. The language currently has very limited functionality and is primarily a learning project.
## Features

Currently implemented:

- Statically typed syntax
- Semicolon-terminated statements
- `exit` statements
- `let` statements
- Variables (all are treated as const int)
- Proper source tokenization
- Proper source parsing
- Code generation
- Compilation to x86-64 NASM assembly
- Automatic assembly and linking with NASM and `ld`
## Requirements

To build and use Helium, you will need:

- **CMake 3.20 or newer**
- A **C++20-compatible compiler**
- [NASM](https://www.nasm.us/)
- **GNU `ld`**

Helium currently targets **x86-64 Linux** using the NASM `elf64` output format.
## Installation

Build the compiler with CMake:
```
    cmake -S . -B build
    cmake --build build
```
The resulting executable will be located at:
```
    ./build/heli
```
## Version 0.3
Version **0.3** introduces variables, and identifiers in general.  
The compiler now:  
 - Lets you define variables that can be used any time with `let`
 - Allows you to exit with a variable as it's exit code
 - Allows you to define another variable with a variable, e.g `let a = b;`  

This establishes the foundation for identifiers and variable references in the language.
## Usage/Examples

Compile a Helium source file by passing it to the compiler:
```
    ./build/heli <file.he>
```
For example:
```
    ./build/heli example.he
```
The compiler generates a `.asm` file from the source and then invokes NASM and `ld` to assemble and link the generated assembly into an executable.

An example file, `example.he`, is included in the repository. It currently demonstrates the language features implemented so far.

A minimal Helium program looks like:
```he
    exit 42;
```
The source is tokenized, parsed, and then passed to the code generator to produce the corresponding x86-64 NASM assembly.
## Compiler Pipeline

```
The current compiler pipeline is:

    Helium source
         │
         ▼
    Tokenization
         │
         ▼
    Parsing
         │
         ▼
    Code Generation
         │
         ▼
    x86-64 NASM assembly
         │
         ▼
        NASM
         │
         ▼
    ELF64 object file
         │
         ▼
         ld
         │
         ▼
    Executable
```
The pipeline is intentionally kept simple for now, but provides the foundation for adding more language constructs in future versions.
## Project Structure

The project is currently kept intentionally small:
```
    .
    ├── src/          # Helium compiler source code
    ├── docs/         # Documentation regarding Helium. Currently only GRAMMAR.md
    ├── example.he    # Example using the currently implemented features
    ├── run           # A simple shell script to automate building and running the compiler
    ├── CMakeLists.txt
    ├── LICENSE
    └── README.md
```
As the project grows, additional directories and components may be added.
## Development Status
Helium is **experimental and under active development**.

Version 0.2 focuses on establishing a proper compiler architecture with tokenization, parsing, and code generation. The language itself still has very few features, with `exit` and `let` being the primary implemented language constructs.

The design and goals of the language are still evolving, so syntax and compiler behavior may change significantly.
## Liscense
Helium is licensed under the **MIT License**
