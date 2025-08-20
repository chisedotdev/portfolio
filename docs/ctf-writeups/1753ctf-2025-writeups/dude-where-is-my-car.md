# Dude where is my car

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FbvgAQYIPGDdAipbrvciY%2FPasted%20image%2020250412225830.png?alt=media&#x26;token=1cd0c276-4bc6-457f-a0b9-f595ce83ae0b" alt=""><figcaption></figcaption></figure>

***

### Challenge Description

> I'm not sure where I lost my car, but I believe I’ll remember if I can see the original photo again. Can you find it? I only have this photoshopped and cropped version, but I’m confident it contains enough information for an OSINT expert. To prove your success, submit a flag with the Build Number from the EXIF data in the format: `1753c{Build Number}`.

***

### Provided Image

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F4oJ0Xol2WbLNx57XGsDq%2FPasted%20image%2020250412230052.png?alt=media&#x26;token=b982d95e-3371-4105-a8bc-1d3e407f5d33" alt="" width="375"><figcaption></figcaption></figure>

***

### Step 1: Checking Metadata

I used `exiftool` to examine the metadata of the provided image:

```bash
exiftool dude-where-is-my_car.jpg
```

**Output (trimmed):**

```
...
File Name                       : dude-where-is-my_car.jpg
File Size                       : 1828 kB
Image Size                      : 2132x2040
MIME Type                       : image/jpeg
...
```

Unfortunately, **no useful EXIF data** (like GPS or device info) was found.

***

### Step 2: Reverse Image Search

I uploaded the image to **Google Image Search**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FmNdrSDVtDEMvM9p0XpC8%2FPasted%20image%2020250412230943.png?alt=media&#x26;token=5683f1c2-d9b8-45ad-b1cd-5074e55db918" alt=""><figcaption></figcaption></figure>

After skimming through the results, **nothing matched exactly**. So, I analyzed the image further myself.

***

### Step 3: Analyzing Visual Clues

While inspecting the image, I spotted a **URL on the license plate**:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FF0xYIOJaa8OOf7psfby9%2FPasted%20image%2020250412231725.png?alt=media&#x26;token=4943c28d-7453-401e-970d-e806135cc442" alt="" width="375"><figcaption></figcaption></figure>

```
www.lieberzupiper.de
```

Visiting the URL directly didn’t work (domain is offline), so I searched for `lieberzupiper de` on Google.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fk7h61sgOCQ5L0ICcflUx%2FPasted%20image%2020250412232107.png?alt=media&#x26;token=3d59c652-b3bd-4420-b988-89be4ac2ef28" alt=""><figcaption></figcaption></figure>

Bingo! I found a listing on:

```
https://tablica-rejestracyjna.pl/WWY?p=373
```

Unfortunately, it didn’t have the full original image either.

***

### Step 4: Exploring the Site

I clicked on **"Więcej komentarzy »"**, which led to:

```
https://tablica-rejestracyjna.pl/komentarze/WWY
```

There, I browsed through the pages manually until **I found the original image on page 3**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FowbXDWp34l58D2PqtHd8%2FPasted%20image%2020250412232616.png?alt=media&#x26;token=68861b9d-c4c1-4c2b-b86a-15b5e81e7c62" alt=""><figcaption></figcaption></figure>

Downloaded it and prepared to analyze its metadata.

***

### Step 5: Extracting the Flag

Ran `exiftool` on the downloaded original image:

```bash
exiftool original-car-photo.jpg
```

**This time I got the jackpot:**

```
...
Build Number                    : S2RUBS32.51-15-3-19
...
```

***

### Step 6: Submitting the Flag

I submitted the flag using the required format:

```
1753c{S2RUBS32.51-15-3-19}
```

**Correct!**

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fpi1MZehHZGpGB6qYG4ph%2FPasted%20image%2020250412232914.png?alt=media&#x26;token=afc07a69-4f0a-45a1-8996-9787c832a4cd" alt=""><figcaption></figcaption></figure>

***

### Final Flag

```
1753c{S2RUBS32.51-15-3-19}
```
