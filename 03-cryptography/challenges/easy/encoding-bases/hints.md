# Hints (open one at a time)

<details>
<summary>Hint 1 (ASCII)</summary>

Each number in the list is one character. Which Python function turns `99` into `c`?
</details>

<details>
<summary>Hint 2 (Hex)</summary>

Two hex digits = one byte. Python's `bytes` type has a class method that reads a hex string.
</details>

<details>
<summary>Hint 3 (Base64)</summary>

Read the statement carefully: it gives you **hex**, but asks for the **Base64** of the bytes. That is two steps, in order: hex → bytes → Base64.
</details>

<details>
<summary>Hint 4 (Bytes and Big Integers)</summary>

A big number can be read as a sequence of bytes (base 256). Convert the integer to hex first and look at it, or use `long_to_bytes` from PyCryptodome.
</details>
