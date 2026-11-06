# Writeup: tunn3l v1s10n

> 🟡 **Verification status: Source-verified.**
> The approach matches the public solutions for this picoCTF challenge (checked Nov 2026): the BMP header was corrupted, and fixing the magic bytes plus the height field reveals the flag drawn in the image. The author did **not** re-download the challenge file.
> The BMP facts below (magic bytes `42 4D`, height field at offset 22) are **real**, confirmed on a BMP we generated ourselves. No flag is shown.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Forensics → *tunn3l v1s10n*
**Goal:** repair the file so the hidden image (with the flag) displays. Static flag, not printed here.

## Step 1: Ask what type it really is

- **Command:** `file tunn3l_v1s10n`
- **Why:** the file has no helpful extension and will not open. `file` reads the first bytes to guess the type.
- **What you learn:** it is a **BMP** image, but something about the header is off, so viewers refuse it or show garbage.

## Step 2: Learn the BMP header you are fixing

Real facts (confirmed on a BMP we made):

- A valid BMP **starts with the two bytes `42 4D`** = the ASCII letters `BM`.
- The **image height** is a signed 32-bit little-endian integer at **offset 22** (0x16) in the file; the width is at offset 18 (0x12).

```
$ python3 -c "d=open('pic.bmp','rb').read(); print(d[:2], d[22:26])"
b'BM'  b'\x02\x00\x00\x00'      # magic 'BM', height = 2
```

## Step 3: Repair the header on a copy

- **Make a copy first:** `cp tunn3l_v1s10n work.bmp` — never edit the original.
- **Open `work.bmp` in a hex editor** (`hexed.it` or `ghex`).
- **Fix the magic bytes:** if the first two bytes are not `42 4D`, set them to `42 4D`.
- **Save and open the image.** If it displays but the flag looks cut off, the **height** field is wrong (made too small to hide the bottom of the picture).

## Step 4: Fix the height so the flag shows

- **Why:** the viewer only draws as many rows as the height field claims. A too-small height hides the part of the image where the flag is written.
- **Action:** at offset 22, increase the height value (e.g. make it match or exceed the width, or a larger round number). Save, reopen.
- **Result:** the full picture renders, and the `picoCTF{...}` flag is drawn inside it. Read it off the image and submit.

## What you learned

| Idea | Lesson |
|---|---|
| Magic bytes | `42 4D` = `BM` marks a BMP; wrong magic = unopenable |
| Header fields | Width/height tell the viewer how much to draw |
| Hiding by shrinking | A small height field crops the secret out of view |
| Work on a copy | Hex editing is destructive if you slip |

*بالدارجة: الـ header ديال التصويرة كان مكسور بعمد. صلّحنا `42 4D` وزدنا الطول باش تبان التصويرة كاملة والـ flag معاها.*

**Next:** [Medium challenge →](../../medium/lsb-zsteg-st3g0/README.md)
