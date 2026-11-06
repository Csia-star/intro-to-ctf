# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

Open `shark1.pcapng` in Wireshark. There are many packets. Start with **Statistics → Protocol Hierarchy** to see what kinds of traffic exist.
</details>

<details>
<summary>Hint 2</summary>

Most of it is noise. A flag is text, so filter for `http` (or just `tcp`) and look for a human-readable payload.
</details>

<details>
<summary>Hint 3</summary>

Right-click a promising packet → **Follow → TCP Stream**. Step through the streams with the arrows at the bottom right. One stream ends with a string in curly braces `{ }`.
</details>

<details>
<summary>Hint 4</summary>

The string looks almost like the flag but scrambled: it starts `cvpbPGS{...}`. Apply ROT13 to `cvpbPGS` and see what it becomes. Then decode the whole string the same way.
</details>
