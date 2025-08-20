
# HotPause

> CATEGORY: OSINT 

## Introduction

**HotPause** is an open-source intelligence challenge focused on uncovering information from a particular event. It begins with identifying the precise location where a video was filmed. The next task is to locate an agent's specific seat within that venue. The challenge concludes by retrieving the recorded data stream from a Flipper Zero during the beat drop of Chris Martin's "I love you so..." to determine the right color

## Step 1: Finding the Event Location

The challenge provides an `.mp4` file, which suggests that the first step is to analyze the video for any identifiable details. To make the investigation easier, I took a screenshot from the video at a key moment.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FHcTp5aiZchj75kr5jckz%2Fimage.png?alt=media&#x26;token=a6a9de65-0ab5-48fd-902a-e1a786f15c1a" alt="concert.mp4 screenshot" width="375"><figcaption><p>concerpt.mp4</p></figcaption></figure>

To find the event location, I performed a **reverse image search** using **Google Images**.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FCotWMr5noDMzd6Y1qwPh%2Fimage.png?alt=media&#x26;token=ce3dcca9-5394-4129-ab1e-63b1814d0206" alt="reverse image search result screenshot"><figcaption><p>reverse image search result screenshot</p></figcaption></figure>

The results showed multiple **Instagram posts** with similar visuals, one of which revealed the **city name**.

Initially, I tried **MUMBAI**, but it was incorrect. After retrying with **AHMEDABAD**, I got the correct answer.

## Step 2:  Determining the Exact Seat Block

I began by searching **"Coldplay Ahmedabad seating chart"** on Google.

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FK7VxA0Xz3UQB14c9MAXU%2Fimage.png?alt=media&#x26;token=e7a4eaa3-80be-4155-870b-1aedb431debd" alt="google search result screenshot"><figcaption><p>google search result screenshot</p></figcaption></figure>

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FtQavbC1TCCQDy55uhMEh%2Fimage.png?alt=media&#x26;token=4c09518b-4ded-4916-a502-c19c52b76b07" alt="" width="406"><figcaption><p><a href="https://coldplayindia.com/best-seats-for-coldplay-ahmedabad-concert/">https://coldplayindia.com/best-seats-for-coldplay-ahmedabad-concert/</a></p></figcaption></figure>



Comparing the seating chart with the screenshot from the video, I could see that the agent was sitting on the **right side of the stadium**.

To find the exact block, I started testing different inputs, beginning with **P block** and moving to **Q block**. After multiple attempts, I found the correct answer: **Q3**.

## Step 3. Retrieving the Flipper Zero Data Stream

Step 3 took me way longer than I expected. I spent hours trying different approaches before finally figuring it out. I even asked for hints to make sure I was on the right track. Along the way, I fell into several rabbit holes—attempting to decode the data as binary, misinterpreting the format as hexadecimal, and overcomplicating the extraction process. After a lot of trial and error, I finally found the correct answer.

To figure out the correct answer, I started by searching **"Coldplay India concert wristband"** on Google. This led me to an article explaining how the LED wristbands work:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FZAZA4iW6vxB6yuEZUE44%2Fimage.png?alt=media&#x26;token=0fd6fac1-a965-4088-85c5-fce0d35f72c7" alt=""><figcaption><p><a href="https://tech.hindustantimes.com/tech/news/coldplay-concert-india-how-led-wristbands-works-and-create-magical-moments-71726983355343.html">https://tech.hindustantimes.com/tech/news/coldplay-concert-india-how-led-wristbands-works-and-create-magical-moments-71726983355343.html</a></p></figcaption></figure>

From there, I learned that the wristbands use a specific technology, so my next search was **"Coldplay wristband infrared."** This brought me to a discussion on Reddit:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FsXyh0B5jVQYbV2jKPTRK%2Fimage.png?alt=media&#x26;token=57aec920-5e99-4ec9-b3e9-15f7ccc89625" alt=""><figcaption><p><a href="https://www.reddit.com/r/Coldplay/comments/w7rgth/how_do_the_coldplay_wristbands_work_and_how_would/">https://www.reddit.com/r/Coldplay/comments/w7rgth/how_do_the_coldplay_wristbands_work_and_how_would/</a></p></figcaption></figure>

While scrolling through the discussion, I found a **GitHub repository** related to **PixMob IR reverse engineering:**

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2FhQDA9R1DezqfVhNkeg21%2Fimage.png?alt=media&#x26;token=db04a996-606a-49ca-9281-0c10eadccf84" alt=""><figcaption><p><a href="https://github.com/danielweidman/pixmob-ir-reverse-engineering">https://github.com/danielweidman/pixmob-ir-reverse-engineering</a></p></figcaption></figure>

At first, I explored this repo but couldn’t find a direct answer. However, at the bottom of the page, I found another linked repository:

<figure><img src="https://3066381948-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F1v4zpYg12djm83qExa3x%2Fuploads%2Fr09bj7NxcFBLVSbCpsU4%2Fimage.png?alt=media&#x26;token=029856fe-22d4-4d47-aa70-91dd2cfeeda9" alt=""><figcaption></figcaption></figure>

Inside this repo, I found a file named **PixMob\_main.ir** and searched for an instance of the **yellow** color. That’s when I found the correct data stream:

```
1400 1400 700 700 700 700 1400 2800 700 2100 700 700 700 1400 700 1400 1400 2800 1400 2800 70
```

This turned out to be the correct answer.

## Conclusion

This challenge was both fun and difficult, pushing me to think outside the box. It took a lot of trial and error, but I’m happy I was able to solve it—especially since this was my first CTF. One key takeaway from this experience is to not overcomplicate things. Always check the simplest explanations first before diving into more complex solutions.

