# TinyVM v1.1 — FINAL FINAL FINAL (now with flair) 🔥


A stupidly small, ridiculously fast virtual machine that runs `.tvm` bytecode with typewriter-style animated output. Single header-free C++ file, zero dependencies, pure chaos.

## Features
- 64-bit registers (r0–r7)
- 64 KB flat memory
- 16 opcodes (only the good ones)
- Animated PRINTC with 30 ms per char (feels like 1987)
- Fancy ASCII banner + auto-clear
- If no `.tvm` files exist → instantly creates `hello.tvm`
- Colorful HALT / RET / error messages

## Supported Opcodes
| Code   | Mnemonic   | Description                     |
|--------|------------|---------------------------------|
| 0x00   | HALT       | Stop execution                  |
| 0x01   | NOP        | Do nothing                      |
| 0x10   | MOV R, i64 | Load 64-bit immediate           |
| 0x11   | MOV R, i32| Load 32-bit immediate           |
| 0x23   | LOAD64     | r[d] = mem[r[a]] (64-bit)       |
| 0x2B   | STORE64    | mem[r[a]] = r[d] (64-bit)       |
| 0x30–33| ADD/SUB/MUL/DIV | r[d] = r[a] ±×÷ r[b]        |
| 0x40   | JMP        | Relative jump                   |
| 0x41   | JZ         | Jump if r[reg] == 0              |
| 0x42   | CALL       | (not implemented yet)           |
| 0x43   | RET        | Return / exit                   |
| 0xF0   | PRINT      | Print r0 as signed decimal      |
| 0xF1   | PRINTC     | Print r0 as char (animated)     |

## Build & Run
```bash
g++ -std=c++17 -O3 -s tinyvm.cpp -o tinyvm
./tinyvm                  # interactive picker or auto hello.tvm
./tinyvm fib.tvm          # run any .tvm file directly
