# Writeup: Safe Opener

> 🟡 **Verification status: Source-verified.**
> The approach matches public solutions for this picoCTF challenge (checked Nov 2026): the password is built in the code (commonly Base64-encoded) and compared with your input. The author did **not** re-download the challenge file.
> The example below uses our **own** Java-style snippet and a **real** Base64 decode we ran, so no output is invented and no real flag is shown. On the real challenge you recover the actual password/flag.
>
> ⛔ **Spoilers below.** Try the challenge and the [hints](hints.md) first.

**Challenge:** picoGym → Reverse Engineering → *Safe Opener*
**Goal:** find the password the program accepts. Not printed here.

## Step 1: Identify what you were given

```
$ file SafeOpener.class
SafeOpener.class: compiled Java class data, version 55.0
```

- A `.class` is **compiled** Java. If you got a `.java`, skip to Step 3 and just read it.

## Step 2: Decompile (if it is a .class)

- Managed code like Java decompiles almost back to the original source.
- Options: a decompiler site, [dogbolt.org](https://dogbolt.org), or `javap -c -p SafeOpener.class` to read the structure.
- You end up with readable Java.

## Step 3: Find "the check"

Search the source for where your input is compared. It looks like this (our own illustrative snippet):

```java
public boolean openSafe(String password) {
    String encoded = "cGwzYXNlX2wzdF9tM18xbg==";   // suspicious: Base64?
    String expected = decode(encoded);
    if (password.equals(expected)) {               // <-- the check
        System.out.println("Opened!");
        return true;
    }
    return false;
}
```

- The important line is the `equals`: it compares your input to `expected`.
- Notice `expected` is **not** a plain word — it is decoded from a Base64-looking string.

## Step 4: Recover the expected value

- The string ends with `==`, a Base64 giveaway. Decode it (real run):
  ```
  $ echo 'cGwzYXNlX2wzdF9tM18xbg==' | base64 -d
  pl3ase_l3t_m3_1n
  ```
- **Meaning:** `pl3ase_l3t_m3_1n` is the password the safe accepts. On the real challenge, the decoded value is the flag (or the password that reveals it). Submit exactly what you recover.

## What you learned

| Idea | Lesson |
|---|---|
| `file` | Tells you it is Java → decompilable |
| The check | The `equals`/`==` line holds the secret comparison |
| Built secrets | Passwords are often encoded, not plain |
| Base64 | A `==` ending is the tell; decode it |

*بالدارجة: الباسورد ما كانش مكتوب نيشان، كان Base64. لقينا سطر المقارنة (`equals`)، فكّينا الـ Base64، وطلعات الكلمة اللي كيقبلها البرنامج.*

**Next:** [Medium challenge →](../../medium/gdb-test-drive/README.md)
