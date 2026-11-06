# Set Up Your Environment

You do **not** need an expensive setup. Start simple.

## Do I need Kali Linux?

| Option | Verdict |
|---|---|
| **Ubuntu / Debian (normal install or WSL2)** | ✅ Enough for most beginner challenges. |
| **Kali Linux** | Optional. Comes with many tools pre-installed. Not required to start. |
| **Virtual machine** | ✅ Recommended: you can break things safely and take snapshots. |
| **Browser-only** | ✅ Enough for many web, crypto (CyberChef), and OSINT challenges. |

*بالدارجة: ما خاصكش Kali باش تبدا. Ubuntu وصافي، والـ VM كيحميك من الأخطاء.*

## Recommended path

1. Install **VirtualBox** (free): <https://www.virtualbox.org>
2. Install **Ubuntu** (<https://ubuntu.com/download/desktop>) or **Kali** (<https://www.kali.org/get-kali/>) as a VM. Download only from the official site.
3. Take a **snapshot** after setup.
4. On Windows you can also use **WSL2** (Ubuntu inside Windows): run `wsl --install` in an administrator PowerShell, then restart.

## Core tools (all categories)

```bash
sudo apt update
sudo apt install -y git curl wget unzip file binutils xxd netcat-openbsd python3 python3-pip tree
```

> Package names are for Ubuntu/Debian/Kali. `binutils` gives you `strings`. `netcat-openbsd` gives you `nc`.

## Tools by category (install later, when needed)

| Tool | Purpose | Installation / Access |
|---|---|---|
| Browser DevTools | Inspect pages, requests, cookies | Built into Firefox/Chrome (`F12`) |
| Burp Suite Community | Intercept and modify web requests | <https://portswigger.net/burp/communitydownload> |
| CyberChef | Decode/encode (Base64, hex, ...) | <https://gchq.github.io/CyberChef/> (browser) |
| `strings`, `file`, `xxd` | Quick file analysis | `sudo apt install binutils xxd` |
| Python 3 | Small scripts | Preinstalled on most Linux |
| Ghidra | Reverse engineering | <https://ghidra-sre.org> (later) |

## Safety rules for your lab

- Keep your VM updated.
- Do **not** run unknown files on your main OS. Use the VM.
- Never scan networks you do not own or have permission to test.

## Quick test

```bash
python3 --version
curl --version | head -n 1
file --version | head -n 1
```

If each command prints a version, you are ready.

**Next:** [Linux cheat sheet →](../01-linux-cheatsheet/README.md)
