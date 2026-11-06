# So Meta

![Medium](https://img.shields.io/badge/Medium-ED8936) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Forensics](https://img.shields.io/badge/category-forensics-00D4FF)

> **STOP!** Don't open the writeup immediately. Try the challenge yourself first. If you're stuck, use the [hints](hints.md) one by one before reading the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Forensics](https://play.picoctf.org/practice?category=4), search *So Meta* |
| **Access** | Free picoCTF account (challenges are behind a login) |
| **picoCTF points** | 150 (their scale) |
| **Given file** | An image file |
| **Goal** | Find the flag in the picture |
| **Flag?** | Static, format `picoCTF{...}`. Not shown here |
| **Estimated time** | 5–15 minutes |
| **Tools** | `exiftool` (or `strings`) |

## Concepts required

A file is bytes, `strings`, and especially **metadata / EXIF**.
See [concepts 1–3 and 6](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [exiftool metadata tutorial](https://www.youtube.com/results?search_query=exiftool+metadata+tutorial)
- [What is EXIF metadata](https://www.youtube.com/results?search_query=what+is+exif+metadata+explained)

## Your mission

The title is the hint: *So Meta* → **metadata**. The flag is not in the pixels; it is written in one of the file's metadata fields. Find which field.

## Legal reminder

picoCTF practice file. Analyse it; never run it.
