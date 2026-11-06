# OhSINT

![Easy](https://img.shields.io/badge/Easy-48BB78) ![Platform](https://img.shields.io/badge/platform-TryHackMe-805AD5) ![OSINT](https://img.shields.io/badge/category-osint-00D4FF)

> **STOP!** Try the room yourself first. Use the [hints](hints.md) one by one, then the [method writeup](writeup.md).
>
> *بالدارجة: جرب بوحدك الأول، الـ hints وحدة وحدة، والـ writeup فالأخير.*

> ⚖️ **Ethics:** investigate only the image the room gives you. Never apply this to a real private person.

| | |
|---|---|
| **Platform** | TryHackMe (free) |
| **URL** | <https://tryhackme.com/room/ohsint> |
| **Access** | Free TryHackMe account. Runs in the browser |
| **Given** | A single image file |
| **Goal** | Answer the room's questions (owner's name, location, a password, etc.) |
| **Answers** | Entered in the room (per-account). No universal flag |
| **Estimated time** | 20–40 minutes |
| **Tools** | Browser, an EXIF viewer, reverse image search, username search |

## Concepts required

What OSINT is, extracting every detail, image metadata, reverse image search, username enumeration, pivoting.
See [concepts 1–4, 6, 9](../../../concepts/README.md).

## Videos to watch before attempting

Search links (no single video was verified):

- [What is OSINT (and ethics)](https://www.youtube.com/results?search_query=what+is+osint+explained+ethics)
- [EXIF GPS metadata from a photo](https://www.youtube.com/results?search_query=exif+gps+metadata+photo+osint)
- [Username enumeration with WhatsMyName](https://www.youtube.com/results?search_query=username+enumeration+osint+whatsmyname)

## Your mission

You get one picture and a series of questions. The whole room is a lesson in **pivoting**: the image's metadata gives a handle, the handle gives a profile, the profile gives the next answer, and so on.

## Legal reminder

This is a designed training scenario. Do not use the techniques on real people.
