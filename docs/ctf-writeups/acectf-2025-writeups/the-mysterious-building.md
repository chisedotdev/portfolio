# The Mysterious Building

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FCtyXflyPoGwKeGLi15VT%2Fimage.png?alt=media&#x26;token=589732a7-7a81-4cd5-b83f-a12447b8274b" alt=""><figcaption></figcaption></figure>

## Introduction

This challenge provides an image of a building, and the objective is to identify its name and location using OSINT techniques.

## Steps

### Step 1: Inspecting the Given Image

The challenge provides an image:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FmqtI7WUSXZhABXOFnckI%2FOSINT-1.jpg?alt=media&#x26;token=96d7e965-d4d5-415f-9d87-f393f2761f9d" alt=""><figcaption></figcaption></figure>

To gather initial information, I used **ExifTool** to check the image metadata.

```bash
exiftool OSINT-1.jpg
```

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FgvHJRAJ6d3kx3K5SWHnm%2Fimage.png?alt=media&#x26;token=de8e6be8-2361-40e8-b45b-aaa9c254bc4e" alt=""><figcaption></figcaption></figure>

In the metadata, I found an interesting **Description** field that stated:

```
Description: National Capital of India
```

This strongly hinted that the building was located in **Delhi, India**.

### Step 2: Reverse Image Search

Since metadata confirmed that the image was from **India's capital**, I used [**FindPicLocation**](https://findpiclocation.com), an image-based location search tool.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FTFNJJ7jJK3uBEOMCMdBy%2Fimage.png?alt=media&#x26;token=e448173f-05ee-40ee-8f48-3912b49c9585" alt=""><figcaption></figcaption></figure>

The results suggested that the building was **near Pitampura TV Tower, Delhi, India**.

### Step 3: Searching for the Building

Finding the exact building using **Google Maps** was challenging since I wasn’t familiar with the area. Instead, I searched **YouTube** for:

```
buildings near Pitampura TV Tower
```

I found a relevant video:\
[Driving in Delhi (Pitampura) - India](https://www.youtube.com/watch?v=PVWj6LvZjLk)

At **1:48 minutes**, I noticed a **similar logo** on a building, so I rewound the video slightly.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FqbV6yqYqx9YFqIJ2ttkh%2Fimage.png?alt=media&#x26;token=3f57c61d-1366-457a-a53b-e2eef73c89f4" alt=""><figcaption></figcaption></figure>

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fg6w2ckPh41k86GtxpY66%2Fimage.png?alt=media&#x26;token=8e3fe7ed-3a87-4a12-bbe1-44af91216dc0" alt=""><figcaption></figcaption></figure>

### Step 4: Identifying the Building

The video showed the name **"PP TRADE CENTER"** on the building.

Now that I had a possible name, I searched for it on **Google Maps** to confirm its existence.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fkwpd1xxjSw2EUgdQxc7z%2Fimage.png?alt=media&#x26;token=109173a5-3231-4534-85c7-d476502e2249" alt=""><figcaption></figcaption></figure>

The **same logo** appeared, but it was on a different building, so I checked another nearby location.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FN2bmn84DFNsbVclPlaTB%2Fimage.png?alt=media&#x26;token=f8eecf21-97c6-48f9-abc7-a78ed3b2e25c" alt=""><figcaption></figcaption></figure>

This confirmed that the building’s name is **PP Trade Center (or Centre)**.

## FLAG

```
ACECTF{pp_trade_center}
```
