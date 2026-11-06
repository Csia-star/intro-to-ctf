# Writeup: Glory of the Garden

> 🟡 **Verification status: Source-verified.**
> The method matches picoCTF's own hint and public solutions (checked Nov 2026). The author did **not** re-download the challenge file.
> The terminal outputs below are **real**, but taken from a **test file we built ourselves** (`mygarden.png`, with `demoCTF{...}` appended on purpose) so nothing is invented and no real flag is spoiled. On the real `garden.jpg` you will see `picoCTF{...}` instead.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Forensics → *Glory of the Garden*
**Goal:** find the flag hidden in `garden.jpg`. Static flag, not printed here.

## Step 1: Check the file size

- **What we look for:** a mismatch between what we see and how big the file is.
- **Why:** a plain garden photo should not be unusually large. Extra bytes are a clue.
- **Action:** `ls -l garden.jpg` and compare with what a simple image needs.

## Step 2: Confirm the real type

- **Why:** before anything, make sure the extension is honest.
- **Command and real output (test file):**
  ```
  $ file mygarden.png
  mygarden.png: PNG image data, 8 x 8, 8-bit/color RGB, non-interlaced
  ```
- **Meaning:** it really is an image. So the flag is extra data, not a disguised file type.

## Step 3: Read the text inside the bytes

- **Why:** the picoCTF hint points at a hex editor, i.e. the raw bytes. `strings` reads the same bytes but shows only printable text, which is faster.
- **Command and real output (test file):**
  ```
  $ strings mygarden.png | tail -3
  IDATx
  IEND
  Here is a flag "demoCTF{this_is_my_own_test_file}"
  ```
- **Meaning:** the flag text sits **after** the image data (`IEND` is the end of a PNG). The viewer stops at `IEND`, so your eyes never see it, but the bytes are still there.

## Step 4: Filter straight to the flag

- **Why:** on a big file the output is long. You already know the prefix.
- **Command and real output (test file):**
  ```
  $ strings mygarden.png | grep -i demo
  Here is a flag "demoCTF{this_is_my_own_test_file}"
  ```
- **On the real challenge:** use `strings garden.jpg | grep -i pico`. Submit the `picoCTF{...}` it prints.

## Hex editor alternative

Open the file in `hexed.it` or run `xxd garden.jpg | tail`. The flag appears as readable ASCII in the right-hand column of the last lines.

## What you learned

| Idea | Lesson |
|---|---|
| A file is bytes | The picture is only part of the file |
| Appended data | Text after `IEND` still travels with the file |
| `strings` + `grep` | Your first reflex on any file challenge |

*بالدارجة: الـ flag كان مكتوب فـ آخر الملف، من بعد نهاية التصويرة. العين ما كتشوفوش، ولكن `strings` كيبيّنو.*

**Next:** [Medium challenge →](../../medium/metadata-exiftool/README.md)
