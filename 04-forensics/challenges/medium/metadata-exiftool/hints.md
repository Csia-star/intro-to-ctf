# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

The challenge name *So Meta* is a direct hint. "Meta" as in **metadata**: the information stored *about* the image (author, date, comments), separate from the pixels.
</details>

<details>
<summary>Hint 2</summary>

`strings` will actually reveal it too, mixed into the output. But there is a tool made specifically for reading metadata cleanly.
</details>

<details>
<summary>Hint 3</summary>

Install and run `exiftool` on the image. Read every field it prints.
</details>

<details>
<summary>Hint 4</summary>

Look at unusual fields such as `Artist`, `Comment`, or `Copyright`. One of them holds the `picoCTF{...}` flag.
</details>
