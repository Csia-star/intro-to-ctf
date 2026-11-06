# St3g0

![Medium](https://img.shields.io/badge/Medium-ED8936) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Stego](https://img.shields.io/badge/category-stego-00D4FF)

> **STOP!** Try the challenge yourself first. Use the [hints](hints.md) one by one, then the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Forensics](https://play.picoctf.org/practice?category=4), search *St3g0* |
| **Access** | Free picoCTF account (behind a login) |
| **picoCTF points** | 250 (their scale) |
| **Given file** | A PNG image that looks normal and opens fine |
| **Goal** | Extract the flag hidden in the pixels |
| **Flag?** | Static, format `picoCTF{...}` (watch for a trailing marker). Not printed here |
| **Estimated time** | 20–40 minutes |
| **Tools** | `zsteg` (or Aperi'Solve in the browser) |

## Concepts required

Carrier vs payload, how images store pixels, **LSB**, **bit planes**, visual tools.
See [concepts 1, 3, 5, 6](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [LSB steganography explained](https://www.youtube.com/results?search_query=LSB+steganography+explained)
- [zsteg tutorial](https://www.youtube.com/results?search_query=zsteg+stego+tutorial)

## Your mission

The image opens normally and shows nothing special. The forensics basics come up empty. The data is hidden in the **least significant bits** of the pixels. Pull it out.

## Legal reminder

picoCTF practice file. Analyse it; never run it.
