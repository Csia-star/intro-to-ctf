# Safe Opener

![Easy](https://img.shields.io/badge/Easy-48BB78) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Reverse](https://img.shields.io/badge/category-reverse-00D4FF)

> **STOP!** Try the challenge yourself first. Use the [hints](hints.md) one by one, then the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Reverse Engineering](https://play.picoctf.org/practice?category=3), search *Safe Opener* |
| **Access** | Free picoCTF account (behind a login) |
| **picoCTF points** | 100 (their scale) |
| **Given file** | A Java source/class file that checks a password |
| **Goal** | Find the password the program accepts |
| **Flag?** | Some versions use the password itself; format `picoCTF{...}`. Not printed here |
| **Estimated time** | 15–30 minutes |
| **Tools** | A text editor (source) or a Java decompiler (`.class`) |

## Concepts required

Source vs compiled, `file`, `strings`, **finding "the check"**, reading managed code.
See [concepts 1–5](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [Decompile a Java class file](https://www.youtube.com/results?search_query=decompile+java+class+file)
- [Find a password check in code](https://www.youtube.com/results?search_query=reverse+engineering+password+check+explained)

## Your mission

The program compares the password you type against a value it builds in the code. Read the code, find that comparison, and recover the expected value.

## Legal reminder

picoCTF practice file. Read/decompile it; run it only in your VM if you wish.
