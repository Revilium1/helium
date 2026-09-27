# Helium

**Helium** is a lightweight, statically typed programming language and compiler written as an experimental and educational project.

Helium currently compiles source code into **x86-64 NASM assembly** and uses **NASM** and **`ld`** to assemble and link the resulting program.

> **Note:** Helium is still in a very early stage of development. The language currently has very limited functionality and is primarily a learning project.

## Features

Currently implemented:

- Statically typed syntax
- Semicolon-terminated statements
- `exit` statements
- Proper source tokenization
- Proper source parsing
- Code generation
- Compilation to x86-64 NASM assembly
- Automatic assembly and linking with NASM and `ld`

For example:

    exit 42;

## Version 0.2

Version **0.2** introduces a proper compiler pipeline for Helium.

The compiler now processes source code through three main stages:

1. **Tokenization** — source code is converted into a stream of tokens.
2. **Parsing** — tokens are analyzed according to Helium's grammar and converted into a structured representation.
3. **Code generation** — the parsed representation is converted into x86-64 NASM assembly.

This establishes a proper separation between the source language, its syntax, and the generated assembly.

**Version 0.2 does not introduce any new language syntax.** The language still has the same limited set of constructs as before, with `exit` being the primary implemented language construct. The focus of v0.2 is the compiler infrastructure required to support additional language features in future releases.

## Requirements

To build and use Helium, you will need:

- **CMake 3.20 or newer**
- A **C++20-compatible compiler**
- [NASM](https://www.nasm.us/)
- **GNU `ld`**

Helium currently targets **x86-64 Linux** using the NASM `elf64` output format.

## Building

Build the compiler with CMake:

    cmake -S . -B build
    cmake --build build

The resulting executable will be located at:

    ./build/heli

## Usage

Compile a Helium source file by passing it to the compiler:

    ./build/heli <file.he>

For example:

    ./build/heli example.he

The compiler generates an `.asm` file from the source and then invokes NASM and `ld` to assemble and link the generated assembly into an executable.

## Example

An example file, `example.he`, is included in the repository. It currently demonstrates the language features implemented so far.

A minimal Helium program looks like:

    exit 42;

The source is tokenized, parsed, and then passed to the code generator to produce the corresponding x86-64 NASM assembly.

## Compiler Pipeline

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

The pipeline is intentionally kept simple for now, but provides the foundation for adding more language constructs in future versions.

## Project Structure

The project is currently kept intentionally small:

    .
    ├── src/          # Helium compiler source code
    ├── docs/         # Documentation regarding Helium. Currently only GRAMMAR.md
    ├── example.he    # Example using the currently implemented features
    ├── run           # A simple shell script to automate building and running the compiler
    ├── CMakeLists.txt
    ├── LICENSE
    └── README.md

As the project grows, additional directories and components may be added.

## Development Status

Helium is **experimental and under active development**.

Version 0.2 focuses on establishing a proper compiler architecture with tokenization, parsing, and code generation. The language itself still has very few features, with `exit` being the primary implemented language construct.

No new syntax has been added in v0.2. Future versions will build on the new compiler pipeline to introduce additional language features.

The design and goals of the language are still evolving, so syntax and compiler behavior may change significantly.

## License

Helium is licensed under the **MIT License**