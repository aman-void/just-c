# History of C language

## Table of Contents

- [1. Before C: Assembly was the problem](#1-before-c-assembly-was-the-problem)
- [2. BCPL -> B -> C](#2-bcpl--b--c)
- [3. 1971–1972: C is born](#3-19711972-c-is-born)
- [4. The killer application: Unix](#4-the-killer-application-unix)
- [5. Why C became powerful](#5-why-c-became-powerful)
- [6. 1978: K&R C](#6-1978-knr-c)
- [7. The problem: C needed a standard](#7-the-problem-c-needed-a-standard)
- [8. C99](#8-c99)
- [9. C11](#9-c11)
- [10. C17](#10-c17)
- [11. C23: the C i am exploring](#11-c23-the-c-i-am-exploring)
- [12. The entire Timeline](#12-the-entire-timeline)
- [13. The important historical lesson](#13-the-important-historical-lesson)

C has a surprisingly interesting history because it wasn't designed as an academic language. It was built to solve a very practical problem: **Write an OS without writing everything in assembly**. Humanity, for once, has a sensible reason for inventing another programming language.

# 1. Before C: Assembly was the problem

In the 1960s, system software was commonly written in assembly language.
Assembly gives you very precise control over the machine, but it has an obvious problem:

```text
Assembly program
      ↓
Tied closely to one CPU architecture
      ↓
Hard to maintain
      ↓
Hard to port
```

At Bell Labs, researchers were working on **Multics**, a large operating-system project involving MIT, General Electric, and Bell Labs.

Bell Labs eventually withdrew from Multics. Around 1969, **Ken Thompson** began working on a much smaller operating system that eventually became **Unix**.

The important question became:

> How can we write system software with the control of assembly, but with a higher-level language?

That is where C's family tree begins.

---

# 2. BCPL -> B -> C

The lineage is roughly:

```text
BCPL
  │
  ▼
  B
  │
  ▼
  C
  ├── K&R C (pre-standard)
  │
  └── C89/C90
      ├── C95 amendment
      ├── C99
      ├── C11
      ├── C17
      └── C23
```

**BCPL**
**BCPL**, created by Martin Richards, was an early systems programming language.

It was relatively minimal and did not have the rich type system that modern C has.

**B**
Ken Thompson developed **B**, heavily influenced by BCPL

B was used in the early development of Unix on the **PDP-7**. It was essentially a small systems language intended to replace assembly for portions of system programming. But **B** had a problem.

The newer **PDP-11** machine had hardware features that B did not express particularly well.
So the language needed something more sophisticated.

---

# 3. 1971–1972: C is born

**Dennis Richie** began developing a successor at B at Bell Labs.

The language initially went through an intermediate stage sometimes called **NEW B (NB)** Then it became the **C** around 1972. This wasn't merely a rename. C gained a real type system and features such as:

```c
int
char
arrays
pointers
struct
```

along with increasingly powerful expressions and operators.
The key idea was extremely important:

> Give the programmers higher-level abstraction while retaining a close relationship with machine hardware.

That's still one of C's defining characteristics.

---

# 4. The killer application: Unix

Here's the historically important part. Unix was initially written largely in **assembly**.
Then something rather revolutionary happened:
**Unix was rewritten in C.**
By 1973, much of the Unix kernel had been rewritten in C.
This demonstrated something extremely important.

```text
      C source
          │
  ┌───────┴───────────────┐
  ▼                       ▼
Compiler for A        Compiler for B
  │                       │
  ▼                       ▼
Machine code A        Machine code B
```

Instead of rewriting an entire operating system in assembly for every architecture, much of the source could remain the same.
This helped establish C as a _**systems programming language.**_

---

# 5. Why C became powerful

C occupies an unusual position. it is high-level enough to express:

```c
struct process {
    int pid;
    int state;
};
```

but low-level enough to manipulate memory:

```c
int value = 32;
int *p = &value;
```

and yeah perform explicit memory allocation:

```c
int *p = malloc(sizeof *p);
```

The language doesn't hide the machine completely. Its model gives you things such as: _objects, types, addresses, pointers, arrays, memory_, while still providing _functions, control flow, structured types, expressions, standard library_

That balance was one of the reasons C became so useful for operating systems, compilers, embedded systems, networking software, and other infrastructure.

---

# 6. 1978: K&R C

In 1978, **Brian Kernighan and Dennis Ritchie** published a book: _The C programming Language_. The first edition became the famous **K&R** book. At that time, there wasn't yet the Modern ISO C standard.

So the book became an enormously influential description of the language. This period is commonly called **K&R C**. The C language continued evolving while being implemented on different machines. Ritchie describes the period from roughly 1977 to 1979 as particularly important for demonstrating C and Unix portability.

---

# 7. The problem: C needed a standard

By the 1980s, C was no longer just a Bell Labs/Unix language. Different implementations existed, and programmers needed a common definition of what C actually meant.
So standardization began.

In **1983**, ANSI established the **X3J11 committee** to standardize C. Then the result was:

**C89**
ANSI published the first C standard in **1989**:

```text
ANSI X3.159-1989
```

This became known as **C89**
Then ISO adopted it in 1990:

```text
ISO/IEC 9899:1990
```

which is commonly called **C90** This distinction matters:

```text
C89 = ANSI standard
C90 = ISO adoption of essentially that standard
```

---

# 8. C99

In **1999**, ISO published:

```text
ISO/IEC 9899:1999
```

known as **C99**. It was a major evolution. Among other things, it introduced or standardized features such as:

```c
// declaration mixed with statements

for (int i = 0;i <10; ++i) {
    ...
}
```

and:

```c
// variable length arrays
int n = 10;
int a[n];
```

as well as:

- `long long`
- designated initializers
- compound literals
- `inline`
- `_Bool`
- `<stdint.h>`
- `stdbool.h`

improved floating-point facilities
C99 was a substantial modernization of the language.

---

# 9. C11

Then came:

```text
ISO/IEC 9899:2011
```

One of the **C11** most historically significant additions was standardized support for **concurrency and atomics**. For example:

```c
#include <stdatomic.h>

atomic_int counter;
```

C11 also introduced:

- `_Generic`
- `_Static_assert`
- thread support
- atomic operations
- improved Unicode support
- alignment facilities

This was important because C was no longer only being used for single-threaded systems.

---

# 10. C17

Next:

```text
ISO/IEC 9899:2018
```

This one commonly called **C17**. It was intentionally much less ambitious than C11. Think it approximately as: C11 -> Clarifications --> defect fixes ---> C17

It mostly cleaned up and corrected the existing standard rather than introducing a giant set of new language features.
The WG14 revision history lists C17 as ISO/IEC 9899:2018.

---

# 11. C23: the C i am exploring

And now we arrive at our actual target.
**C23** is:

```text
ISO/IEC 9899:2024
```

It was adopted/published in 2024. The ISO/IEC WG14 committee identifies C23 as the current C standard. C23 modernizes several areas of C. Some notable changes include:

```c
// bool is now directly available
bool ready = true;
```

instead of historically relying on:

```c
#include <stdbool.h>
```

C23 also introduces things such as:

- `nullptr`
- `constexpr`
- improved enumerations
- attributes
- `typeof`
- binary integer constants
- digit separators
- improved preprocessing facilities
- new library functionality
- removal of several obsolete features

And importantly, C23 is still recognizably C.
It didn't suddenly turn C into C++.

---

# 12. The entire Timeline

```text
1960s
  │
  ├── BCPL
  │
  ▼
1969
  │
  ├── B developed by Ken Thompson
  │
  ▼
1971
  │
  ├── New B / NB
  │
  ▼
1972
  │
  ├── C developed by Dennis Ritchie
  │
  ▼
1973
  │
  ├── Unix largely rewritten in C
  │
  ▼
1978
  │
  ├── K&R, "The C Programming Language"
  │
  ▼
1983
  │
  ├── ANSI X3J11 C standardization committee
  │
  ▼
1989
  │
  ├── C89
  │
  ▼
1990
  │
  ├── C90 / ISO 9899:1990
  │
  ▼
1995
  │
  ├── C95 amendment
  │
  ▼
1999
  │
  ├── C99
  │
  ▼
2011
  │
  ├── C11
  │
  ▼
2018
  │
  ├── C17
  │
  ▼
2024
  │
  └── C23 / ISO 9899:2024
```

---

# 13. The important historical lesson

The most useful thing to understand isn't memorizing dates.
It's **why C looks the way it does.**
C inherited a fundamental philosophy from its systems-programming origins:

```text
Hardware <------ close relationship ------> C
                                        │
                                        ▼
                           Higher-level abstraction
```

C tries to provide abstractions **without completely hiding the machine**.

And that's also why C can be both incredibly powerful and spectacularly unforgiving. The language gives you enough rope to build an OS, and enough rope to make a very memorable bug.
