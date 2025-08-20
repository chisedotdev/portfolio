# Van Gogh's GARBAGE hunt

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FDoTCSS5MGOEvmKXhwwl4%2FPasted%20image%2020250308203808.png?alt=media&#x26;token=b9afe9f4-d745-4654-86aa-7dbe6a7f08a7" alt=""><figcaption></figcaption></figure>

## Introduction

Helga, a maid working at Mr. X’s mansion, made a **huge mistake**—she unknowingly gave away his **gold jewelry** along with some old clothes. Now, she has **no idea** which textile collection point she left them at.

Our job? **Track down the exact shop** where the jewelry ended up and retrieve the flag.

***

## Step by Step Solution

### Step 1: Inspecting the Given File

The challenge provided a file: `vangogh.zip`. Unzipping it gave me a single image file:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FvZbCKWtdcHNcJs2aSMZZ%2FPasted%20image%2020250308211149.png?alt=media&#x26;token=8ac1801c-c583-4902-966d-087b10aab6db" alt=""><figcaption></figcaption></figure>

I started by checking the metadata using `exiftool`.

```
exiftool chall.jpeg
```

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FJn8M8csoloqaJBLpBrCP%2FPasted%20image%2020250308212049.png?alt=media&#x26;token=5ffe59f2-8c85-41f3-bf01-d88956d00d78" alt=""><figcaption></figcaption></figure>

The **comment field** contained something that looked like **Base64-encoded text**.

### Step 2: Decoding the Hidden String

The extracted Base64 string was:

```
SnVzdGFub3JtYTgxODYx
```

I decoded it using:

```sh
echo "SnVzdGFub3JtYTgxODYx" | base64 -d
```

Which gave me:

```
Justanorma81861
```

Looks like a username.

### Step 3: Investigating the Username

I used `sherlock` to find where this username exists online.

```
sherlock Justanorma81861
```

```
https://freelance.habr.com/freelancers/Justanorma81861
https://gitlab.gnome.org/Justanorma81861
https://nationstates.net/nation=Justanorma81861
https://nationstates.net/region=Justanorma81861
https://torrentgalaxy.to/profile/Justanorma81861
https://x.com/Justanorma81861
Total Websites Username Detected On : 7
```

The **X (Twitter) account** stood out, so I checked it.

### Step 4: Checking the X account

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FPMZVpdgXb40pEJ8pDcIH%2FPasted%20image%2020250308212511.png?alt=media&#x26;token=34b9f7cf-c25f-43b4-bc9c-871f1fd55d5e" alt=""><figcaption></figcaption></figure>

The profile had only **two tweets**. One contained another **Base64-encoded string**:

```
QjQ6NUQ6NTA6QUE6ODY6NDE=
```

I decoded it:

```sh
echo "QjQ6NUQ6NTA6QUE6ODY6NDE=" | base64 -d
```

Result:

```
B4:5D:50:AA:86:41
```

This looked like a **BSSID (Wi-Fi MAC address)**.

### Step 5: Searching for the BSSID

I searched for the **BSSID** on `wigle.net` to get its location.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FKQhfZzlzgcHKbdfqZHsj%2FPasted%20image%2020250308212851.png?alt=media&#x26;token=67f83de5-9d4f-45ce-8ef5-71873ada4e06" alt=""><figcaption></figcaption></figure>

It pointed to **His Majesty’s Theatre**, so I checked Google Maps.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FQ1BM7HoO0WVO1tB0Scsc%2FPasted%20image%2020250308213525.png?alt=media&#x26;token=a070584e-37e3-4f3e-b36a-821c652c08bb" alt=""><figcaption></figcaption></figure>

The location didn’t seem right. I decided to try **reverse image searching** the original `chall.jpeg`.

### Step 6: Reverse Image Search

I uploaded `chall.jpeg` to **Google Lens** and found a **match**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FpShpPcyZA9VyYgsIRECr%2FPasted%20image%2020250308213852.png?alt=media&#x26;token=3c11d3f0-5262-4a5b-9962-f2ef87648cc1" alt=""><figcaption></figcaption></figure>

Clicking the **third link** gave me this address:

```
Buiten Oranjestraat 14-A
```

I looked it up on Google Maps.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FgyFdOE0nwHCsyV8chzCR%2FPasted%20image%2020250308214543.png?alt=media&#x26;token=2570251b-fa94-4f2c-887d-f200ec39796a" alt=""><figcaption></figcaption></figure>

### Step 7: Identifying the Shop

From the challenge description:

> _Helga, a maid at Mr. X’s mansion, mistakenly gave away his gold jewelry to some textile collection point along with a pile of old clothes thinking they were GARBAGE._

The clue pointed to a **textile collection point**.

There was a **store nearby called "The Swapshop"**, which fit perfectly.

***

## FLAG

```
pearl{the_swapshop}
```