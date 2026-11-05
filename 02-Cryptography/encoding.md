# Cryptographic Encoding & Decoding: ASCII and Hexadecimal XOR Analysis

## Platform & Metadata

| Field | Details |
| :--- | :--- |
| **Platform** | [CryptoHack](https://cryptohack.org/) |
| **Category** | Introduction to CryptoHack — Encoding & Symmetric XOR |
| **Challenges Covered** | 1. **ASCII** (`5 pts`)<br>2. **You either know, XOR you don't** (`30 pts`) |
| **Difficulty** | Beginner |
| **Tools Used** | Python 3 (`chr()`, `ord()`, `bytes.fromhex()`, `.encode()`), Ubuntu WSL Terminal, GNU Nano |

> **Warning:** All cryptographic exercises and scripts documented in this guide were performed exclusively on challenge data from the authorized **CryptoHack** training platform.

---

## Objective

Understand how character and byte **encoding** schemes (`ASCII` and `Hexadecimal`) represent data in computer systems, distinguish **encoding** from **encryption** and **hashing**, and use Python to decode encoded ciphertexts and recover hidden flags.

---

## Prerequisites

- An active account on [CryptoHack](https://cryptohack.org/).
- A Linux command-line environment (Ubuntu on WSL) with `python3` installed.
- Familiarity with basic data representations (integers, hexadecimal strings, ASCII characters, and raw bytes).

---

## Concept Overview

### Encoding vs. Encryption vs. Hashing

A foundational principle in cybersecurity is distinguishing between **encoding**, **encryption**, and **hashing**:

| Operation | Purpose | Secret Key Required? | Reversible? | Examples |
| :--- | :--- | :--- | :--- | :--- |
| **Encoding** | Transforms data from one publicly known format into another for transport, storage, or usability. Provides **no confidentiality**. | No | Yes (anyone can decode using the standard algorithm) | `ASCII`, `Hexadecimal` (Base16), `Base64`, `UTF-8` |
| **Encryption** | Transforms plaintext into ciphertext using a cryptographic algorithm and a secret key to protect **confidentiality**. | Yes | Yes (only with the correct decryption key) | `AES`, `RSA`, Repeating-Key `XOR` |
| **Hashing** | Maps data of arbitrary size to a fixed-length digest using a one-way mathematical function to verify **integrity**. | No | No (one-way function) | `SHA-256`, `SHA-3`, `bcrypt` |

In cryptographic challenges, encrypted ciphertexts are frequently **encoded** as hexadecimal strings or integer arrays so they can be safely displayed and copied as printable text before being decoded back into raw bytes for decryption.

---

## Part 1: ASCII Integer Encoding Challenge

### Challenge Overview
**ASCII** (*American Standard Code for Information Interchange*) is a 7-bit character encoding standard that represents text characters using integers from `0` to `127`.

In the CryptoHack **ASCII** (`5 pts`) challenge, an array of 23 decimal integers is provided. The goal is to convert each integer into its corresponding ASCII character to reveal the flag.

![CryptoHack Encoding Section — ASCII Challenge Prompt](./screenshots/Screenshot%202026-11-05%20091547.png)

### Given Integer Array

```python
[99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
```

### Methodology & Solution
1. In Python, the built-in `chr()` function converts an ASCII ordinal integer (such as `99`) into its corresponding character (`'c'`), while `ord()` performs the reverse operation.
2. Iterate through the integer list using a Python list comprehension and join the resulting characters into a single string:

   ```python
   ascii_values = [
       99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73,
       95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125
   ]

   flag = "".join(chr(value) for value in ascii_values)
   print(flag)
   ```

3. Executing the conversion maps the integers directly to the ASCII flag:

   ```text
   crypto{ASCII_pr1nt4bl3}
   ```

![Solved ASCII Encoding Challenge on CryptoHack](./screenshots/Screenshot%202026-11-05%20091537.png)

---

## Part 2: Hexadecimal Decoding & Known-Plaintext XOR ("You either know, XOR you don't")

### Challenge Overview
In the **You either know, XOR you don't** (`30 pts`) challenge, the flag has been encrypted using a repeating-key **XOR** (*Exclusive OR*) operation with an unknown secret key and then **encoded** as a hexadecimal string:

```text
0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104
```

> **Challenge Hint:** *"Remember the flag format and how it might help you in this challenge!"*

![CryptoHack Challenge — You either know, XOR you don't](./screenshots/Screenshot%202026-11-05%20091158.png)

### Methodology & Step-by-Step Walkthrough

#### 1. Decode Hexadecimal Ciphertext to Raw Bytes
Before any cryptographic operation can be performed, the hexadecimal string must be **decoded** into raw bytes using `bytes.fromhex()`. Each pair of hex digits (such as `0e`) represents a single byte (`0x0e` = `14`).

#### 2. Deduce the Secret Key via Known-Plaintext Analysis
1. Standard CryptoHack flags always begin with the 7-character prefix `crypto{` and end with `}`.
2. Because XOR is both **commutative** and **self-inverse** ($P \oplus K = C \implies C \oplus P = K$), XORing the first 7 bytes of the ciphertext (`0e0b213f26041e`) with the known ASCII bytes of `crypto{` reveals the first 7 bytes of the key:
   - `0x0e ^ ord('c')` $\rightarrow$ `'m'`
   - `0x0b ^ ord('r')` $\rightarrow$ `'y'`
   - `0x21 ^ ord('y')` $\rightarrow$ `'X'`
   - `0x3f ^ ord('p')` $\rightarrow$ `'O'`
   - `0x26 ^ ord('t')` $\rightarrow$ `'R'`
   - `0x04 ^ ord('o')` $\rightarrow$ `'k'`
   - `0x1e ^ ord('{')` $\rightarrow$ `'e'`
3. This yields `"myXORke"`. Completing the English word (or XORing the final byte with `}`) confirms the full 8-byte repeating secret key is:

   ```text
   myXORkey
   ```

#### 3. Write and Execute the Python Decryption Script (`decod.py`)
1. Open the terminal and create a Python script named `decod.py` using `nano`:

   ```bash
   nano decod.py
   ```

2. Implement `xor_decrypt()` to decode the hex string into bytes, encode the secret key string into bytes, apply repeating-key XOR across the ciphertext, and decode the resulting bytes back into readable ASCII text:

   ```python
   def xor_decrypt(hex_ciphertext, key_str):
       # Convert hex string to raw bytes
       ciphertext = bytes.fromhex(hex_ciphertext)
       # Convert key string to bytes
       key = key_str.encode()

       # Perform repeating-key XOR
       decrypted = bytes([c ^ key[i % len(key)] for i, c in enumerate(ciphertext)])
       return decrypted.decode(errors='ignore')

   # Given ciphertext and the deduced key
   hex_str = "0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104"
   secret_key = "myXORkey"

   # Decrypt and print the flag
   flag = xor_decrypt(hex_str, secret_key)
   print(f"Flag: {flag}")
   ```

   ![Writing the decod.py Script in GNU Nano](./screenshots/Screenshot%202026-11-05%20091034.png)

3. Run the script in the Ubuntu terminal:

   ```bash
   python3 decod.py
   ```

   ![Executing python3 decod.py in the Terminal](./screenshots/Screenshot%202026-11-05%20091006.png)

---

## Findings & Evidence

### Terminal Output

```text
(.venv) cyberflex@DESKTOP-CYBERFLEX:~/Desk$ python3 decod.py
Flag: crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}
```

![Terminal Output Showing the Decrypted Flag](./screenshots/Screenshot%202026-11-05%20091055.png)

### Captured Flags Summary

| Challenge | Method Used | Captured Flag |
| :--- | :--- | :--- |
| **ASCII** (`5 pts`) | Decimal integer to ASCII decoding (`chr()`) | `crypto{ASCII_pr1nt4bl3}` |
| **You either know, XOR you don't** (`30 pts`) | Hex decoding (`bytes.fromhex()`) + Known-plaintext repeating-key XOR (`myXORkey`) | `crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}` |

---

## Security Takeaways

1. **Encoding Is Not Encryption:** Converting data into ASCII ordinal numbers or hexadecimal strings (`0e0b21...`) only changes its representation. Anyone can reverse encoding immediately without a key.
2. **Short Repeating XOR Keys Are Vulnerable to Known-Plaintext Attacks:** When a short secret key (`myXORkey`) is repeated across a message, knowing or guessing just a few bytes of the plaintext (such as a standard file header or the `crypto{` flag prefix) immediately exposes the key and compromises the entire message.

---

## Learning Outcomes

- Distinguished between **encoding** (reversible format conversion without a key) and **encryption** (keyed transformation for confidentiality).
- Used Python's `chr()`, `bytes.fromhex()`, and `.encode()` functions to convert between integer arrays, hexadecimal strings, raw byte arrays, and ASCII text.
- Executed a known-plaintext attack against a repeating-key XOR cipher by leveraging the predictable `crypto{...}` flag structure.
