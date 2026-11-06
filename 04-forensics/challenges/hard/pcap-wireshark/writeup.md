# Writeup: Wireshark doo dooo do doo

> 🟡 **Verification status: Source-verified.**
> The steps match multiple public solutions for this picoCTF 2021 challenge (checked Nov 2026): the flag is in a TCP stream and it is ROT13-encoded. The author did **not** re-download the capture.
> The ROT13 snippet below is **real** (run with Python) but uses only the public flag **prefix**, not the flag body, so nothing is spoiled.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Forensics → *Wireshark doo dooo do doo*
**Goal:** recover the flag from `shark1.pcapng`. Static flag, not printed here.

## Step 1: Open and survey the capture

- **Action:** open `shark1.pcapng` in Wireshark.
- **Then:** **Statistics → Protocol Hierarchy**. This shows which protocols are present and how much of each.
- **Why:** a capture can hold thousands of packets. The hierarchy tells you where to look. Seeing **HTTP** or **"Line based text data"** is a strong sign: text travels there.

## Step 2: Filter to the readable traffic

- **Action:** in the filter bar type `http` and press Enter (or `tcp` if you prefer).
- **Why:** flags are text. HTTP bodies are often plaintext, unlike the encrypted noise around them.

## Step 3: Follow the stream

- **Action:** right-click a packet in that traffic → **Follow → TCP Stream**. Use the arrows at the bottom right to move between streams.
- **What you find:** one stream (publicly documented as **stream 5**) ends with a line containing a flag-shaped string in `{ }`. You can jump straight to it with the filter `tcp.stream eq 5`.
- **Why it works:** "Follow TCP Stream" reassembles the scattered packets of one conversation into one readable block.

## Step 4: Notice it is encoded, then decode

- **The clue:** the string starts `cvpbPGS{...}`, not `picoCTF{...}`. It is scrambled.
- **The test (real, run with Python):**
  ```
  $ python3 -c "import codecs; print(codecs.encode('cvpbPGS','rot13'))"
  picoCTF
  ```
- **Meaning:** `cvpbPGS` is `picoCTF` shifted by 13 letters — classic **ROT13**. So the whole string is ROT13.
- **Decode it:** paste the full `cvpbPGS{...}` string into [CyberChef](https://gchq.github.io/CyberChef/) with the *ROT13* operation, or <https://rot13.com>. The result is the real `picoCTF{...}` flag. Submit it.

## Why this is a good "combining" challenge

| Skill used | From |
|---|---|
| Open and read a capture | This category (Forensics) |
| Follow a TCP stream | Wireshark |
| Recognise and decode ROT13 | [Cryptography](../../../../03-cryptography/README.md) |

*بالدارجة: لقينا النص فـ TCP stream، ولكن ماشي واضح. بدا بـ `cvpbPGS` اللي هي `picoCTF` بـ ROT13، إذن فكينا الكل بـ ROT13.*

## What you learned

- How to survey a capture with Protocol Hierarchy.
- How to isolate one conversation with Follow TCP Stream.
- How to spot an encoded flag by its wrong-looking prefix.

**Next:** continue to [Steganography](../../../../05-steganography/README.md), where hidden data lives inside the pixels and sound themselves.
