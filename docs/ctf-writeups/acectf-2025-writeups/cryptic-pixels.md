# Cryptic Pixels

> CATEGORY - STEGANOGRAPHY

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FrRtW1eblP4m7Iy4u79iw%2Fimage.png?alt=media&#x26;token=d3f6c1b9-685e-4098-a9ab-f136f9617178" alt=""><figcaption></figcaption></figure>

## Introduction

In this challenge, we are given an image file that likely contains hidden data. Using steganography techniques, we extract and decipher the hidden message to reveal the flag.

## Steps

### Step 1: Initial File Analysis

The challenge provides a PNG file.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FFDuUqVWabldWAZgjYxEu%2Fimage.png?alt=media&#x26;token=16baf69c-ea41-4246-a823-8a32b9e8db86" alt=""><figcaption></figcaption></figure>

To check for metadata, I used `exiftool`, but nothing interesting was found.

### Step 2: Verifying File Integrity

To ensure the file was actually a PNG and not something else in disguise, I used `xxd`:

```bash
xxd CrypticPixels.png | head
```

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fv4I60aug66fcJjsFnT6u%2Fimage.png?alt=media&#x26;token=f69f7bff-5391-4141-b3eb-b548ade280f7" alt=""><figcaption></figcaption></figure>

This revealed that the file contained a hidden `flag.txt` inside.

### Step 3: Extracting Hidden Data

Since the file seemed to contain embedded data, I used `binwalk` to extract it:

```bash
binwalk -e CryticPixels.png
```

This extracted a ZIP archive, but it was password-protected.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FSiqe8sWMdgs1LiejtarE%2Fimage.png?alt=media&#x26;token=75f44e11-11cb-41df-b691-bfb49923fff5" alt=""><figcaption></figcaption></figure>

### Step 4: Cracking the ZIP Password

To crack the ZIP password, I used `fcrackzip` with the `rockyou.txt` wordlist:

```bash
fcrackzip -u -D -p /usr/share/wordlists/rockyou.txt B8103.zip
```

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FcKzgOXBuQBr8KRkA21sN%2Fimage.png?alt=media&#x26;token=a8c66a12-c8ad-4ffd-9c60-7a9073aa04ef" alt=""><figcaption></figcaption></figure>

Password: `qwertyuiop`

### Step 5: Analyzing the Flag

After extracting `flag.txt`, the flag appeared scrambled, suggesting it had been encoded or ciphered.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FK6X6DWZtG2M8XagX6rX2%2Fimage.png?alt=media&#x26;token=d68f28a6-3184-4100-bc9c-aa2c082f249e" alt=""><figcaption></figcaption></figure>

I attempted common ROT ciphers (`ROT5, ROT13, ROT18, ROT47`), but none worked.

### Step 6: Deciphering with a Caesar Cipher

Since ROT didn't work, I tried a **Caesar cipher** with shifts from **1 to 9** until I found the correct shift.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F4nMUWQqQilLMxbPI1ZVi%2Fimage.png?alt=media&#x26;token=264f3c41-05d9-473a-838a-f5d301f52815" alt=""><figcaption></figcaption></figure>

## FLAG

```
ACECTF{h4h4_y0u'r3_5m4r7}
```
