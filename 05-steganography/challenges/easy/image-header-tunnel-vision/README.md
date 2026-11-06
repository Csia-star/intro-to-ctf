# tunn3l v1s10n

![Easy](https://img.shields.io/badge/Easy-48BB78) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Stego](https://img.shields.io/badge/category-stego-00D4FF)

> **STOP!** Don't open the writeup immediately. Try the challenge yourself first. Use the [hints](hints.md) one by one, then the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Forensics](https://play.picoctf.org/practice?category=4), search *tunn3l v1s10n* |
| **Access** | Free picoCTF account (behind a login) |
| **picoCTF points** | 150 (their scale) |
| **Given file** | A file with no useful extension that will not open as an image at first |
| **Goal** | Repair the file so the hidden picture (with the flag) displays |
| **Flag?** | Static, format `picoCTF{...}`, shown **inside the repaired image**. Not printed here |
| **Estimated time** | 20–40 minutes |
| **Tools** | A hex editor (`hexed.it`, `ghex`), `file`, `xxd` |

## Concepts required

Carrier vs payload, how images store pixels, **file headers control display**, repairing a header.
See [concepts 1, 3, 4](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [BMP file header explained](https://www.youtube.com/results?search_query=bmp+file+header+explained)
- [Hex editor basics](https://www.youtube.com/results?search_query=hex+editor+basics+tutorial)

## Your mission

The file will not open properly: its **header** was damaged on purpose. Fix the header bytes so the image renders. The flag is drawn inside the picture.

## Legal reminder

picoCTF practice file. Edit a **copy**; never run the file.
