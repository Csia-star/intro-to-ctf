# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

Opening the presentation and reading the slides will not show the flag. The challenge name hints at Microsoft (MacroHard) and a weak spot (WeakEdge).
</details>

<details>
<summary>Hint 2</summary>

A `.pptx`/`.pptm`/`.docx` file is actually a **ZIP archive**. Copy it to `name.zip` and `unzip` it, or run `unzip -l` to list what is inside.
</details>

<details>
<summary>Hint 3</summary>

Browse the extracted folders (`ppt/`, `docProps/`, etc.). Look for a file that should not be there, or one whose name stands out. `grep -r pico .` across the extracted folder is worth a try.
</details>

<details>
<summary>Hint 4</summary>

The hidden file's contents look like meaningless whitespace or a long encoded blob. Try reading it as **Base64** (whitespace stego often decodes to Base64, which then gives the flag). Paste it into CyberChef.
</details>
