# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

Try the easy win first: `strings ./crackme | grep -i pico`. When the password is not plainly there, it is being **computed or compared piece by piece** in the code.
</details>

<details>
<summary>Hint 2</summary>

Open the binary in Ghidra (Import → analyse with defaults). Go to `main` and read the **Decompile** window. Find where your input is compared.
</details>

<details>
<summary>Hint 3</summary>

The check may compare each character against a specific value (a number like `0x64`, or an arithmetic result). Those numbers are ASCII codes. `0x64` is the character `d`.
</details>

<details>
<summary>Hint 4</summary>

Read every compared value in order, convert each from its ASCII code to a character, and join them. That string is the password. Test it by running the binary (in your VM).
</details>
