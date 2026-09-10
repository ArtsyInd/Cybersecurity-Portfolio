# Linux Cryptography Lab — Caesar Cipher & File Decryption

> **Cybersecurity Portfolio Project**  
> **Category:** Cryptography | Linux | Bash | Data Protection  
> **Environment:** Linux shell (`analyst` user)  
> **Skills Demonstrated:** Linux command line, hidden-file discovery, Caesar cipher decryption, text transformation, OpenSSL, AES-256-CBC decryption, encrypted-file recovery

---

## Project Overview

This lab provided hands-on practice with basic cryptography and Linux command-line tools. I investigated an encrypted home directory, discovered a hidden file containing instructions, decoded a Caesar cipher, and used the recovered information to decrypt an AES-256-CBC encrypted file.

The exercise demonstrates how encryption protects information and how security analysts can use appropriate tools and commands to recover authorized data when the required key or password is available.

---

# Scenario

All files in the user's home directory had been encrypted. My objective was to:

1. Explore the home directory.
2. Read the provided instructions.
3. Locate a hidden file in the `caesar` directory.
4. Decrypt the Caesar cipher contained in the hidden file.
5. Use the recovered command and password to decrypt `Q1.encrypted`.
6. Verify the recovered data by reading `Q1.recovered`.

The lab started with the `analyst` user in:

```text
/home/analyst
```

---

# Task 1 — Explore the Home Directory

## 1. List the Files

### Command

```bash
ls
```

### Output

```text
Q1.encrypted  README.txt  caesar
```

### Explanation

The `ls` command lists the contents of the current working directory. The output showed:

- `Q1.encrypted` — the encrypted data file
- `README.txt` — the file containing the initial instructions
- `caesar` — the directory containing the hidden Caesar cipher file

---

## 2. Read the Instructions

### Command

```bash
cat README.txt
```

### Result

The README explained that the `caesar` subdirectory contained a hidden file that needed to be discovered and decoded before the encrypted data could be recovered.

### Security Relevance

Reading system and application files is a common task for security analysts during investigations. The `cat` command provides a simple way to inspect text-based files directly from the Linux shell.

---

# Task 2 — Find and Decrypt the Hidden Caesar Cipher

## 1. Navigate to the Caesar Directory

### Command

```bash
cd caesar
```

### Explanation

The `cd` command changes the current working directory. This moved the investigation into the `caesar` directory identified by the README.

---

## 2. List Hidden Files

### Command

```bash
ls -a
```

### Output

```text
.  ..  .leftShift3
```

### Explanation

The `-a` option tells `ls` to display **all files**, including hidden files.

In Linux, files whose names begin with a period (`.`) are treated as hidden files by default.

The important file discovered was:

```text
.leftShift3
```

---

## 3. Read the Hidden File

### Command

```bash
cat .leftShift3
```

### Result

The file contained text that appeared scrambled. The message had been encrypted using a **Caesar cipher with a shift of three characters**.

A Caesar cipher substitutes each alphabetic character with another character a fixed number of positions away in the alphabet.

For a three-character left shift during decryption:

```text
d → a
e → b
f → c
```

The same transformation applies to uppercase letters.

---

## 4. Decode the Caesar Cipher

### Command

```bash
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```

### Explanation

The `tr` command translates characters from one character set to another.

The command maps:

```text
d-za-c → a-z
D-ZA-C → A-Z
```

This effectively shifts alphabetic characters three positions to the left, reversing the Caesar cipher.

The pipe (`|`) sends the output of:

```bash
cat .leftShift3
```

directly into:

```bash
tr "d-za-cD-ZA-C" "a-zA-Z"
```

The decoded output revealed the OpenSSL command and password required to decrypt the encrypted data file.

---

## Caesar Cipher Concept

### Encryption

A Caesar cipher shifts characters by a fixed number of positions.

For example, with a shift of three:

```text
a → d
b → e
c → f
```

### Decryption

The reverse operation shifts the characters back:

```text
d → a
e → b
f → c
```

The lab used a three-character shift.

---

# Task 3 — Decrypt the Encrypted File

After decoding `.leftShift3`, the recovered instructions provided the following OpenSSL command:

### Command

```bash
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```

---

## Command Breakdown

| Component | Purpose |
|---|---|
| `openssl` | OpenSSL cryptographic toolkit |
| `aes-256-cbc` | AES-256 encryption using CBC mode |
| `-pbkdf2` | Uses PBKDF2 for password-based key derivation |
| `-a` | Processes Base64-encoded data |
| `-d` | Specifies decryption |
| `-in Q1.encrypted` | Specifies the encrypted input file |
| `-out Q1.recovered` | Specifies the recovered output file |
| `-k ettubrute` | Provides the password used for decryption |

---

## AES-256-CBC

**AES** stands for Advanced Encryption Standard.

`AES-256` indicates that the cipher uses a 256-bit key.

`CBC` stands for **Cipher Block Chaining**, a block-cipher mode in which each plaintext block is combined with the previous ciphertext block before encryption.

In this lab, OpenSSL was used to reverse the encryption because the required password was recovered from the decoded hidden file.

---

## PBKDF2

The command includes:

```bash
-pbkdf2
```

PBKDF2 (**Password-Based Key Derivation Function 2**) strengthens password-based encryption by deriving a cryptographic key from a password through repeated computation.

This makes password guessing more computationally expensive than using a password directly as an encryption key.

---

## Base64 Encoding

The command also contains:

```bash
-a
```

