# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

First, do the basics anyway: `file`, `strings`, `exiftool`, `binwalk`. When they find nothing, the data is probably **inside the pixels**, not around them.
</details>

<details>
<summary>Hint 2</summary>

The challenge name *St3g0* and the clean image point to classic **LSB** steganography: the secret lives in the last bit of each colour value.
</details>

<details>
<summary>Hint 3</summary>

You cannot see LSB data by eye. Use a tool that reads bit planes: `zsteg` (command line) or upload the image to **Aperi'Solve** in the browser.
</details>

<details>
<summary>Hint 4</summary>

Run `zsteg -a` to try all bit-plane combinations. Look in the output for a line that contains text starting with `picoCTF`. The flag may end with an extra marker (like `$t3g0`) that is not part of it.
</details>
