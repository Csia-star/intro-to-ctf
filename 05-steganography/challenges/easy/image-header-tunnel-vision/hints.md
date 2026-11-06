# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

Run `file` on it. It does not say "nice clean image". The problem is the start of the file, the **header**, not the picture data.
</details>

<details>
<summary>Hint 2</summary>

Open it in a hex editor and look at the very first bytes. Compare them with the known header of a **BMP** image (`42 4D`, i.e. `BM`).
</details>

<details>
<summary>Hint 3</summary>

Some header fields (like the stated image height) may have been changed to hide the picture. Work on a **copy**. Fix the magic bytes first, then the size fields.
</details>

<details>
<summary>Hint 4</summary>

Once the header is valid, open the image. If the flag is cut off, the height field is still wrong: increase it so the whole picture (and the flag) shows.
</details>
