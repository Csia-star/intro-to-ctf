# Encoding: ASCII, Hex, Base64 (+ Bytes and Big Integers)

![Easy](https://img.shields.io/badge/Easy-48BB78) ![Platform](https://img.shields.io/badge/platform-CryptoHack-805AD5) ![Crypto](https://img.shields.io/badge/category-crypto-00D4FF)

> **STOP!** Don't open the writeup immediately. Try the challenge yourself first. If you're stuck, use the [hints](hints.md) one by one before reading the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول. إلا تعطلتي، استعمل الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | CryptoHack |
| **URL** | <https://cryptohack.org/challenges/general/> (section *Encoding*) · course: <https://cryptohack.org/courses/intro/> |
| **Challenges** | *ASCII* (5 pts), *Hex* (5 pts), *Base64* (10 pts), *Bytes and Big Integers* (10 pts) |
| **Access** | Free account to submit flags. Statements are readable without login. |
| **Flag?** | Static flags, format `crypto{...}`. Not shown here |
| **Estimated time** | 20–40 minutes for the four |
| **Tools** | CyberChef **or** Python 3 |

> We treat these four small CryptoHack tasks as **one** Easy challenge because each teaches one piece of the same idea.

## Concepts required

Bytes and ASCII, hex, Base64, bytes ⇄ integers. See [concepts 1–4 and 6](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [ASCII, bits and bytes](https://www.youtube.com/results?search_query=ASCII+bits+bytes+explained+beginners)
- [Hexadecimal explained](https://www.youtube.com/results?search_query=hexadecimal+explained+beginners)
- [Base64 encoding explained](https://www.youtube.com/results?search_query=base64+encoding+explained)

## Your mission

Each task gives you data in one shape (a list of numbers, a hex string, a big integer). Convert it to readable text to get the flag.

## Legal reminder

Only submit flags on CryptoHack. Don't share flags publicly.
