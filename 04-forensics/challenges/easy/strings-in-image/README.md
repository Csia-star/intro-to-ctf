# Glory of the Garden

![Easy](https://img.shields.io/badge/Easy-48BB78) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Forensics](https://img.shields.io/badge/category-forensics-00D4FF)

> **STOP!** Don't open the writeup immediately. Try the challenge yourself first. If you're stuck, use the [hints](hints.md) one by one before reading the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول. إلا تعطلتي، استعمل الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Forensics](https://play.picoctf.org/practice?category=4), search *Glory of the Garden* |
| **Access** | Free picoCTF account. Challenges are behind a login, so there is no public per-challenge URL |
| **picoCTF points** | 50 (their scale; see note below) |
| **Given file** | `garden.jpg` — a photo of a garden |
| **Goal** | Find the flag hidden in the file |
| **Flag?** | Static flag, format `picoCTF{...}`. Not shown in this repo |
| **Estimated time** | 5–15 minutes |
| **Tools** | `strings` (or a hex editor) |

> **Why "Easy" when picoCTF says 50 points?** Our levels describe *how much you need to know*, not picoCTF's score. This one needs a single command.

## Concepts required

A file is bytes, magic bytes, `strings`, appended data, hex view.
See [concepts 1–5](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [How files are stored as bytes](https://www.youtube.com/results?search_query=how+files+are+stored+bytes+explained)
- [The Linux `strings` command](https://www.youtube.com/results?search_query=linux+strings+command+tutorial)
- [Hex editor basics](https://www.youtube.com/results?search_query=hex+editor+basics+tutorial)

## Your mission

The challenge says the garden "contains more than it seems". Opening the image shows nothing special. The flag is **inside the file**, not inside the picture.

Download the file, then investigate the bytes.

## Legal reminder

This file comes from picoCTF and is made for practice. Analyse it; never run it.
