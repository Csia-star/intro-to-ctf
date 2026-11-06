# Wireshark doo dooo do doo

![Hard](https://img.shields.io/badge/Hard-E53E3E) ![Platform](https://img.shields.io/badge/platform-picoCTF-805AD5) ![Forensics](https://img.shields.io/badge/category-forensics-00D4FF)

> **STOP!** Don't open the writeup immediately. Try the challenge yourself first. If you're stuck, use the [hints](hints.md) one by one before reading the [complete solution](writeup.md).
>
> *بالدارجة: جرب بوحدك، الـ hints وحدة وحدة، والـ writeup فالأخير.*

| | |
|---|---|
| **Platform** | picoCTF — picoGym practice |
| **Where** | [picoGym → Forensics](https://play.picoctf.org/practice?category=4), search *Wireshark doo dooo do doo* |
| **Access** | Free picoCTF account (challenges are behind a login) |
| **picoCTF points** | 50 (their scale; see note) |
| **Given file** | `shark1.pcapng` — a network capture |
| **Goal** | Find the flag inside the captured traffic |
| **Flag?** | Static, format `picoCTF{...}`, but **encoded** inside the capture. Not shown here |
| **Estimated time** | 20–40 minutes |
| **Tools** | Wireshark (+ CyberChef or any ROT13 decoder) |

> **Why "Hard" when picoCTF says 50 points?** It needs a new tool (Wireshark), the idea of following a stream, **and** recognising an encoded flag. More moving parts than the first two, so we rank it last.

## Concepts required

Packets and protocols, packet captures, Wireshark basics, following a stream — plus **ROT13** from [Cryptography](../../../../03-cryptography/concepts/README.md).
See [concepts 8–11](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [Wireshark tutorial for beginners](https://www.youtube.com/results?search_query=wireshark+tutorial+for+beginners)
- [Wireshark follow TCP stream](https://www.youtube.com/results?search_query=wireshark+follow+tcp+stream+tutorial)
- [ROT13 / Caesar cipher explained](https://www.youtube.com/results?search_query=rot13+caesar+cipher+explained)

## Your mission

Open the capture, find the one conversation that carries a flag-shaped string, and notice it is **not** plaintext. Decode it to get the real flag.

## Legal reminder

This is a recorded capture file from picoCTF. You only open and read it. Never capture traffic on networks you do not own.
