# Writeup: MacroHard WeakEdge

> 🟡 **Verification status: Source-verified.**
> The approach matches public solutions for this picoCTF challenge (checked Nov 2026): the Office file is a ZIP, a hidden internal file holds a Base64 blob, and decoding it gives the flag. The author did **not** re-download the challenge file.
> To avoid inventing output, the commands below are **real**, run on a tiny Office-style ZIP we built ourselves containing `demoCTF{office_is_a_zip}` (Base64) in a hidden internal file. On the real challenge you get `picoCTF{...}`.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Forensics → *MacroHard WeakEdge*
**Goal:** find the flag hidden inside the document. Static flag, not printed here.

## Step 1: Realise the file is a ZIP

- Office files (`.docx`, `.pptx`, `.pptm`, `.xlsx`) are ZIP archives of XML and media.
- **List the contents (real output on our demo file):**
  ```
  $ unzip -l demo.pptx
    Length      Date    Time    Name
  ---------  ---------- -----   ----
         17  ...                ppt/presentation.xml
          8  ...                docProps/core.xml
         32  ...                ppt/slideMasters/hidden
  ```
- **Meaning:** most entries are normal Office parts. One (`ppt/slideMasters/hidden`) does not belong — that is the weak spot.

## Step 2: Extract and hunt for the odd file

- **Extract:** `unzip demo.pptx -d ex/`
- **Search the whole tree for the flag prefix or anything unusual:**
  ```
  $ grep -rl "ZGVtb" ex
  ex/ppt/slideMasters/hidden
  ```
- **Why `grep -r`:** it scans every extracted file at once, so a planted file reveals itself even if you did not spot it in the listing.
- On the real challenge the odd file may look like meaningless **whitespace** or a long text blob rather than valid XML.

## Step 3: Decode the hidden content

- The blob is **Base64**. Decode it:
  ```
  $ cat ex/ppt/slideMasters/hidden | base64 -d
  demoCTF{office_is_a_zip}
  ```
- **On the real challenge:** the decoded text is the `picoCTF{...}` flag. If the file is whitespace stego, first convert the whitespace to its encoded form (e.g. with CyberChef's whitespace/Base64 recipes), then decode.

## Step 4: Confirm and submit

The decoded string is a clean `picoCTF{...}`. Submit it as-is.

## What you learned

| Idea | Lesson |
|---|---|
| Office = ZIP | `unzip` opens any `.docx`/`.pptx`/`.xlsx` |
| `grep -r` | Finds a planted file inside a whole extracted tree |
| Base64 | A common final layer; decode to reveal the flag |

*بالدارجة: ملفات Office هي ZIP. فكيناها، لقينا ملف ماشي من بلاصتو، وكان Base64 — فكيناه وطلع الـ flag.*

**Next:** continue to [Reverse Engineering](../../../../06-reverse-engineering/README.md), where you read a program to understand what it does.
