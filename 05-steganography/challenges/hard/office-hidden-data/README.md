# MacroHard WeakEdge

![Hard](https://img.shields.io/badge/Hard-E53E3E) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Stego](https://img.shields.io/badge/category-stego-00D4FF)

> **STOP!** Try the challenge yourself first. Use the [hints](hints.md) one by one, then the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Forensics](https://play.picoctf.org/practice?category=4), search *MacroHard WeakEdge* |
| **Access** | Free picoCTF account (behind a login) |
| **picoCTF points** | 200 (their scale) |
| **Given file** | A PowerPoint-style file (`.pptm` / Office document) |
| **Goal** | Find the flag hidden inside the document |
| **Flag?** | Static, format `picoCTF{...}`, stored **encoded**. Not printed here |
| **Estimated time** | 30–50 minutes |
| **Tools** | `unzip`, `grep`, a Base64 decoder (CyberChef) |

## Concepts required

Carrier vs payload, run the forensics basics, **documents are ZIP archives**, inspecting archive contents, decoding Base64.
See [concepts 1, 2, 9](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [A .docx/.pptx is a ZIP file](https://www.youtube.com/results?search_query=docx+pptx+is+a+zip+file+explained)
- [Find hidden data in Office files CTF](https://www.youtube.com/results?search_query=office+document+hidden+data+ctf)

## Your mission

The flag is not on any slide. Office files are really ZIP archives of XML and media. The secret hides among the internal files (look for something that does not belong, such as odd whitespace). Extract and decode it.

## Legal reminder

picoCTF practice file. Unzip and read it; never enable macros or run it.
