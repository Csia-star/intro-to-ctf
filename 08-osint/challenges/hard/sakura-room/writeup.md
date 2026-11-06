# Writeup: Sakura Room (method)

> 🟢 **Verification status: Method guide, source-verified.**
> TryHackMe answers are per-account; the OSINT Dojo's Sakura Room is a well-documented beginner investigation. This guide matches its public description (checked Nov 2026) and gives **no answers** — only the chain of techniques.
>
> ⛔ **Spoilers (method) below.** Try the room and the [hints](hints.md) first.
> ⚖️ Consented training scenario only. Never investigate a real private individual.

**Room:** <https://tryhackme.com/room/sakura>
**Goal:** solve each tier by chaining OSINT techniques.

## The idea

Sakura Room is the capstone: no single trick solves it. You **pivot** through tier after tier, each answer unlocking the next search. It rewards method over luck.

## Tier 1 — Who made this?

- Inspect the starting image's **metadata** (`exiftool`). If it is stripped, use **reverse image search** to find where it was posted and the account behind it.
- *Pivot produced:* a username/handle.

## Tier 2 — Who are they?

- **Enumerate the handle** across platforms (whatsmyname.app, search engines). Open each public profile.
- Read bios and posts for the person's **real name** and other identifiers.
- *Pivot produced:* name + more profiles.

## Tier 3 — Where are they?

- Photos on those profiles are **geolocatable**: read signs, landmarks, language; confirm the exact place in **Google Maps Street View**.
- Cross-check the location against claims in the profiles.
- *Pivot produced:* a confirmed location.

## Tier 4 — Follow the trail further

- Later tiers reach into other **public** records. Typical pivots in this room include:
  - a **public cryptocurrency address** → look it up on a blockchain explorer to see public transactions;
  - **archived pages** → the Wayback Machine for content that changed or was removed.
- Each record answers a tier and points to the next.

## Why this is the capstone

| Technique | Where it appears |
|---|---|
| Metadata / reverse image | Tier 1 |
| Username enumeration | Tier 2 |
| Geolocation (Street View) | Tier 3 |
| Public records & archives | Tier 4+ |
| Pivoting & cross-checking | Every tier |

*بالدارجة: هاد الـ room كتجمع كلشي: metadata، reverse image، username، geolocation، سجلات عامة. كل جواب كيفتح اللي بعدو. الطريقة هي اللي كتربح، ماشي الحظ.*

**You finished the categories!** Head back to the [main README](../../../../README.md) to review, or redo any challenge without looking at the writeup.
