# PROJECT_PROGRESS

Use this file to continue in a new conversation.

## Current status: all 8 phases complete ✅

| Phase | Scope | Status |
|---|---|---|
| 1 | Structure, README, Getting Started, Linux cheat sheet, Web Exploitation (3 challenges) | ✅ Done |
| 2 | Cryptography (CryptoHack: Encoding, XOR, RSA Starter) | ✅ Done (source-verified) |
| 3 | Forensics (picoCTF: Glory of the Garden, So Meta, Wireshark) | ✅ Done (source-verified) |
| 4 | Steganography (picoCTF: tunn3l v1s10n, St3g0, MacroHard WeakEdge) | ✅ Done (source-verified) |
| 5 | Reverse Engineering (picoCTF: Safe Opener, GDB Test Drive, Classic Crackme) | ✅ Done (source-verified) |
| 6 | Binary Exploitation (picoCTF: buffer overflow 0/1/2) | ✅ Done (source-verified) |
| 7 | OSINT (TryHackMe: OhSINT, Searchlight IMINT, Sakura Room) | ✅ Done (method guides) |
| 8 | Consistency and quality audit + interactive page + packaging | ✅ Done |

## Every category now has

- `README.md` (definition + Darija, method flowchart, concepts/tools links, 3 challenges, progression + concept-coverage tables, quality checklist)
- `concepts/README.md` (ordered concept table with YouTube **search** links, visual diagrams, challenge→concept map)
- `tools/README.md` (tools, install, "do I need Kali?", browser-only note, safety)
- `resources.md`
- `challenges/{easy,medium,hard}/<name>/` each with `README.md`, `hints.md`, `writeup.md`

## Verification notes (honest)

- All challenge names, categories, and platform URLs were checked against the platforms' own pages / well-known public writeups in Nov 2026.
- Writeups are **source-verified**, not re-run live by the author. Every terminal output shown was produced on **our own test files** (clearly labelled), never copied from the real challenge, so **no real flag is reproduced**.
- Tool mechanics (base64, XOR, RSA math, BMP header offsets, LSB extraction, GDB session, cyclic/p32) were **run locally** and their real outputs used.
- picoCTF/TryHackMe answers are left for the learner to find.

## Interactive page

- `docs/index.html` — a self-contained dark-mode roadmap page for GitHub Pages (Settings → Pages → deploy from `/docs`).

## Open items (nice-to-have, not blocking)

- [ ] Add real screenshots to `assets/screenshots/` once you solve each challenge
- [ ] Replace YouTube **search** links with specific verified videos (keep search links as fallback)
- [ ] Optional extra challenges per category (lists already name good candidates)

## Conventions to keep

- Folder template: `README.md`, `hints.md`, `writeup.md` per challenge
- Writeup labels: ✅ Verified / 🟡 Source-verified / ⚠️ Unverified (+ 🟢 Method guide for OSINT)
- Darija beside key ideas; palette `#101827 #00D4FF #805AD5 #F7FAFC`
- Never invent URLs, flags, outputs, or videos
- Difficulty is "for a beginner", not the platform's own score (stated where they differ)
