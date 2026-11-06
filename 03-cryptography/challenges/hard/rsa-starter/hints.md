# Hints (open one at a time)

<details>
<summary>Hint 1 (Modular Exponentiation)</summary>

Don't compute the huge power first. Python's built-in `pow` takes a **third argument**.
</details>

<details>
<summary>Hint 2 (Public Keys)</summary>

Encryption is `c = m^e mod n` with `n = p × q`. It is the same function as Hint 1.
</details>

<details>
<summary>Hint 3 (Euler's Totient)</summary>

For two primes, `φ(n) = (p − 1) × (q − 1)`. No loop needed.
</details>

<details>
<summary>Hint 4 (Private Keys)</summary>

`d` is the number such that `e × d mod φ(n) = 1`. In Python 3.8+, `pow(e, -1, phi)` gives it.
</details>

<details>
<summary>Hint 5 (RSA Decryption)</summary>

Decryption is `m = c^d mod n`. Reuse `d` from the previous task (same `p`, `q`, `e`).
</details>