This tells OpenSSL to process the encrypted data using Base64 encoding/decoding.

Base64 is an **encoding mechanism**, not encryption. It allows binary data to be represented as printable characters.

---

# Verify the Recovered File

After running the OpenSSL command, I listed the directory contents.

### Command

```bash
ls
```

### Output

```text
Q1.encrypted  Q1.recovered  README.txt  caesar
```

The new file:

```text
Q1.recovered
```

confirmed that the encrypted data had been successfully decrypted into a separate output file.

---

## Read the Recovered Data

### Command

```bash
cat Q1.recovered
```

### Result

The recovered message confirmed that the encrypted file had been successfully decrypted and that the Caesar cipher exercise had been completed.

The lab output stated:

> If you are able to read this, then you have successfully decrypted the classic cipher text. You recovered the encryption key that was used to encrypt this file. Great work!

---

# Evidence from Lab Execution

The completed lab demonstrated the following command sequence:

```bash
ls
cat README.txt
cd caesar
ls -a
cat .leftShift3
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
cd ~
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
ls
cat Q1.recovered
```

---

# Investigation Workflow

```text
/home/analyst
     |
     v
     ls
     |
     v
Read README.txt
     |
     v
Navigate to caesar/
     |
     v
     ls -a
     |
     v
Find .leftShift3
     |
     v
Decode Caesar Cipher
     |
     v
Recover OpenSSL command
     |
     v
Decrypt Q1.encrypted
     |
     v
Create Q1.recovered
     |
     v
Read recovered message
```

---

# Security Concepts Demonstrated

## 1. Encryption vs. Encoding

Encryption protects confidentiality by transforming data using a cryptographic algorithm and key.

Encoding, such as Base64, only changes the representation of data and does not provide confidentiality.

---

## 2. Symmetric Encryption

AES is a **symmetric encryption algorithm**, meaning the same secret key is used to encrypt and decrypt the data.

The simplified process is:

```text
Plaintext
    |
    v
AES-256 Encryption + Key
    |
    v
Ciphertext
    |
    v
AES-256 Decryption + Key
    |
    v
Plaintext
```

---

## 3. Key and Password Recovery

The lab demonstrated that recovering the correct password or cryptographic key is necessary to decrypt protected information.

In the exercise, the password was not directly provided at the beginning. It was obtained by following the investigation path and decoding the hidden Caesar cipher.

---

## 4. Hidden Files in Linux

Linux hidden files commonly begin with:

```text
.
```

For example:

```text
.leftShift3
```

The standard `ls` command does not display these files, while:

```bash
ls -a
```

does.

---

## 5. Command-Line Pipelines

The command:

```bash
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```

demonstrates a Linux pipeline.

The output of one command becomes the input of another:

```text
cat
 |
 v
tr
 |
 v
Decoded text
```

Pipelines are useful for combining simple command-line utilities into efficient data-processing workflows.

---

# Why This Matters in Cybersecurity

Encryption is an important security control for protecting sensitive information both at rest and in transit. Security analysts should understand common cryptographic concepts and be able to recognize how encryption, encoding, key derivation, and decryption tools are used during security operations.

This lab also demonstrates practical Linux skills that are relevant to security analysis, including file discovery, hidden-file identification, command pipelines, and working with cryptographic utilities.

---

# Tools Used

| Tool | Purpose |
|---|---|
| Linux Bash shell | Command-line investigation |
| `ls` | List directory contents |
| `ls -a` | Display hidden files |
| `cat` | Read text files |
| `cd` | Navigate directories |
| `tr` | Translate characters and decode the Caesar cipher |
| OpenSSL | Perform AES-256-CBC decryption |
| AES-256-CBC | Symmetric cryptographic algorithm used in the exercise |
| PBKDF2 | Password-based key derivation |

---

# Key Takeaways

- Hidden Linux files can be identified using `ls -a`.
- The `cat` command can be used to inspect text files.
- The `tr` command can perform character substitution and was used to reverse the Caesar cipher.
- Caesar ciphers use fixed character shifts and provide only very weak historical cryptographic protection.
- AES-256 is a modern symmetric encryption algorithm.
- CBC is a block-cipher mode of operation.
- PBKDF2 strengthens password-based key derivation.
- Base64 is encoding rather than encryption.
- OpenSSL provides command-line tools for cryptographic operations.
- Secure decryption requires access to the appropriate key or password.

---

# Portfolio Summary

In this Linux cryptography lab, I investigated an encrypted file system by following a sequence of clues and using Bash commands to recover protected data. I discovered a hidden file, decoded a three-character Caesar cipher with `tr`, and used the recovered OpenSSL command to decrypt an AES-256-CBC encrypted file. The exercise strengthened my understanding of encryption, symmetric cryptography, PBKDF2, Base64 encoding, hidden Linux files, and command-line security operations.

---

## Lab Evidence

Screenshots from the completed lab can be added below to demonstrate hands-on execution.

### Discovering the Hidden File

![Finding the hidden Caesar cipher file](screenshots/hidden-file.png)

### Decrypting the Caesar Cipher

![Decoding the Caesar cipher](screenshots/caesar-decryption.png)

### Decrypting the AES-256 File

![Decrypting Q1.encrypted](screenshots/openssl-decryption.png)

### Reading the Recovered Data

![Reading Q1.recovered](screenshots/recovered-file.png)

> **Note:** Replace the image paths above with the actual screenshot filenames when adding your lab evidence to GitHub.
