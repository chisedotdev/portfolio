# SentMail

> CATEGORY - FORENSICS

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FEa27gyrnzNLySprgQqUR%2FPasted%20image%2020250308005652.png?alt=media&#x26;token=178e5c14-06e1-4ecf-a617-f899935abaed" alt=""><figcaption></figcaption></figure>

## Introduction

Vortex prefers simplicity, but iamgreedy. I want more—(text & background), they don’t tell the whole story. Have you checked the footer? And don't forget, there's something unique about the file name. It might just be the key.

***

## Step by Step Solution

### Step 1: Checking Metadata

Since this is a PDF file, I started with some basic forensic techniques. The first tool I used was `exiftool` to extract metadata.

<pre class="language-sh"><code class="lang-sh"><strong>exiftool sentmail.pdf
</strong></code></pre>

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FG2ID4EtmzeFC7lMGJ8h3%2FPasted%20image%2020250308010020.png?alt=media&#x26;token=b29e8767-415a-4b7c-b6f4-63ef46ad8b89" alt=""><figcaption></figcaption></figure>

Unfortunately, nothing useful was found.

### Step 2: Inspecting the PDF in a Browser

Next, I opened the PDF in my browser and carefully examined it. The challenge description suggested looking at the footer. Translating the Morse code in the footer revealed a YouTube link, but the link was expired.

To retrieve the original content, I used the Wayback Machine. The archived link led to a **Rickroll**. Classic.

### Step 3: Extracting Hidden Text

Since the PDF allowed highlighting invisible text, I suspected hidden content. Copying and pasting the text revealed two hidden messages:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FLfAbF5XimBP65kfLG24g%2FPasted%20image%2020250308010308.png?alt=media&#x26;token=7854a0ed-51a9-4c4b-a3f0-fcec1dce3720" alt=""><figcaption></figcaption></figure>

#### First Hidden Message

```
Science ReportLorem ipsum dolor sit amet, consectetuer adipiscing elit
SixEight SevenFour SevenFour SevenZero SevenThree Threea Twof Twof SevenNine
Sixf SevenFive SevenFour SevenFive Twoe SixTwo SixFive Twof SevenEight SevenSix
FourSix Fivea Sixa Sixf ThreeFive FiveZero SixSeven FourSeven ThreeZero
```

#### Second Hidden Message

```
*##*#****###*#***###*#***###*****###**##**###*#***#*####**#*####*####**#*
##*####*###*#*#*###*#***###*#*#**#*###**##***#**##**#*#**#*####*####****
###*##**#***##**#*##*#**##*#*#**##*####**##*#*#*#*#*****##**###*#***###**#
#****
```

#### Decoding the Messages

* The first message was a **hexadecimal string** that, when translated, revealed the same **Rickroll YouTube link**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F5fazD2l5E2AweZYQlr97%2FPasted%20image%2020250308011232.png?alt=media&#x26;token=b904df6b-0695-4019-bd16-941667f3caea" alt=""><figcaption></figcaption></figure>

*   The second message was **binary encoded using `* = 0` and `# = 1`**. Once decoded, it also pointed to the **Rickroll link**.



<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F8AmelMWJfPPzq9cYi2k8%2FPasted%20image%2020250308011434.png?alt=media&#x26;token=2f2aec38-a455-41da-8a2f-83bbe30dbb39" alt=""><figcaption></figcaption></figure>

At this point, it was clear that the PDF was full of distractions. Time to dig deeper.

### Step 4: Analyzing the PDF Structure

To check for any hidden content or embedded files, I used `pdf-parser`.

```sh
pdf-parser sentmail.pdf
```

Scrolling through the results, I found an interesting reference:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fd0S774CAXrKUAqlXheKj%2FPasted%20image%2020250308011823.png?alt=media&#x26;token=6cbf8d8b-70d4-4c6e-b420-e5b063a11c83" alt=""><figcaption></figcaption></figure>

It showed **`flag.txt`** embedded in object **3 0 R**.

### Step 5: Extracting the Flag

Since `flag.txt` was stored within object 3, I extracted it using:

```sh
pdf-parser sentmail.pdf -o 3 -f -d flag.txt
```

After extraction:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FrdVKftP92RdStjGXj7uf%2FPasted%20image%2020250308012528.png?alt=media&#x26;token=1790eee8-3f52-46f1-a779-5b6068751d13" alt=""><figcaption></figcaption></figure>

The extracted file contained the final flag!

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FvN97bbmwUFyTcm17kFX8%2FPasted%20image%2020250308012547.png?alt=media&#x26;token=4dae2e0c-f8bb-47a4-8093-3e8377c14383" alt=""><figcaption></figcaption></figure>

***

## FLAG

```
pearl{I_N3v3r_Kn3w_PDF5_Att4ch}
```
