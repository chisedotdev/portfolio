# Happy New Year!

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FHv2rto98I4Qo8PTREbX9%2FPasted%20image%2020250412194908.png?alt=media&#x26;token=458061b2-0566-486e-88c0-88520a4f4d24" alt=""><figcaption></figcaption></figure>



### Challenge Description

> Can you tell where we last celebrated New Year's?
>
> The flag is the city name in English spelling.
>
> **Flag format:** `1753c{cityname}`

***

### Provided Image

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FAEULAXLEPYznyy8IzbHA%2FPasted%20image%2020250412195057.png?alt=media&#x26;token=8ff72688-bc6e-455f-a80f-04101f458cc6" alt="" width="563"><figcaption></figcaption></figure>

***

### Step 1: Checking Metadata

As usual, I started with `exiftool` to check if there was anything useful in the image metadata.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FljqRrtw5hHQ7soprFkAr%2FPasted%20image%2020250412195135.png?alt=media&#x26;token=857e82ce-0ab2-410e-84b1-667a80a54ab3" alt=""><figcaption></figcaption></figure>

Unfortunately, nothing special came up in the EXIF data.

***

### Step 2: Reverse Image Location

Next, I used my **favorite OSINT image tool**:\
&#x20;[findpiclocation.com](https://findpiclocation.com)

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FycPTGBcmfUJRCDpLWfD4%2FPasted%20image%2020250412195955.png?alt=media&#x26;token=55975092-28e6-4c3c-bbd0-adef2eea31c5" alt=""><figcaption></figcaption></figure>

The tool quickly identified the location as **Larnaca**.

***

### Step 3: Submitting the Flag

Based on the result, I submitted the following flag:

```
1753c{larnaca}
```

**Correct!**

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F9aOPNt3sZMkY4JKElhOM%2FPasted%20image%2020250412200233.png?alt=media&#x26;token=81331d24-223e-4277-b635-42f958ddc88f" alt=""><figcaption></figcaption></figure>

***

### Final Flag

```
1753c{larnaca}
```
