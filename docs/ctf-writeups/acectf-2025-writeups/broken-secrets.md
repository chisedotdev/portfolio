# Broken Secrets

> CATEGORY - FORENSICS

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FxgkDHmikreql7R0XSDkN%2Fimage.png?alt=media&#x26;token=5aab9956-a7b6-406f-926d-658ea83d5d86" alt=""><figcaption></figcaption></figure>

A file is attached to the challenge.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F4A8p9eExuqqUSwMGQMys%2Fimage.png?alt=media&#x26;token=5e93ea50-58d7-4d1f-a714-fc7301a8cf5f" alt=""><figcaption></figcaption></figure>

## Introduction

This challenge provides a suspicious file that needs to be analyzed to extract a hidden flag. By investigating its structure, identifying corruption, and repairing it, we can uncover the secret message.

## Steps

### Step 1: Extracting and Searching for the Flag

After extracting the file, I navigated into the directory and ran a quick check using `cat` and `grep` to search for a possible flag.

```bash
find . -type f -exec cat {} \; | grep -a -i 'acectf'
```

However, this yielded no results, meaning the flag could be hidden, encrypted, or embedded elsewhere.

### Step 2: Exploring the Directory Structure

The `word` directory looked interesting, so I navigated into it to investigate further.

Finding nothing useful there, I decided to explore the `media` directory, as media files often contain hidden data.

### Step 3: Analyzing the Suspicious File

Inside `media`, I found a file that caught my attention. Running a few tests revealed that it might be a PNG file due to the presence of the `IHDR` chunk, a key indicator of PNG format.\


<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FQWlaxpMdgOAXP9jY6f0h%2Fimage.png?alt=media&#x26;token=b2994518-3d2e-4fb4-b89b-0eb9f176cf3a" alt=""><figcaption></figcaption></figure>

However, there was a problem. Attempting to copy and rename the file to a `.png` extension didn’t work. I then tried using `convert`:

```bash
convert not_so_suspicious_file file.png
```

But this still resulted in an error. A quick Google search led me to suspect a corrupted file header.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fl9I5EqNUk08rx4raFNFK%2Fimage.png?alt=media&#x26;token=83879482-09cd-45e7-8ebb-6f909554de3e" alt=""><figcaption></figcaption></figure>

### Step 4: Identifying the Header Issue

The expected PNG file header should be:

```bash
89 50 4E 47 0D 0A 1A 0A
```

However, checking the file’s actual header revealed:

```bash
12 2E D4 A7 0D 0A 1A 0A
```

This confirmed that the first four bytes of the header were incorrect.

### Step 5: Fixing the Corrupted PNG Header

To repair the file, I replaced the incorrect bytes with the correct PNG signature using the `dd` command:

```bash
printf '\x89PNG' | dd of=file.png bs=1 seek=0 count=4 conv=notrunc
```

This successfully restored the image.

### Step 6: Extracting the Flag

Opening the repaired image revealed the hidden flag:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FsqQu1hJXoLvQRIfpLWjA%2Fimage.png?alt=media&#x26;token=72b4b263-c008-404f-aeac-0f5d9486857b" alt=""><figcaption></figcaption></figure>

## FLAG

```
ACECTF{h34d3r_15_k3y}
```
