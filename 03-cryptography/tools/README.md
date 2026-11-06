# Crypto Tools and Environment

| Tool | Required? | Purpose | Installation / Access |
|---|---|---|---|
| **CyberChef** | ✅ Recommended | Decode Base64/hex, ROT13, XOR in the browser | <https://gchq.github.io/CyberChef/> (no install) |
| **Python 3** | ✅ Required (Medium, Hard) | Scripts for XOR and RSA | Preinstalled on most Linux; Windows: <https://www.python.org/downloads/> |
| **PyCryptodome** | ✅ Recommended | `long_to_bytes`, `bytes_to_long` helpers | `pip install pycryptodome` |
| `base64`, `xxd` | Optional | Quick decoding in the terminal | `sudo apt install coreutils xxd` |
| **dCode.fr** | Optional | Identify classic ciphers | <https://www.dcode.fr/cipher-identifier> |

> On Ubuntu/Debian, if `pip install` complains about an "externally managed environment", use a virtual environment:
> ```bash
> python3 -m venv ~/ctf-venv && source ~/ctf-venv/bin/activate
> pip install pycryptodome
> ```

## Do I need Kali?

**No.** Any OS with a browser and Python works. A VM is not needed for crypto: you only run your own small scripts.

*بالدارجة: ما خاصكش Kali. CyberChef فـ المتصفح و Python كافيين.*

## When is the browser enough?

| Challenge | Browser (CyberChef) only? |
|---|---|
| Easy: Encoding | ✅ Yes |
| Medium: XOR | Partly (XOR Starter yes; Favourite byte is easier in Python) |
| Hard: RSA | ❌ Use Python (`pow`) |

## Useful commands

```bash
echo 'aGVsbG8=' | base64 -d          # Base64 → text   → hello
echo -n 'hello' | base64             # text → Base64   → aGVsbG8=
echo '68656c6c6f' | xxd -r -p        # hex → text      → hello
echo -n 'hello' | xxd -p             # text → hex      → 68656c6c6f
```

## Python cheat sheet

```python
import base64
bytes.fromhex("68656c6c6f")           # b'hello'
b"hello".hex()                        # '68656c6c6f'
base64.b64decode("aGVsbG8=")          # b'hello'
int.from_bytes(b"Hi", "big")          # 18537
(18537).to_bytes(2, "big")            # b'Hi'
bytes([x ^ 0x20 for x in b"Hi"])      # XOR every byte with 0x20 → b'hI'
pow(4, 13, 497)                       # modular exponentiation → 445
pow(17, -1, 3120)                     # modular inverse (Python 3.8+) → 2753
```

Every output above was checked with Python 3.

## CyberChef in 4 steps

1. Paste the data into **Input**.
2. Drag an operation (e.g. *From Base64*) into **Recipe**.
3. Read the **Output**. Not readable? Add another operation.
4. Try the **Magic** operation: it guesses common encodings automatically.
