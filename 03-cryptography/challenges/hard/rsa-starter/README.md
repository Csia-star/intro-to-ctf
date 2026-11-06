# RSA Starter (Modular Exponentiation → RSA Decryption)

![Hard](https://img.shields.io/badge/Hard-E53E3E) ![Platform](https://img.shields.io/badge/platform-CryptoHack-805AD5) ![Crypto](https://img.shields.io/badge/category-crypto-00D4FF)

> **STOP!** Don't open the writeup immediately. Try the challenge yourself first. If you're stuck, use the [hints](hints.md) one by one before reading the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | CryptoHack |
| **URL** | <https://cryptohack.org/challenges/rsa/> (section *Starter*) |
| **Challenges** | *Modular Exponentiation*, *Public Keys*, *Euler's Totient*, *Private Keys*, *RSA Decryption* |
| **Access** | Free account to submit answers |
| **Flag?** | Static. Most answers are **numbers**; the last one is a `crypto{...}` flag. Not shown here |
| **Estimated time** | 45–90 minutes |
| **Tools** | Python 3 (`pow`), optionally PyCryptodome |

> **Prerequisite (free):** CryptoHack *General → Mathematics → Modular Arithmetic 1 & 2* if "mod" is new to you.
> "Hard" here means hard for a beginner: it needs math you may not have used before.

## Concepts required

Bytes ⇄ integers (Easy), modular arithmetic, RSA keys, Euler's totient, modular inverse. See [concepts 1, 6, 9–11](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [Modular arithmetic explained](https://www.youtube.com/results?search_query=modular+arithmetic+explained+beginners)
- [RSA algorithm explained simply](https://www.youtube.com/results?search_query=RSA+algorithm+explained+simply)
- [Euler's totient and modular inverse for RSA](https://www.youtube.com/results?search_query=RSA+euler+totient+modular+inverse+explained)

## Your mission

Build RSA step by step: compute a power mod `n`, encrypt, compute `φ(n)`, compute the private key `d`, and finally decrypt a ciphertext.

## Legal reminder

Only submit answers on CryptoHack.
