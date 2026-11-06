# Linux Cheat Sheet for CTF Beginners

Keep this page open while you practice. Most CTF work happens in a terminal.

> ⚠️ **Warnings**
> - `rm -rf` deletes **without** a recycle bin. Never run it on `/` or `~` or paths you didn't type yourself.
> - Never copy-paste commands you do not understand, especially with `sudo`.
> - **Network scanning (`nmap`, `nc`, `curl` on targets) only on systems you are authorized to test** (your own lab or the CTF's provided targets).
>
> *بالدارجة: `rm -rf` ما كايرجعش الملفات. و`nmap` غير فـ الأهداف المسموحة.*

## Quick reference

| Need | Command |
|---|---|
| Where am I? | `pwd` |
| List files (with hidden) | `ls -la` |
| Read a file | `cat file` |
| Find text in files | `grep -rn "text" .` |
| Find a file by name | `find . -name "flag*"` |
| What type is this file? | `file thing` |
| Readable text inside a binary | `strings thing` |
| Hex view | `xxd thing \| head` |
| Decode Base64 | `echo 'aGk=' \| base64 -d` |
| Hash a file | `sha256sum file` |
| Fetch a web page | `curl -i URL` |
| Unzip | `unzip file.zip` |

---

## 1. Navigation

| Command | Purpose | Example | Expected output | Darija |
|---|---|---|---|---|
| `pwd` | Print current folder | `pwd` | `/home/user/ctf` | فين أنا دابا |
| `ls` | List files | `ls -la` | files, including hidden ones starting with `.` | كيورّيك الملفات (`-a` للمخبية) |
| `cd` | Change folder | `cd challenges` · `cd ..` · `cd ~` | no output (prompt changes) | تنتقل لفولدر |
| `tree` | Show folder tree | `tree -L 2` | indented tree of 2 levels | كيورّيك الهيكل |

> `tree` may need `sudo apt install tree`.

## 2. File operations

| Command | Purpose | Example | Notes | Darija |
|---|---|---|---|---|
| `cat` | Print a file | `cat flag.txt` | Best for short text files | كيقرا الملف |
| `less` | Read long files page by page | `less big.log` | `q` quit, `/word` search | قراءة ملف طويل |
| `head` | First lines | `head -n 5 file` | default 10 lines | البداية |
| `tail` | Last lines | `tail -n 5 file` | `tail -f` follows live logs | النهاية |
| `cp` | Copy | `cp a.txt b.txt` | `-r` for folders | نسخ |
| `mv` | Move/rename | `mv old.txt new.txt` | | نقل/تسمية |
| `rm` | Delete ⚠️ | `rm file.txt` | permanent | مسح (حذر!) |
| `touch` | Create empty file | `touch notes.txt` | | كريي ملف خاوي |

## 3. Searching

| Command | Purpose | Example | Expected output | Darija |
|---|---|---|---|---|
| `grep` | Search text | `grep -rn "flag" .` | `./a.txt:3:flag{...}`-style lines | قلب على كلمة |
| `find` | Find files | `find / -name "flag*" 2>/dev/null` | list of paths (errors hidden) | قلب على ملف |
| `locate` | Fast find by name (uses a database) | `locate flag.txt` | paths; may need `sudo updatedb` | قلب سريع |
| `strings` | Readable text in binary | `strings image.png \| grep -i flag` | printable strings | كيستخرج النص من ملف |

Useful `grep` options: `-i` ignore case, `-r` recursive, `-n` line numbers, `-v` invert.

## 4. File analysis

| Command | Purpose | Example | Expected output | Darija |
|---|---|---|---|---|
| `file` | Real file type (ignores extension) | `file mystery` | `PNG image data, ...` or `Zip archive data` | شنو نوع الملف بصح |
| `xxd` | Hex dump | `xxd file \| head` | offset, hex bytes, ASCII | عرض بالهيكس |
| `hexdump` | Another hex viewer | `hexdump -C file \| head` | similar to `xxd` | بحال xxd |
| `stat` | File details | `stat file` | size, permissions, timestamps | معلومات الملف |

> Why `file`? Extensions can lie. A `.jpg` may really be a ZIP. `file` reads the first bytes ("magic bytes").

## 5. Permissions

| Command | Purpose | Example | Notes | Darija |
|---|---|---|---|---|
| `ls -la` | Show permissions | `ls -la` | `-rwxr-xr--` = owner/group/others | الصلاحيات |
| `chmod` | Change permissions | `chmod +x script.sh` | makes it executable | كتعطي صلاحية |
| `chown` | Change owner | `sudo chown user:user file` | needs root | كتبدل المالك |

Reading `-rwxr-xr--`: first char type (`-` file, `d` folder); then 3 triplets: owner `rwx`, group `r-x`, others `r--`.

## 6. Networking

| Command | Purpose | Example | Darija |
|---|---|---|---|
| `ping` | Test if a host answers | `ping -c 3 example.com` | واش السيرفر كيجاوب |
| `curl` | Make HTTP requests | `curl -i https://example.com` (`-i` shows headers) | تصيفط request |
| `wget` | Download a file | `wget URL` | تحميل |
| `ip` | Show your IPs | `ip a` | الـ IP ديالك |
| `ss` | Show open connections/ports | `ss -tulpn` | البورتات المفتوحة |
| `nc` | Connect to a port (used for Pwn/CTF servers) | `nc host 1337` | تتصل بسيرفر التحدي |

## 7. Archives

| Command | Purpose | Example | Darija |
|---|---|---|---|
| `unzip` | Extract ZIP | `unzip a.zip` | فك الضغط |
| `zip` | Create ZIP | `zip out.zip file1 file2` | ضغط |
| `tar` | Extract/create tar | `tar -xvf a.tar` · `tar -xzvf a.tar.gz` · `tar -czvf out.tar.gz folder/` | أرشيف |
| `gzip` | Compress/decompress | `gzip file` · `gzip -d file.gz` | ضغط gz |

## 8. Encoding and hashing

| Command | Purpose | Example | Expected output | Darija |
|---|---|---|---|---|
| `base64` | Encode/decode Base64 | `echo 'aGVsbG8=' \| base64 -d` | `hello` | فك Base64 |
| `sha256sum` | SHA-256 hash | `sha256sum file` | 64 hex chars + filename | بصمة الملف |
| `md5sum` | MD5 hash (old, weak) | `md5sum file` | 32 hex chars | بصمة MD5 |
| `xxd` | Hex ⇄ bytes | `echo -n "hi" \| xxd -p` → `6869` · `echo 6869 \| xxd -r -p` → `hi` | تحويل هيكس |

> Base64 is **encoding**, not encryption. Anyone can decode it.

## 9. Processes

| Command | Purpose | Example | Darija |
|---|---|---|---|
| `ps` | List processes | `ps aux` | البرامج الخدامة |
| `top` | Live process monitor | `top` (`q` to quit) | مراقبة مباشرة |
| `kill` | Stop a process | `kill PID` (`kill -9 PID` if stuck) | قتل برنامج |

## 10. Useful CTF operations

| Command | Purpose | Example | Darija |
|---|---|---|---|
| `nmap` | Port scan ⚠️ | `nmap -sV <authorized-target>` | سكان للبورتات (غير بإذن) |
| `whois` | Domain registration info | `whois example.com` | معلومات الدومين |
| `dig` | DNS lookup | `dig example.com` · `dig +short example.com` | DNS |

> `nmap`, `whois`, `dig` may need `sudo apt install nmap whois dnsutils`.

## Pipes and redirects (very useful)

| Syntax | Meaning | Example |
|---|---|---|
| `a \| b` | Send output of `a` into `b` | `strings f \| grep flag` |
| `> file` | Write output to a file (overwrites) | `ls > list.txt` |
| `>> file` | Append | `echo hi >> notes.txt` |
| `2>/dev/null` | Hide error messages | `find / -name x 2>/dev/null` |

## Practice

Play **OverTheWire Bandit**: <https://overthewire.org/wargames/bandit/>. It teaches these commands with real levels.
