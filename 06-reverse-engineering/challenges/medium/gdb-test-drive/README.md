# GDB Test Drive

![Medium](https://img.shields.io/badge/Medium-ED8936) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Reverse](https://img.shields.io/badge/category-reverse-00D4FF)

> **STOP!** Try the challenge yourself first. Use the [hints](hints.md) one by one, then the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Reverse Engineering](https://play.picoctf.org/practice?category=3), search *GDB Test Drive* |
| **Access** | Free picoCTF account (behind a login) |
| **picoCTF points** | 20 (their scale) |
| **Given file** | A Linux ELF binary that only prints the flag after a long delay |
| **Goal** | Use GDB to skip the delay and let the program print the flag |
| **Flag?** | Static, format `picoCTF{...}`. Not printed here |
| **Estimated time** | 15–30 minutes |
| **Tools** | GDB |

## Concepts required

`file`/`strings`, finding the check, **what a debugger is**, **GDB basics**, a gentle look at registers.
See [concepts 1–4, 6–8](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [What is a debugger](https://www.youtube.com/results?search_query=what+is+a+debugger+explained)
- [GDB tutorial for beginners](https://www.youtube.com/results?search_query=gdb+tutorial+for+beginners)

## Your mission

The binary is written to stall (a long sleep) before printing the flag. This challenge teaches you to **drive GDB**: load the program, set a breakpoint, run, and continue past the delay so the flag appears.

## Legal reminder

picoCTF practice binary. Run it inside your VM.
