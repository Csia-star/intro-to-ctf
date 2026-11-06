# Writeup: St3g0

> 🟡 **Verification status: Source-verified.**
> The approach matches public solutions for this picoCTF challenge (checked Nov 2026): the flag is hidden with LSB steganography and `zsteg` recovers it. The author did **not** re-download the challenge file.
> To avoid inventing tool output, the LSB demonstration below is **real** — we hid `demoCTF{lsb_demo}` in the red channel of our own PNG and recovered it with Python. The `zsteg` block shows the tool's **usage and output shape**, not a captured run. On the real image you get `picoCTF{...}`.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Forensics → *St3g0*
**Goal:** extract the flag from the pixels. Static flag, not printed here.

## Step 1: Rule out the easy hiding places

- Run the basics: `file`, `strings img.png | grep -i pico`, `exiftool img.png`, `binwalk img.png`.
- They find nothing. That is the signal: the data is **inside the pixels**, not appended or in metadata.

## Step 2: Understand LSB (why the eye fails)

Each pixel colour is a byte like `11111111`. The **last bit** barely changes the colour, so flipping it is invisible. Hide one message bit per colour value, and the picture looks identical.

**Real demonstration (our own image, not the challenge):**

```
$ python3 hide.py     # set red-channel LSBs to the bits of "demoCTF{lsb_demo}"
hid 17 bytes in LSB of red

$ python3 recover.py  # read back the red-channel LSBs, regroup into bytes
recovered: b'demoCTF{lsb_demo}\xff\xff\xff'
```

The message comes back exactly (the `\xff` tail is just leftover white pixels). This proves the mechanism: **collect last bits → group into bytes → read text.**

## Step 3: Let `zsteg` do it for you

You do not write that script in a CTF — `zsteg` tries every bit-plane/channel combination automatically.

- **Command:**
  ```
  $ zsteg -a img.png
  ```
- **Output shape:** one line per combination, like
  ```
  b1,r,lsb,xy   .. text: "some text here"
  b1,rgb,lsb,xy .. text: "...picoCTF{...}..."
  ```
  The left part names the bit/channel/order; the right part is what was decoded there. Scan for the line containing `picoCTF`.
- **No install?** Upload the image to **[Aperi'Solve](https://aperisolve.fr)** — it runs `zsteg` for you and highlights the result.

## Step 4: Clean up the flag

The decoded text may include an extra marker right after the closing brace (for this challenge, a short tag). The flag is only the `picoCTF{...}` part, up to and including the `}`. Submit exactly that.

## What you learned

| Idea | Lesson |
|---|---|
| LSB | The last bit of each colour hides data invisibly |
| Bit planes | `zsteg`/Aperi'Solve scan them automatically |
| Read carefully | Trim any trailing marker that is not part of the flag |

*بالدارجة: السر كان فالبيت الأخير ديال الألوان. العين ما كتشوفوش، ولكن `zsteg` كيقراه. عيّط غير على جزء `picoCTF{...}`.*

**Next:** [Hard challenge →](../../hard/office-hidden-data/README.md)
