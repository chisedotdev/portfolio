# No Country for Old Keys

> CATEGORY - OSINT

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F8whbl4qs3blITpEq8qW0%2FPasted%20image%2020250427160811.png?alt=media&#x26;token=dbda363a-8b43-44b8-bdc0-10d24dd4b43d" alt=""><figcaption></figcaption></figure>

## TL;DR

The challenge asks for Anthony McConnolly's API key. After searching for his online presence and using tools like **Sherlock** to find additional accounts, I discovered his GitHub profile. I then found a hardcoded API key in a GitHub repository and submitted it successfully.

***

## Solution

### Step 1: Investigating Anthony McConnolly

The challenge asks for **Anthony McConnolly's API key**, so my first step was to search for his name online. A quick Google search led me to his **LinkedIn** profile:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2F952VtvldVpsKuzIsyp3I%2FPasted%20image%2020250427161114.png?alt=media&#x26;token=1e24bf2a-7f02-4373-9c92-30ec471f3a1a" alt=""><figcaption></figcaption></figure>

Unfortunately, there wasn't much information there, so I decided to use **Sherlock**, a tool for finding social media accounts associated with a username. I used the LinkedIn slug and ran Sherlock, but got no useful results.

Next, I decided to check **X (Twitter)**, a popular platform for developers, to see if Anthony McConnolly had an account there. After searching, I found his profile:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FJI5A6hAcelBzXhemWWJO%2FPasted%20image%2020250427162123.png?alt=media&#x26;token=ce7970c4-1d2c-4f8f-ad24-2dbabbe42e61" alt="" width="563"><figcaption></figcaption></figure>

Although there was no immediate useful information in his posts, I gained another potential username: **antmcconn**.

***

### Step 2: Using Sherlock Again

With the new username **antmcconn**, I ran **Sherlock** again. This time, I found several results:

```
[*] Checking username antmcconn on:

[+] AllMyLinks: https://allmylinks.com/antmcconn
[+] Freelance.habr: https://freelance.habr.com/freelancers/antmcconn
[+] GNOME VCS: https://gitlab.gnome.org/antmcconn
[+] GitHub: https://www.github.com/antmcconn
[+] LibraryThing: https://www.librarything.com/profile/antmcconn
[+] Mydramalist: https://www.mydramalist.com/profile/antmcconn
[+] NationStates Nation: https://nationstates.net/nation=antmcconn
[+] NationStates Region: https://nationstates.net/region=antmcconn
[+] Spotify: https://open.spotify.com/user/antmcconn
[+] TorrentGalaxy: https://torrentgalaxy.to/profile/antmcconn
[+] Twitter: https://x.com/antmcconn
[+] YandexMusic: https://music.yandex/users/antmcconn/playlists

[*] Search completed with 12 results
```

Among these results, the **GitHub** account caught my attention, so I clicked the link:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FnQ3FVqpCE2NuhNDHtHLo%2FPasted%20image%2020250427162413.png?alt=media&#x26;token=0b294712-eb94-44bb-8d58-d3b9e97fac89" alt=""><figcaption></figcaption></figure>

***

### Step 3: Finding the API Key

On his GitHub profile, there was only one repository. I opened the repository and checked the code. In the **main.c** file, I found the following line:

```
#define API_KEY "YOUR_API_KEY_HERE"
```

To investigate further, I checked the **History** of the file to see if an actual API key was previously hard-coded. After browsing through the file history, I found this:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FXRhaW4hRiWyRrgAhoKTO%2FPasted%20image%2020250427162607.png?alt=media&#x26;token=55c8c9a0-9bd8-4dde-9e16-88a0a8122cee" alt=""><figcaption></figcaption></figure>

```
#define API_KEY "ap9gt04qtxcqfin9"
```

***

### Step 4: Submitting the Flag

I submitted the API key: **ap9gt04qtxcqfin9**. The flag was accepted!

***

## Final Flag

```
ap9gt04qtxcqfin9
```

***

## Notes

* **Sherlock Tool**: Useful for finding social media profiles based on usernames.
* **GitHub Repository**: Always check the file history for potential sensitive information like hard-coded API keys.
* **Keep an Eye on Comments**: Sometimes, sensitive information can be exposed in comments or file histories, so check the history if needed.
