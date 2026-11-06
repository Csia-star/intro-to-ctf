# Classic Crackme 0x100

![Hard](https://img.shields.io/badge/Hard-E53E3E) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Reverse](https://img.shields.io/badge/category-reverse-00D4FF)

> **STOP!** Try the challenge yourself first. Use the [hints](hints.md) one by one, then the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Reverse Engineering](https://play.picoctf.org/practice?category=3), search *Classic Crackme 0x100* |
| **Access** | Free picoCTF account (behind a login) |
| **picoCTF points** | 110 (their scale) |
| **Given file** | A native Linux ELF that asks for a password |
| **Goal** | Recover the password the binary accepts |
| **Flag?** | Static, format `picoCTF{...}`. Not printed here |
| **Estimated time** | 45–90 minutes |
| **Tools** | Ghidra (or dogbolt.org), optionally GDB |

## Concepts required

`file`/`strings`, finding the check, assembly & registers, **Ghidra decompiling**, **reconstructing input**.
See [concepts 1–4, 8–10](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [Ghidra tutorial for beginners](https://www.youtube.com/results?search_query=ghidra+tutorial+for+beginners)
- [Solve a crackme with Ghidra](https://www.youtube.com/results?search_query=solve+crackme+ghidra+reconstruct+password)

## Your mission

`strings` will not just hand you the password this time — it is **checked character by character** in native code. Decompile the binary in Ghidra, read the comparison logic, and reconstruct the exact password it wants.

## Legal reminder

picoCTF practice binary. Analyse in Ghidra; run only in your VM.
