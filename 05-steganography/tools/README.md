# Steganography Tools and Environment

| Tool | Required? | Purpose | Installation / Access |
|---|---|---|---|
| **Aperi'Solve** | ✅ Recommended | Runs many stego tools on an image at once, in the browser | <https://aperisolve.fr> (no install) |
| `file`, `strings`, `exiftool`, `binwalk` | ✅ Required | The forensics basics you always run first | See [Forensics tools](../../04-forensics/tools/README.md) |
| `zsteg` | ✅ Required (Medium) | Detects LSB / bit-plane data in PNG & BMP | `sudo gem install zsteg` (needs Ruby) |
| **A hex editor** | ✅ Required (Easy) | Repair a broken file header | `hexed.it` (browser) or `ghex` / `bless` (desktop) |
| `unzip` | ✅ Required (Hard) | Office files are ZIPs | Preinstalled |
| `steghide` | Recommended | Extract passphrase-protected data from JPG/WAV | `sudo apt install steghide` |
| **Audacity** | Optional (audio) | Spectrogram view of sound files | <https://www.audacityteam.org> |
| **stegsolve** | Optional | Browse image bit planes & channels (Java) | Search "stegsolve.jar" (official: Caesum) |
| `stegcracker` | Optional | Brute-force a steghide password with a wordlist | `pip install stegcracker` |

**Install the command-line set (Ubuntu/Debian/Kali):**

```bash
sudo apt update && sudo apt install -y binutils libimage-exiftool-perl binwalk steghide unzip ruby
sudo gem install zsteg
```

## Do I need Kali?

**No.** Ubuntu/Debian/WSL2 works. In fact, **Aperi'Solve** in a browser solves a large share of image stego with zero install: it runs `zsteg`, `steghide`, `binwalk`, `exiftool`, and shows bit planes for you.

*بالدارجة: ما خاصكش Kali. Aperi'Solve فـ المتصفح كيدير بزاف ديال الأدوات دفعة وحدة.*

## Is the browser enough?

| Challenge | Browser only? |
|---|---|
| Easy: tunn3l v1s10n | Yes — `hexed.it` to fix the header |
| Medium: St3g0 | Yes — Aperi'Solve runs `zsteg` for you (or install `zsteg`) |
| Hard: MacroHard WeakEdge | Mostly — you need `unzip`; an online unzip works, local is easier |

## Useful commands

```bash
file secret.bmp                      # is the header/type right?
strings secret.png | grep -i pico    # always try this first
zsteg secret.png                     # scan PNG/BMP bit planes for hidden text
zsteg -a secret.png                  # try all known bit-plane combinations
steghide info secret.jpg             # is something embedded? (press Enter for empty password)
steghide extract -sf secret.jpg      # extract it (asks for the passphrase)
unzip -l presentation.pptx           # list the files inside an Office document
unzip presentation.pptx -d out/      # extract them to inspect
```

## Safety

- Treat challenge media as **untrusted**. Analyse, do not execute.
- `steghide`/`zsteg` only read the file; they are safe to run on challenge media.

*بالدارجة: الملفات ديال التحدي ما كنشغلوهاش. غير كنحللوها.*

## Aperi'Solve in 3 steps

1. Go to <https://aperisolve.fr> and upload the image.
2. It automatically runs `zsteg`, `steghide`, `binwalk`, `exiftool`, and shows each bit plane / colour channel.
3. Read the results tabs. If a flag is in a bit plane or a channel, it usually appears here without any command.
