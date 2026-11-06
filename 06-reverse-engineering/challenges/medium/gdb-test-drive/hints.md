# Hints (open one at a time)

<details>
<summary>Hint 1</summary>

Running the program normally "works" but is painfully slow on purpose. A debugger lets you control execution instead of waiting.
</details>

<details>
<summary>Hint 2</summary>

Start it with `gdb ./the_binary`. Use `info functions` to see what functions exist. The picoCTF page gives you the exact commands to follow — this challenge is a guided GDB tour.
</details>

<details>
<summary>Hint 3</summary>

Set a breakpoint (`break main`), then `run`. The program pauses so you can look around instead of sitting through the delay.
</details>

<details>
<summary>Hint 4</summary>

Follow the challenge's GDB commands to jump past the sleep (for example by continuing, or by setting the instruction pointer forward). Once execution reaches the print, the flag is shown.
</details>
