# Helium

**Helium** is a lightweight, statically typed programming language and compiler written as an experimental and educational project.

Helium currently compiles source code into **x86-64 NASM assembly** and uses **NASM** and **`ld`** to assemble and link the resulting program.

> **Note:** Helium is still in a very early stage of development. The language currently has very limited functionality and is primarily a learning project.

## Features

Currently implemented:

- Statically typed syntax
- Semicolon-terminated statements
- `return` statements
- Compilation to x86-64 NASM assembly
- Automatic assembly and linking with NASM and `ld`

For example:

```he
return 42;
```

## Requirements

To build and use Helium, you will need:

- **CMake 3.20 or newer**
- A **C++20-compatible compiler**
- [NASM](https://www.nasm.us/)
- **GNU `ld`**

Helium currently targets **x86-64 Linux** using the NASM `elf64` output format.

## Building

Build the compiler with CMake:

```bash
cmake -S . -B build
cmake --build build
```

The resulting executable will be located at:

```text
./build/heli
```

> **Note:** The project's `CMakeLists.txt` is currently located in the `src/` directory, which is why `./src` is passed as the CMake source directory.

## Usage

Compile a Helium source file by passing it to the compiler:

```bash
./build/heli <file.he>
```

Helium generates an `.asm` file with the same base filename as the source file.

For example:

```bash
./build/heli example.he
```

will generate:

```text
out.asm
```

The compiler then invokes NASM and `ld` to assemble and link the generated assembly into an executable.

## Example

An example file, `example.he`, is included in the repository. It currently demonstrates all of the language features implemented so far.

A minimal Helium program looks like:

```he
return 42;
```

## Project Structure

The project is currently kept intentionally small:

```text
.
├── src/          # Helium compiler source code and CMakeLists.txt
├── example.he    # Example using the currently implemented features
├── run           # A simple shell script to automate building and running the compiler
├── CMakeLists.txt
├── LICENSE
└── README.md
```

As the project grows, additional directories and components may be added.

## Development Status

Helium is **experimental and under active development**.

The language currently has very few features, with `return` being the only implemented language construct. The design and goals of the language are still evolving, so syntax and compiler behavior may change significantly.

## License

Helium is licensed under the **MIT License**.
