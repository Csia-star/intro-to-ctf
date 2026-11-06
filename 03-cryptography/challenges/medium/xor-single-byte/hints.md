# Hints (open one at a time)

<details>
<summary>Hint 1 (XOR Starter)</summary>

XOR each **character code** of the given string with the given integer, then turn the codes back into characters. `ord()` and `chr()` are your friends.
</details>

<details>
<summary>Hint 2 (XOR Properties)</summary>

You know `A ⊕ A = 0` and `A ⊕ 0 = A`. If `KEY2 ⊕ KEY1` is given and you know `KEY1`, how do you get `KEY2` alone?
</details>

<details>
<summary>Hint 3 (Favourite byte)</summary>

A single byte has only **256** possible values (0–255). That is very few for a computer.
</details>

<details>
<summary>Hint 4 (Favourite byte)</summary>

Try every key. Keep only the result that starts with `crypto{`. Even faster: XOR the first ciphertext byte with `ord('c')` to get the key directly.
</details>
