# Reverse Engineering Tools and Environment

| Tool | Required? | Purpose | Installation |
|---|---|---|---|
| `file` | ✅ Required | Identify the binary type | Preinstalled on Linux |
| `strings` | ✅ Required | Readable text inside the binary | `sudo apt install binutils` |
| **GDB** | ✅ Required (Medium) | Run and inspect a program step by step | `sudo apt install gdb` |
| **Ghidra** | ✅ Required (Hard) | Decompile native code to C-like pseudocode | <https://ghidra-sre.org> (needs Java) |
| **Java JDK** | ✅ (for Ghidra & Java challenges) | Runs Ghidra; `javap`/decompilers read `.class` | `sudo apt install default-jdk` |
| **pwndbg** | Recommended | Makes GDB output readable (registers, stack) | <https://github.com/pwndbg/pwndbg> |
| **Decompiler Explorer** | Optional | Decompile in the browser, no install | <https://dogbolt.org> |
| `objdump` | Optional | Disassemble without a GUI | Comes with `binutils` |

**Install the core set (Ubuntu/Debian/Kali):**

```bash
sudo apt update && sudo apt install -y binutils gdb default-jdk
# Ghidra: download the release zip from ghidra-sre.org, unzip, run ./ghidraRun
```

## Do I need Kali?

**No.** A plain **Ubuntu VM** is ideal. Kali only bundles these tools. You *do* want a **VM** here, because you are running unknown programs — take a snapshot first.

*بالدارجة: ما خاصكش Kali، ولكن خدم فـ VM حيت غادي تشغّل برامج مجهولة. دير snapshot قبل.*

## Is the browser enough?

| Challenge | Browser only? |
|---|---|
| Easy: Safe Opener (Java) | Yes — a Java decompiler site, or `dogbolt.org`, reads the `.class` |
| Medium: GDB Test Drive | ❌ No — you need GDB locally |
| Hard: Classic Crackme | Mostly — `dogbolt.org` decompiles it; local Ghidra is more powerful |

## Useful commands

```bash
file ./challenge                 # ELF? Java class? script?
strings ./challenge | less       # readable text; try grep -i pico too
# --- GDB basics ---
gdb ./challenge                  # start the debugger
(gdb) info functions             # list functions; look for main, win, check...
(gdb) break main                 # pause at main
(gdb) run                        # start running until the breakpoint
(gdb) continue                   # keep going
(gdb) info registers             # read CPU registers
(gdb) x/s $rdi                   # examine memory as a string (e.g. an argument)
(gdb) disassemble main           # show the assembly of main
# --- Java ---
javap -c -p Challenge.class      # show the bytecode / method structure
```

## Safety

- **Always run RE challenges inside a VM** with a snapshot. They are unknown executables.
- Reading/decompiling (`file`, `strings`, Ghidra) is safe. **Executing** (even under GDB) should be done in the VM.

*بالدارجة: البرامج ديال RE شغّلها غير فـ VM. القراءة بـ Ghidra بلا تشغيل هي أأمن.*

## Ghidra quick start (6 steps)

1. Launch with `./ghidraRun`. Create a new project.
2. **File → Import File**, choose the binary.
3. Double-click it; when asked to analyse, click **Yes** (defaults are fine).
4. In the **Symbol Tree**, open **Functions** and double-click `main`.
5. Read the **Decompile** window on the right (C-like pseudocode).
6. Find the comparison against your input; the expected value (or how to build it) is right there.
