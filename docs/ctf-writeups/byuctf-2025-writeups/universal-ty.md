# Universal-ty

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FxxVqF17bF0m8yapXiAEd%2FPasted%20image%2020250517145822.png?alt=media&#x26;token=d393830e-bbb1-47da-a274-69232d706f63" alt=""><figcaption></figcaption></figure>

## TL;DR

The challenge asked for the university Cameron Snider visited before choosing BYU. The image provided didn't contain useful metadata, and AI tools gave misleading results. Through manual visual analysis and reverse image searching, I identified a unique building that led me to the DeBartolo Performing Arts Center. Cross-referencing the location confirmed it was at the University of Notre Dame. I submitted the flag and it was correct.

***

## Solution

### Step 1: Checking the Image Metadata

Since this was a classic OSINT/location-identification challenge, the first step was to check the image metadata using `exiftool`.

Unfortunately, the image contained no useful metadata.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fmg9S0njrsQxXt7KyGr9i%2Fschool2.jpg?alt=media&#x26;token=8623cfee-93e6-4d95-92cb-a449444a3c25" alt="" width="375"><figcaption></figcaption></figure>

***

### Step 2: AI Image Location Detection

I used the AI tool [Find Picture Location & Identify Photo Location Using AI](https://findpiclocation.com/) to analyze the image.

The tool was 90% confident that the image was taken at the Reva and David Logan Center for the Arts. However, comparing it to Google Maps revealed the architecture didn’t match, so I ruled it out.

***

### Step 3: Manual Visual Analysis

With the AI results proving unreliable, I moved on to manual image analysis. I looked for unique architectural features that stood out.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FtjbQrRtrh7HAqOeSLjqr%2FPasted%20image%2020250517151852.png?alt=media&#x26;token=f5515fa3-d5d8-4c89-9a35-7bc3998b2614" alt=""><figcaption></figcaption></figure>

I cropped the prominent structure and ran it through reverse image search.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FBgLaDEwBuyzKxgN9VXED%2FPasted%20image%2020250517152137.png?alt=media&#x26;token=54439f02-2b65-446c-923f-ea1772d37459" alt=""><figcaption></figcaption></figure>

***

### Step 4: Reverse Image Search Hit

The search returned a promising result: a blog post titled [Jax Stumpes: South Bend, IN (10/30/2015)](https://jaxstumpes.blogspot.com/2015/10/south-bend-in-10302015.html).

Scrolling through the post, I found an image that matched the architecture — the **DeBartolo Performing Arts Center**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FuP3G1E3GgQMbT8MUtg8T%2FPasted%20image%2020250517152449.png?alt=media&#x26;token=ed37c567-81de-46f6-a2a6-ab3fe9c749ef" alt=""><figcaption></figcaption></figure>

***

### Step 5: Verifying the Location

I checked the DeBartolo Performing Arts Center on Google Maps. The structure matched the image provided in the challenge.

To confirm, I analyzed the intersection seen in the challenge photo. I tested multiple intersections and confirmed the correct one based on angle and structure alignment.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FyQZZsuvAzlPwXztGnlVK%2FPasted%20image%2020250517153544.png?alt=media&#x26;token=719f6996-5943-4d5a-975a-c3176b918dc7" alt="" width="494"><figcaption></figcaption></figure>

I did a final cross-reference between the Google Maps view and the challenge image.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F2EOQNmEqARtkWvVvCfIP%2FPasted%20image%2020250517154542.png?alt=media&#x26;token=94591645-a7d1-42b9-9dde-26ffcb56cc96" alt=""><figcaption></figcaption></figure>

***

### Step 6: Identifying the University

I searched **“What university is DeBartolo Performing Arts Center in?”** and confirmed it was part of the **University of Notre Dame**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FMkQRyoW2ou0HqcJLcCH4%2FPasted%20image%2020250517154741.png?alt=media&#x26;token=ba016e0f-a46b-43e3-98ce-330975f2c828" alt=""><figcaption></figcaption></figure>

***

## Final Flag

```
byuctf{University_of_Notre_Dame}
```

***

## Notes

* **Exiftool**: Good to try first, but may not always yield results.
* **AI Tools**: Useful for ideas, but always verify — they can be wrong.
* **Manual Analysis**: Pay attention to unique architecture and road layouts.
* **Reverse Image Search**: Very effective when cropping key features.
* **Cross-Referencing Maps**: Use Google Maps’ angles and intersections to verify locations.
