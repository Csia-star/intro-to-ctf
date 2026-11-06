# OSINT Tools and Environment

| Tool | Required? | Purpose | Access |
|---|---|---|---|
| **A web browser** | ✅ Required | 95% of OSINT happens here | Any browser |
| **Google Lens** | ✅ Recommended | Reverse image search, best for landmarks/objects | <https://lens.google> |
| **Yandex Images** | ✅ Recommended | Reverse image search, strong on faces/places | <https://yandex.com/images/> |
| **TinEye** | Recommended | Finds exact copies of an image online | <https://tineye.com> |
| `exiftool` | ✅ Recommended | Read GPS/metadata from a photo | `sudo apt install libimage-exiftool-perl` (or an online EXIF viewer) |
| **WhatsMyName** | ✅ Recommended | Check a username across many platforms | <https://whatsmyname.app> |
| **Wayback Machine** | Recommended | View old versions of web pages | <https://web.archive.org> |
| **Google Maps / Street View** | ✅ Recommended | Confirm a geolocation on the ground | <https://maps.google.com> |
| **OSINT Framework** | Optional | Directory of specialised tools | <https://osintframework.com> |

## Do I need Kali or a VM?

**No.** OSINT is browser-first. You do not run untrusted files, so no VM is needed. `exiftool` is the only local tool worth having, and even that has online equivalents.

*بالدارجة: ما خاصكش Kali ولا VM. المتصفح كافي. `exiftool` هي الأداة المحلية الوحيدة اللي مفيدة، وكاينة ليها بدائل أونلاين.*

## Is the browser enough?

| Challenge | Browser only? |
|---|---|
| Easy: OhSINT | Yes (an online EXIF viewer covers the metadata step) |
| Medium: Searchlight IMINT | Yes |
| Hard: Sakura Room | Yes |

## Useful commands & techniques

```bash
exiftool photo.jpg | grep -i -E "gps|date|author|camera"   # pull location/time from a photo
```

**Reverse image search:** save the image, then upload it to Google Lens, Yandex, and TinEye. Different engines win on different images — try more than one.

**Google dorking cheat sheet:**

```
site:example.com              only results from this site
filetype:pdf                  only PDFs
intitle:"index of"            exposed directory listings
inurl:admin                   pages with 'admin' in the URL
"exact phrase"                must contain this phrase
site:example.com filetype:xlsx   combine operators
```

**Username enumeration:** paste the handle into <https://whatsmyname.app> to see every platform it exists on, then open the public profiles.

**Geolocation workflow:** read signs (language, phone numbers, area codes) → identify the country → reverse-image the landmark → confirm the exact spot in Street View.

## Safety & ethics

- Investigate **only** the image/username/scenario the challenge gives you.
- Never geolocate, profile, or track a **real private person**. That can be harmful and illegal.
- Do not log into, message, or interact with any account you find — just observe public data.

*بالدارجة: غير الهدف ديال التحدي. بلا ما تدخل لشي حساب ولا تراسل شي واحد. غير كتفرج فالمعلومة العامة.*
