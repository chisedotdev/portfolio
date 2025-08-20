# Timesink

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fatlr2pT5Gh0RaCtNRCaD%2FPasted%20image%2020250427143331.png?alt=media&#x26;token=7b03fcd1-d7e0-4004-a67e-ff68faf0b703" alt=""><figcaption></figcaption></figure>

## TL;DR

The challenge asks for the street where a bridge in a YouTube video is located. After analyzing the bridge image, I identified the **Little Nestucca River Bridge** and confirmed it using coordinates and additional cross-referencing. The correct street is **Little Nestucca River Road**.

***

## Solution

### Step 1: Analyzing the Image

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fvz6uMQ7dtteud8lijJhl%2FPasted%20image%2020250427143440.png?alt=media&#x26;token=cdc4144b-e1c5-44fb-833b-ee3c972ded47" alt=""><figcaption></figcaption></figure>

The first step was to use **Google Reverse Image Search** on the provided photo of the bridge.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FBg0abDz7SeDoriVFIhEC%2FPasted%20image%2020250427143936.png?alt=media&#x26;token=2ca8dcaa-5f82-42f5-ab02-63831ed5059f" alt=""><figcaption></figcaption></figure>

The **first result** was interesting, so I clicked on it:\
[https://weareplaygrounds.nl/lorn-timesink-directed-by-pavel-brenner/](https://weareplaygrounds.nl/lorn-timesink-directed-by-pavel-brenner/)

After scrolling down, I found a **high-quality version** of the bridge image.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fv31tepL4I7dOmCH96uxA%2FPasted%20image%2020250427144259.png?alt=media&#x26;token=8ce92707-2763-45da-ad29-f75283987ea5" alt=""><figcaption></figcaption></figure>

In this version of the image, I zoomed in on a sign and could read "Nestucca River." This gave me a key clue for the next step.

***

### Step 2: Identifying the Bridge

My search results led me to a website that described the **Little Nestucca River Bridge I**, which seemed to match the bridge in the photo.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FyfBEb7SumKVT9eavLwrZ%2FPasted%20image%2020250427144801.png?alt=media&#x26;token=429f29b0-895a-4989-a6b2-b9d38756f869" alt=""><figcaption></figcaption></figure>

I found the **coordinates** for the bridge: **45° 6' 29.98" N, 123° 49' 26" W** and plugged these into **Google Maps** to check if the location was accurate.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FMnFfkuN7qYzKAmb1Y7Fx%2FPasted%20image%2020250427151116.png?alt=media&#x26;token=8a24c04d-1460-498f-9fb8-b3d6ce985bac" alt=""><figcaption></figcaption></figure>

***

### Step 3: Verifying the Location

To verify that this was the correct bridge, I cross-referenced the video still with images and information from the **BTS of the Timesink music video** on Instagram:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FluW5F8uBwCEO18dIwqjj%2FPasted%20image%2020250427151236.png?alt=media&#x26;token=027f7940-311e-446c-b1fb-a2ab9880df91" alt=""><figcaption></figcaption></figure>

This gave me additional visual confirmation that the bridge was indeed the correct one.

***

### Step 4: Confirming the Street Name

I searched for information on the bridge's street and found that there is a **Little Nestucca River Road** with a **truss bridge**, which matched the bridge I was analyzing.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FeOCDGGuUqxKpYy4ZPyfI%2FPasted%20image%2020250427151513.png?alt=media&#x26;token=a5c62ec5-2805-441a-ae99-9c5847383dfe" alt=""><figcaption></figcaption></figure>

I also searched for where **Timesink by Lorn** was filmed on Google, and this gave me further confirmation that I was on the right track.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FkiK0AwNsKlsjtela1s9Y%2FPasted%20image%2020250427151648.png?alt=media&#x26;token=255c8adc-2351-4a1e-93eb-c00a77520e17" alt=""><figcaption></figcaption></figure>

***

### Step 5: Final Flag Submission

After confirming the location, I submitted the flag:

```
CIT{little_nestucca_river_rd}
```

It was accepted!

## Final Flag

```
CIT{little_nestucca_river_rd}
```

## Notes

* **Reverse Image Search**: Helped find a high-quality version of the bridge image, essential for identification.
* **Cross-Referencing**: The **Behind-the-Scenes (BTS)** footage from **Timesink** was invaluable for confirming the bridge location.
* **Structurae Database**: A top resource for structural engineering, with over 85,000 structures and 600,000 publications, it helped verify the bridge details.
