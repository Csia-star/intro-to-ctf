# Writeup: Classic Crackme 0x100

> 🟡 **Verification status: Source-verified.**
> The approach matches public Ghidra-based solutions for this picoCTF challenge (checked Nov 2026): the password is checked in native code and must be reconstructed from the decompiled logic. The author did **not** re-download the challenge binary.
> To avoid inventing a decompiler screenshot, the pseudocode below mirrors what Ghidra shows, and the reconstruction was **really run** against a crackme we compiled ourselves (password `d3m0_k3y`). On the real challenge you recover the actual `picoCTF{...}`.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Reverse Engineering → *Classic Crackme 0x100*
**Goal:** recover the accepted password. Not printed here.

## Step 1: Confirm `strings` is not enough

```
$ file crackme
crackme: ELF 64-bit LSB pie executable, x86-64, ...
$ strings crackme | grep -i pico
(nothing)
```

- Native ELF, and the flag is **not** sitting in the strings. So the password is built or compared in code → decompile.

## Step 2: Decompile in Ghidra and find the check

Import the binary, analyse with defaults, open `main`. Ghidra shows C-like pseudocode. The interesting part looks like this (equivalent to what the decompiler reconstructs):

```c
// expected password is compared character by character
char exp[9];
exp[0] = 0x64;  exp[1] = 0x33;  exp[2] = 0x6d;  exp[3] = 0x30;
exp[4] = 0x5f;  exp[5] = 0x6b;  exp[6] = 0x33;  exp[7] = 0x79;
exp[8] = 0;
if (strcmp(input, exp) == 0) { /* correct */ }
```

- The key insight: each `exp[i]` is an **ASCII code** in hex. The check is `strcmp(input, exp)`.

## Step 3: Reconstruct the password from the codes

Convert each hex code to its character (real run):

```
$ python3 -c "print(bytes([0x64,0x33,0x6d,0x30,0x5f,0x6b,0x33,0x79]).decode())"
d3m0_k3y
```

| Hex | 0x64 | 0x33 | 0x6d | 0x30 | 0x5f | 0x6b | 0x33 | 0x79 |
|---|---|---|---|---|---|---|---|---|
| Char | d | 3 | m | 0 | _ | k | 3 | y |

## Step 4: Verify against the binary

```
$ echo "d3m0_k3y" | ./crackme
Password: Correct! demoCTF{d3m0_k3y}
```

- The reconstructed password is accepted. On the real challenge, running it with the recovered password prints the `picoCTF{...}` flag (or the password itself is wrapped into the flag). Submit what the real binary gives.

## If the check is arithmetic, not a plain table

Some crackmes do `input[i] + 3 == something`, or XOR each byte. The method is the same: read the operation per character, then **invert** it to compute the needed input. GDB can confirm — break at the comparison and inspect the expected value with `x/s`.

## What you learned

| Idea | Lesson |
|---|---|
| `strings` not enough | Native checks hide the secret in logic |
| Ghidra | Turns machine code into readable pseudocode |
| ASCII codes | Hex constants in the check are characters |
| Reconstruct & verify | Build the input, then prove it on the binary |

*بالدارجة: الباسورد كان متقارن حرف بحرف بأكواد ASCII. قرينا الكود فـ Ghidra، حوّلنا كل كود لحرف، وجمعناهم، ومن بعد جرّبنا البرنامج وتأكدنا.*

**Next:** continue to [Binary Exploitation](../../../../07-binary-exploitation/README.md).
