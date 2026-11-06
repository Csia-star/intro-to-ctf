# Writeup: So Meta

> 🟡 **Verification status: Source-verified.**
> The method matches the public solutions for this challenge (checked Nov 2026). The author did **not** re-download the challenge file.
> To avoid inventing output, the `strings` output below is **real**, taken from a **test image we built ourselves** (`meta.png`, with the flag placed in a metadata field on purpose, flag `demoCTF{...}`). The `exiftool` block shows the tool's **normal output format**, not a captured run. On the real file you will see `picoCTF{...}`.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Forensics → *So Meta*
**Goal:** read the flag from the image's metadata. Static flag, not printed here.

## Step 1: Understand the hint

- *So Meta* → **metadata**: data stored *about* the file (author, date, camera, comment), separate from the pixels you see.
- So we should not stare at the image. We should read its fields.

## Step 2: The quick way — `strings`

- **Why:** metadata text is readable text, so `strings` already catches it.
- **Command and real output (our test file):**
  ```
  $ strings meta.png | grep -i demo
  demoCTF{m3t4d4t4_c4n_hide_a_flag}
  ```
- **Meaning:** the flag is present as text. But `strings` does not tell us **which field** it lives in. For that, use the proper tool.

## Step 3: The clean way — `exiftool`

- **Why:** `exiftool` lists every metadata field as `Tag : Value`, so you see exactly where the flag is.
- **Command:**
  ```
  $ exiftool image.png
  ```
- **Output format (illustrative, not a real flag):**
  ```
  File Name     : image.png
  File Size     : ...
  Artist        : demoCTF{m3t4d4t4_c4n_hide_a_flag}
  ...
  ```
- **Meaning:** the flag sits in a field such as `Artist`, `Comment`, or `Copyright`. Narrow it down with:
  ```
  $ exiftool image.png | grep -i -E "artist|comment|copyright"
  ```
- **On the real challenge:** the printed value is the `picoCTF{...}` flag. Submit it as-is.

## Step 4: Install note

If `exiftool` is missing:
```
sudo apt install libimage-exiftool-perl
```
No install? Use an online EXIF viewer, or fall back to the `strings` method in Step 2.

## What you learned

| Idea | Lesson |
|---|---|
| Metadata | Files carry hidden fields beside their content |
| `exiftool` | Reads those fields cleanly and names them |
| `strings` vs `exiftool` | `strings` finds the text; `exiftool` tells you where it is |

*بالدارجة: الـ flag كان مخبي فـ واحد الحقل ديال الـ metadata (بحال Artist). `exiftool` كيورّيك كل الحقول بأسمائها.*

**Next:** [Hard challenge →](../../hard/pcap-wireshark/README.md)
