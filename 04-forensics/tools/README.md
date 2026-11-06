# Forensics Tools and Environment

| Tool | Required? | Purpose | Installation |
|---|---|---|---|
| `file` | ✅ Required | Real file type from magic bytes | Preinstalled on Linux |
| `strings` | ✅ Required | Readable text inside a binary | `sudo apt install binutils` |
| `grep` | ✅ Required | Filter the output of `strings` | Preinstalled |
| `exiftool` | ✅ Required (Medium) | Read metadata fields | `sudo apt install libimage-exiftool-perl` |
| **Wireshark** | ✅ Required (Hard) | Open and analyse packet captures | `sudo apt install wireshark` |
| `binwalk` | ✅ Recommended | Find and extract embedded files | `sudo apt install binwalk` |
| `xxd` / `hexdump` | Recommended | Hex view in the terminal | `sudo apt install xxd` (or use `hexdump -C`) |
| `tshark` | Optional | Wireshark from the command line | `sudo apt install tshark` |
| **hexed.it** | Optional | Hex editor in the browser, no install | <https://hexed.it> |

**Install everything for this category in one line (Ubuntu/Debian/Kali):**

```bash
sudo apt update && sudo apt install -y binutils libimage-exiftool-perl binwalk wireshark xxd
```

> During the Wireshark install, Ubuntu asks whether non-root users may capture packets. Answer **No**: for CTF you only *open files*, you never need to capture traffic.

## Do I need Kali?

**No.** Ubuntu, Debian, or **WSL2 on Windows** is enough. Kali only ships these tools preinstalled.

One exception: Wireshark has a graphical window. On WSL2 that needs WSL with GUI support (Windows 11). Otherwise install **Wireshark for Windows** from <https://www.wireshark.org/download.html> and open the capture there.

*بالدارجة: ما خاصكش Kali. Ubuntu ولا WSL2 كافيين. Wireshark عندو نسخة ديال Windows إلا ماشي ساهل عندك فـ WSL.*

## Is the browser enough?

| Challenge | Browser only? |
|---|---|
| Easy: Glory of the Garden | Partly — hexed.it works, but `strings` is much faster |
| Medium: So Meta | Partly — online EXIF viewers exist; `exiftool` is more complete |
| Hard: Wireshark capture | ❌ No. You need Wireshark installed |

## Useful commands

```bash
file suspicious.jpg                    # real type: JPEG image data, ... (or something else!)
strings suspicious.jpg | grep -i pico  # search the flag prefix directly
strings -n 8 suspicious.jpg | less     # only strings of 8+ chars, page by page
exiftool suspicious.jpg                # all metadata fields
exiftool suspicious.jpg | grep -i -E "artist|comment|copyright|description"
binwalk suspicious.jpg                 # list embedded files
binwalk -e suspicious.jpg              # extract them into _suspicious.jpg.extracted/
xxd suspicious.jpg | head              # first bytes: check the header
xxd suspicious.jpg | tail              # last bytes: check for appended data
ls -l suspicious.jpg                   # size: bigger than expected?
```

## Safety

- Challenge files are **untrusted**. Keep them in their own folder, and never run them.
- Analysing a file (`strings`, `exiftool`, `binwalk`) is safe. **Executing** it is not.
- A VM is recommended but not mandatory for read-only analysis.

*بالدارجة: الملفات ديال التحديات ما كنشغلوهاش. غير كنحللوها.*

## Wireshark quick start (5 steps)

1. **File → Open** your capture.
2. **Statistics → Protocol Hierarchy** — see which protocols exist. A line called "Line based text data" is a great sign.
3. Type a filter in the bar: `http`, or `tcp`, then press Enter.
4. Right-click an interesting packet → **Follow → TCP Stream**.
5. Read the conversation. Use the arrows at the bottom right to move to the next stream.
