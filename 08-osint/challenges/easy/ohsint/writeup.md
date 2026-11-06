# Writeup: OhSINT (method)

> 🟢 **Verification status: Method guide, source-verified.**
> TryHackMe answers are per-account and this room is a well-known beginner box; the **method** below matches its public description (checked Nov 2026). This guide deliberately gives **no answers** — it teaches the pivots so you solve it yourself.
>
> ⛔ **Spoilers (method) below.** Try the room and the [hints](hints.md) first.
> ⚖️ Training scenario only. Never apply this to a real private person.

**Room:** <https://tryhackme.com/room/ohsint>
**Goal:** answer the room's questions by pivoting from one image.

## The idea

Everything starts from a single picture. OhSINT teaches that **one artifact can leak a chain of facts** if you pivot patiently.

## Step 1: Read the image's metadata

- Download the image. Open it in an EXIF viewer or run `exiftool image.jpg`.
- Look for an **author/owner** field and any **GPS** data.
- *Why:* metadata is the laziest, most reliable first pivot. The owner field often contains a reusable **username**.

## Step 2: Turn the name into a username search

- Take the name you found and search it across platforms (whatsmyname.app) and in a normal search engine.
- *Why:* people reuse the same handle. One name → a blog, a social profile, a code-hosting profile.

## Step 3: Read every public profile you find

- Open each profile. Note the avatar, bio, pinned posts, and any location mentioned.
- *Why:* the room asks for things like the person's location and other facts — these live in the profiles, not in the original image.
- Cross-check: if a location appears in a bio, confirm it against another profile or post.

## Step 4: Find the detail hidden "in plain sight"

- One answer is placed somewhere easy to overlook: the **content of a blog post**, or even a visual property of a page (for example, text made the same colour as its background so it is invisible until you select it, or view the page source).
- *Why:* the room teaches you to inspect pages fully, not just skim them.

## Method recap

| Pivot | From → To |
|---|---|
| Metadata | image → owner username |
| Username | handle → public profiles |
| Profiles | bios/posts → location & other facts |
| Close reading | page content/source → the hidden answer |

*بالدارجة: من تصويرة وحدة: الـ metadata كتعطي username، الـ username كيعطي profiles، والـ profiles كيعطيو الأجوبة. آخر جواب مخبي فـ صفحة، قلّب مزيان.*

**Next:** [Medium room →](../../medium/searchlight-imint/README.md)
