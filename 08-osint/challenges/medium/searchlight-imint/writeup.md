# Writeup: Searchlight - IMINT (method)

> 🟢 **Verification status: Method guide, source-verified.**
> TryHackMe answers are per-account; this guide matches the room's public description (checked Nov 2026) and gives **no answers** — only the image-intelligence method.
>
> ⛔ **Spoilers (method) below.** Try the room and the [hints](hints.md) first.
> ⚖️ Training images only. Never geolocate a real private person.

**Room:** <https://tryhackme.com/room/searchlightosint>
**Goal:** identify and locate each provided image.

## The idea

IMINT = Image INTelligence. You turn pixels into a place by combining reverse image search with careful reading of what is *in* the frame.

## Step 1: Reverse image search first

- Save the image, then upload it to **Google Lens**, **Yandex Images**, and **TinEye**.
- *Why:* for a famous landmark this often names it instantly. Different engines are strong on different content — Yandex frequently wins on buildings and places.

## Step 2: Read the frame for clues

- List every readable detail: shop/brand names, **language and script**, phone-number format, licence-plate style, flags, road markings, climate/vegetation.
- *Why:* even when reverse search fails, these pin down a country, then a city. A single sign in a specific language plus a phone format can be enough.

## Step 3: Confirm on the ground with Street View

- Open Google Maps, go to the suspected area, drop into **Street View**, and match the exact building, angle, and surroundings in the photo.
- *Why:* this turns a guess ("probably this city") into a confirmed answer ("this exact corner").

## Step 4: Pivot and cross-check

- Each confirmed detail feeds the next question. Before submitting, verify with **two** independent features (e.g. a landmark shape *and* a street name), not one.

## Method recap

| Step | Tool |
|---|---|
| Identify the scene | Google Lens / Yandex / TinEye |
| Narrow the country/city | signs, language, plates in the image |
| Confirm the exact spot | Google Maps Street View |
| Trust the answer | cross-check two features |

*بالدارجة: صوّر → reverse image search → قرا الإشارات واللغة باش تحدد البلاد → أكّد البلاصة بالضبط فـ Street View → تأكّد بزوج تفاصيل قبل ما تجاوب.*

**Next:** [Hard room →](../../hard/sakura-room/README.md)
