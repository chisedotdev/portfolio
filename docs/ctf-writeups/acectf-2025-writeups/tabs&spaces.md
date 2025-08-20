# Tabs\&Spaces

> CATEGORY - STEGANOGRAPHY

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FXvVDaoc9iapqKIKqFS4V%2Fimage.png?alt=media&#x26;token=b04d0f12-056e-4621-914e-9cd3f902e569" alt=""><figcaption></figcaption></figure>

## Introduction

This challenge provides a ZIP file containing multiple files. Our goal is to analyze them and extract a hidden flag, which appears to involve whitespace-based steganography.

## Steps

### Step 1: Extracting and Inspecting the ZIP File

The challenge provides a ZIP archive. After extracting it, we see the following files inside:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F7ozh1h2JCH9XArBpuEYm%2Fimage.png?alt=media&#x26;token=0d35686e-c9ea-4187-bce0-2944f667c30f" alt=""><figcaption></figcaption></figure>

A **Python script** is present, which appears to be for checking file integrity and isn't immediately useful.

### Step 2: Identifying an Anomalous File

Navigating into the `files/` directory, I checked the contents of all files. One file stood out due to its **different color and unusual file extension**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F512ga8rXSrpTBtSwuoHo%2Fimage.png?alt=media&#x26;token=3f9f6954-58f8-4acc-a99c-82c1cd8d0c9d" alt=""><figcaption></figcaption></figure>

To make it easier to work with, I renamed the file to remove the extra `.` in its name.

### Step 3: Initial Steganography Checks

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Ff3dLll1JFXGpkteYxiP3%2Fimage.png?alt=media&#x26;token=57f42ff8-162b-4324-bc97-fb13c7d824b9" alt=""><figcaption></figcaption></figure>

Since the file was a **JPG image**, I performed basic steganography checks:

* **Exiftool** → No interesting metadata found.
* **Steghide (without passphrase)** → Extracted a hidden text file named `whitespace_flag.txt`.

```bash
steghide extract -sf 87.jpg
```

### Step 4: Analyzing `whitespace_flag.txt`

Opening `whitespace_flag.txt` in **Sublime Text**, I noticed that the content wasn't regular text. Instead, it appeared to contain **whitespace-based encoding**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FHygX2DH6qFhKWH6IIPJW%2Fimage.png?alt=media&#x26;token=3a40c572-df37-42dc-a5a2-a84dded570c6" alt=""><figcaption></figcaption></figure>

Searching online for whitespace steganography, I found tools like **stegsnow**. However, `stegsnow` didn't reveal any meaningful text, suggesting that another encoding method was used.

Upon closer inspection, I saw patterns of **tabs (`^I`) and spaces (`␣`)**, which indicated **binary encoding**, where:

* **Tab (`^I`) = 1**
* **Space (`␣`) = 0**

### Step 5: Converting Whitespace to Binary

To decode the message, I used the following command:

```bash
cat whitespace_flag.txt | tr ' ' '0' | tr '\t' '1' | tr -d '\n'
```

This converted the hidden text into a binary string:

```bash
0100000101000011010001010100001101010100010001100111101101101110001100000101111100110011011110000111000000110001001100000011000100110111010111110110111000110000010111110110011100110100001100010110111001111101
```

### Step 6: Converting Binary to Text

For the final step, I converted the binary data to readable text using **Perl**:

```bash
echo "0100000101000011010001010100001101010100010001100111101101101110001100000101111100110011011110000111000000110001001100000011000100110111010111110110111000110000010111110110011100110100001100010110111001111101" | perl -lpe '$_=pack"B*",$_'
```

## FLAG

```
ACECTF{n0_3xp1017_n0_g41n}
```
