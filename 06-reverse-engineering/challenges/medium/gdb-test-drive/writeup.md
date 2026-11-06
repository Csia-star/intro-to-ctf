# Writeup: GDB Test Drive

> 🟡 **Verification status: Source-verified.**
> The approach matches the official picoCTF walkthrough for this challenge (checked Nov 2026): it is a guided tour that has you load the binary in GDB and run it under control to reach the flag. The author did **not** re-download the challenge binary.
> The GDB session shown below is **real**, captured on a **tiny program we compiled ourselves** that prints `demoCTF{gdb_demo}`. On the real challenge you get `picoCTF{...}`.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Reverse Engineering → *GDB Test Drive*
**Goal:** use GDB to reach the flag without waiting out the delay. Not printed here.

## Step 1: Why a debugger

Running the binary normally prints the flag only after a long, deliberate delay. A **debugger** lets you pause, inspect, and jump around instead of waiting. GDB is the standard one on Linux.

## Step 2: Load it and look around

```
$ gdb ./gdbtest
(gdb) info functions
0x0000000000001149  main
```

- `info functions` lists the functions. You confirm there is a `main` (and often a print/flag function).

## Step 3: Break, run, inspect (real session on our test binary)

```
(gdb) break main
Breakpoint 1 at 0x1151
(gdb) run
Breakpoint 1, 0x0000555555555151 in main ()
(gdb) info registers rip
rip   0x555555555151   0x555555555151 <main+8>
```

- `break main` sets a pause point; `run` starts the program and stops there.
- `info registers rip` shows the instruction pointer — where execution currently is. This is the "look around" moment a debugger gives you.

## Step 4: Continue past the delay to the flag

```
(gdb) continue
checking...
demoCTF{gdb_demo}
[Inferior 1 exited normally]
```

- `continue` resumes execution. Because you are in control, you can skip the artificial wait the challenge built in (the official steps show exactly how for their binary — e.g. continuing, or moving the instruction pointer past the sleep).
- When execution reaches the print, the flag appears in GDB's output. On the real challenge that line is `picoCTF{...}` — submit it.

## GDB command recap

| Command | Does |
|---|---|
| `info functions` | List functions |
| `break main` | Pause at `main` |
| `run` | Start until a breakpoint |
| `info registers rip` | Show where execution is |
| `continue` | Resume |
| `x/s $rdi` | Examine memory as a string |

*بالدارجة: البرنامج كيعطّل بعمد. GDB كيخليك تتحكم: حط breakpoint، شغّل، وكمّل حتى يطبع الـ flag بلا ما تستنى.*

**Next:** [Hard challenge →](../../hard/ghidra-crackme/README.md)
