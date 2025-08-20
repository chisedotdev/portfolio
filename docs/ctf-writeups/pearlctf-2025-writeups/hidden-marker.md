# Hidden Marker

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FfQZcaIsfFIuxZak3HRdp%2FPasted%20image%2020250307234638.png?alt=media&#x26;token=c68e428c-64b2-4d1a-b230-7944ecf873f3" alt=""><figcaption></figcaption></figure>

## Introduction

A whistleblower using the alias "spiriteawx" has revealed a large-scale art smuggling operation, leaking crucial financial documents and leaving behind cryptic hints. The goal of this challenge is to track down the smuggling location and identify the associated transaction.

***

## Step by Step Solution

### Step 1: Finding Social Media Accounts

Since we have a username, I used Sherlock to check for social media accounts.

Result of Sherlock:

```
https://allmylinks.com/spiriteawx
https://www.artstation.com/spiriteawx
https://cults3d.com/en/users/spiriteawx/creations
https://freelance.habr.com/freelancers/spiriteawx
https://gitlab.gnome.org/spiriteawx
https://nationstates.net/nation=spiriteawx
https://nationstates.net/region=spiriteawx
https://torrentgalaxy.to/profile/spiriteawx
https://x.com/spiriteawx
Total Websites Username Detected On : 9
```

Among these, we found an X account. Checking it revealed the following:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FChSqVXpVQFNTvmarl3Td%2FPasted%20image%2020250307235228.png?alt=media&#x26;token=8a767a8c-465c-4bbd-b34f-f175eb3cca35" alt=""><figcaption></figcaption></figure>

A tweet related to major art smuggling contained a link to Pastebin with financial records. The tweet also included an image, which supposedly shows where the smuggling took place.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FiPLscdfT8EpRb6RbjqzG%2F1.jpg?alt=media&#x26;token=e27a0db5-8508-41b4-a43f-5f140b42c690" alt=""><figcaption></figcaption></figure>

### Step 2: Identifying the Location

To determine the location, I first attempted reverse image searches but found no matches. Assuming the image was taken from Google Maps, I decided to use my favorite tool, [Find Picture Location & Identify Photo Location Using AI](https://findpiclocation.com/).

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FP4slfw5EDkPUYfCXDWkY%2FPasted%20image%2020250308000330.png?alt=media&#x26;token=8fa186e3-d296-4076-8d7c-9544707a3a36" alt=""><figcaption></figcaption></figure>

This led me to a possible location: Prague, Czech Republic.

I then manually searched the map for about 30 minutes, but the area was too vast to check every street. Upon closer examination of the provided image, I noticed a vintage car, which stood out. This suggested it could be a known attraction. Searching for 'Prague Czech vintage cars location' on Google helped narrow it down.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fxge9xzIgE5I8tSTia1ZF%2FPasted%20image%2020250308000642.png?alt=media&#x26;token=4d354804-9dbc-4d9f-97eb-e2b5cbfde6c0" alt=""><figcaption></figcaption></figure>

The first result in Google Maps provided the answer.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FrHGuSS6QOe9IYx5cT8QJ%2FPasted%20image%2020250308000829.png?alt=media&#x26;token=3c2c8d33-12fb-4f3c-a1e8-216a604d430f" alt=""><figcaption></figcaption></figure>

FOUND IT! The street name is 'Celetna'. This gave me half of the flag.

### Step 3: Finding the Transaction ID

Now, I needed to extract the transaction ID from the financial records. The logs contained over 1000 entries, and I had only 500 attempts to find the correct one.

After skimming through the data, I found suspicious entries such as:

```
"UserId","TransactionId","TransactionTime","ItemCode","NumberOfItemsPurchased","CostPerItem"

"309960","5988543","Wed May 02 10:36:00 IST 2023","469644","3067248","4.08"
"321426","6268163","Tue Dec 18 08:56:00 IST 2023","459921", BACK DOOR ,"72"
...
537. "-1","-1","[REDACTED BY ADMIN]","-1","-1", "-1"
```

After 12 failed attempts with different transaction IDs, I became suspicious of the redacted entry:

`"-1","-1","[REDACTED BY ADMIN]","-1","-1", "-1"`

I was initially confused as to why it was censored. Scrolling further, I found a comment in the Pastebin log:

`It was there. I swear!` - ArmoredVortex

This suggested that the log had been edited. If the original data had been altered, I needed to find an earlier version. Searching for "ArmoredVortex" and "spiriteawx" using Sherlock yielded nothing useful, so my last resort was the Wayback Machine.

Using the Wayback Machine:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F5t1RMNbwBXs6DLW5AoWM%2FPasted%20image%2020250308002234.png?alt=media&#x26;token=457d2f20-54fe-4fa6-b92e-5796fd157e2b" alt=""><figcaption></figcaption></figure>

Bingo! The redacted entry at line `537` was visible in an earlier version:

```
"845921","6382938","Sat Jan 07 00:00:00 IST 2024","372819","7", "3.21"
```

***

## FLAG

```
pearl{celetna_6382938}
```
