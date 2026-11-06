# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

If you were given a `.java` file, you can just read it. If you got a `.class` file, it is compiled — decompile it back to source first.
</details>

<details>
<summary>Hint 2</summary>

Look for the method that handles the password, often named something like `openSafe` or `checkPassword`. Find the line that **compares** your input (an `equals` or `==`).
</details>

<details>
<summary>Hint 3</summary>

The expected password may not be written as one plain string. It can be **built** in the code (pieces joined together, or decoded from Base64). Read exactly how it is assembled.
</details>

<details>
<summary>Hint 4</summary>

If the password is Base64-encoded in the source, decode it (CyberChef). The decoded value is what the safe accepts, and for this challenge it is the flag.
</details>
