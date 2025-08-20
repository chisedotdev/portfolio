# Somewhere in Space

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FIIo0HRBI3M1dcBA36km7%2FPasted%20image%2020250412215127.png?alt=media&#x26;token=fb0b80eb-270b-435c-a917-59da4a363d5d" alt=""><figcaption></figcaption></figure>

### Challenge Description

> This handsome man is looking at a beautiful woman.
>
> The flag is a filename in which the woman's face is stored. Use only characters that are at least 90% visible.
>
> **Flag format:** `1753c{filename}`

***

### Provided Image

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fd9QaFOm9YVQY1hDuH2Lj%2FPasted%20image%2020250412215218.png?alt=media&#x26;token=85ae4823-1f1f-44b0-902c-7982f4ee7328" alt=""><figcaption></figcaption></figure>

***

### Step 1: EXIF Metadata

I ran `exiftool` to inspect any metadata that might help.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F4GrwA5GnxgmR8HCz8FKJ%2FPasted%20image%2020250412215401.png?alt=media&#x26;token=861e1089-56ad-4978-a2c3-b2ac904b92ba" alt=""><figcaption></figcaption></figure>

Nothing particularly useful stood out in the metadata.

***

### Step 2: Reverse Image Search

Next, I turned to **Google Image Search**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FbaMGATO5VT5Rn6qx4LlS%2FPasted%20image%2020250412215631.png?alt=media&#x26;token=9bfcf0f5-ffba-4cf1-a0e0-e207930f3f76" alt=""><figcaption></figcaption></figure>

Among the results, two sites stood out — Facebook and Vagabundler. I went ahead and explored the Vagabundler page.

🔗 [Vagabundler Street Art - Agiou Andreou 253](https://vagabundler.com/cyprus/streetart-map-limassol/agiou-andreou-253/)

***

### Step 3: Clue From the Source

The **first image** on the site caught my attention. Looking at the browser tab title gave me a very promising filename: `Aphrodite_final.j`.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FGymhgGRL1sQnEARZzuey%2FPasted%20image%2020250412215844.png?alt=media&#x26;token=f4b2c3e6-640e-467c-bbf2-702d2ad71551" alt=""><figcaption></figcaption></figure>

Based on the challenge description, I used this filename as the flag.

***

### Step 4: Submitting the Flag

```
1753c{Aphrodite_final.j}
```

**Correct!**

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FwK3fYIxPqz2OGTg9rEcp%2FPasted%20image%2020250412220118.png?alt=media&#x26;token=6596cc7f-1cc3-4f13-9843-929ef5be3dc3" alt=""><figcaption></figcaption></figure>

***

### Final Flag

```
1753c{Aphrodite_final.j}
```
