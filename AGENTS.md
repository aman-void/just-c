# AGENTS.md

## Standard

- Compile everything with C23: `gcc -std=c23 -Wall -Wextra -g`
- Core reference is Kochan _Programming in C_ 4th ed (2014), which targets C11 (ISO/IEC 9899:2011). Adapt book examples to C23 when they differ.

## Layout

- Flat per-topic dirs, no `src/`, no `Makefile`:
  `NN-topic/main.c` + `NN-topic/README.md` (e.g. `01-hello-c/main.c`)
- Extra `.c` files live directly in the topic dir. Compile together:
  `gcc -std=c23 -Wall -Wextra -g <topic>/*.c -o /tmp/opencode/main`

## Rules

- Never delete or rewrite `01-hello-c/README.md` (preserved C-evolution notes).
- Each topic `README.md` holds that topic's notes and C23 observations.
- Never commit binaries/objects (`main`, `*.o`, `*.i`, `*.s` are gitignored). Build to `/tmp/opencode/` and run from there.
- Book PDF is local-only (`*.pdf` gitignored).

## Verify

- `gcc -std=c23 -Wall -Wextra -g <topic>/main.c -o /tmp/opencode/main && /tmp/opencode/main`
- Zero warnings is required; fix code, don't drop flags.
