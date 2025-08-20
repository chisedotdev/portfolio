# Social Circles

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FqgV5VK0opVWfbRLA9Jkx%2Fimage.png?alt=media&#x26;token=ad4b9838-092b-4d8c-bcf4-76876fa4fee2" alt=""><figcaption></figcaption></figure>

## Introduction

This OSINT challenge provides a **username** and instructs us to **follow them on YouTube**. Our goal is to track the user across different platforms and extract the hidden flag.

## Steps

### Step 1: Checking the YouTube Channel

The challenge provides the username:&#x20;

```
AhjussiPlayz
```

So, I searched for this **YouTube channel** and found that it had only **one video** uploaded. Since it was the only available content, it was likely where the flag was hidden.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F6GYTHfu6FUI5x6vt7Bz8%2FPasted%20image%2020250228222827.png?alt=media&#x26;token=2d0dedfb-0e5d-4499-8d64-c9fe3091d11f" alt=""><figcaption></figcaption></figure>

### Step 2: Inspecting the Video for Clues

I played the video, and at first, nothing seemed unusual. However, I noticed that **a transcript was available**, suggesting that **closed captions (CC)** were present.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FNBzqAda6AM82EB7RiGxS%2FPasted%20image%2020250228223032.png?alt=media&#x26;token=83b924d6-e22b-411b-8967-099b6c0026b5" alt=""><figcaption></figcaption></figure>

Checking the **English CC** revealed nothing.

I then switched to **Korean CC**, and this was where I found something interesting.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FVE7y3hePYucFsuyK9UFR%2FPasted%20image%2020250228223157.png?alt=media&#x26;token=2d7e7133-2d50-4683-b228-6a40182aefaa" alt=""><figcaption></figcaption></figure>

### Step 3: Translating the Hidden Text

I used **Google Translate** to translate the Korean subtitles.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FdVmfbytaNKSPHaXwsp7K%2FPasted%20image%2020250228223420.png?alt=media&#x26;token=31912f91-477a-4bbd-8839-1835bacfb016" alt=""><figcaption></figcaption></figure>

It revealed a **new username**:

```
wimebix884
```

This was an important lead, so I decided to search for this username across different platforms.

### Step 4: Tracking the Username with Sherlock

I used **Sherlock**, a Kali Linux CLI tool for username enumeration, to find accounts associated with **wimebix884**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FXhcjsNt8MQ8Sip5aq9EZ%2FPasted%20image%2020250228223937.png?alt=media&#x26;token=2d1facf3-9d50-48f2-9f05-01cd2cd65742" alt=""><figcaption></figcaption></figure>

Sherlock found **multiple results**, so I manually checked **seven links** one by one.

### Step 5: Finding the Account on Smule

One of the results led me to this **Smule profile**:

🔗 [https://www.smule.com/wimebix884](https://www.smule.com/wimebix884)

Under the **Songs tab**, I noticed an attachment named **"Flag Debaucher"**. This looked suspicious, so I clicked on it.

### Step 6: Extracting the Final Flag

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FB44rWPkOFbxzFncPKCDd%2FPasted%20image%2020250228224223.png?alt=media&#x26;token=9e454a02-03a8-4a5c-afd2-ef3ff35f9a1d" alt=""><figcaption></figcaption></figure>

The **Smule attachment** contained a **Google Drive link**:

🔗 [https://drive.google.com/file/d/1093uvDYSVWke8ze2jdgJ1rVehz51Jx00](https://drive.google.com/file/d/1093uvDYSVWke8ze2jdgJ1rVehz51Jx00)

I played the **audio file** uploaded to Google Drive and successfully extracted the **flag**.

## FLAG

```
ACECTF{mu171m3d14_f146}
```
