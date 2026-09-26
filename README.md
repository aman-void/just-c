# just-c

A hands-on repository for learning **C programming**.

Core reference is _Programming in C_ (Stephen G. Kochan, 4th edition, 2014), which is based on ANSI C11 (ISO/IEC 9899:2011). Every example here is compiled with C23.

## Compiler

This repository uses **GCC** as the primary C compiler.

```bash
gcc --version
```

Current toolchain:

```text
GCC       16.2.1
Clang     22.1.8
C Standard C23
```

---

# Everyday Commands

## Compile

Compile a C file:

```bash
gcc main.c -o main
```

Run it:

```bash
./main
```

Compile using C23 with useful warnings:

```bash
gcc -std=c23 -Wall -Wextra main.c -o main
```

### Useful flags

| Flag       | Purpose                       |
| ---------- | ----------------------------- |
| `-std=c23` | Use the C23 language standard |
| `-Wall`    | Enable common warnings        |
| `-Wextra`  | Enable additional warnings    |
| `-g`       | Add debugging information     |
| `-o`       | Specify output filename       |

A good default while learning:

```bash
gcc -std=c23 -Wall -Wextra -g main.c -o main
```

---

# Project Structure

Each numbered directory is one topic. Flat layout, no Makefiles, no `src/`:

```text
just-c/
├── README.md
├── .gitignore
│
├── 01-hello-c/
│   ├── main.c
│   └── README.md
│
├── 02-variables-types/
│   ├── main.c
│   └── README.md
│
└── ...
```

Each topic's `README.md` holds notes, experiments, and C23 observations for that topic.
