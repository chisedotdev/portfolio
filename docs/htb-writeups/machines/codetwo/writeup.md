# CodeTwo – Writeup

<p align="center">
  <img src="https://htb-mp-prod-public-storage.s3.eu-central-1.amazonaws.com/avatars/992c992925936b399906f2a78a740eea.png" alt="logo" width="300">
</p>

## Overview

-   **Machine Name:** CodeTwo
-   **IP Address:** 10.10.11.82
-   **Difficulty:** Easy
-   **OS:** Linux

---

## Enumeration

The initial step in any penetration test is to perform a port scan to identify open services and potential entry points. I used **nmap** with a comprehensive set of flags to gather detailed information.

```bash
nmap -sV -sC -vv -T4 -oA nmap/codetwo 10.10.11.82
```

The scan results revealed three open ports:

* **Port 22 (SSH):** Running OpenSSH 8.2p1, which is a relatively recent version and unlikely to be vulnerable to common exploits. This will likely require credentials.
* **Port 8000 (HTTP):** Running Gunicorn 20.0.4. The website's title, "Welcome to CodeTwo," indicates a custom web application.
* **Port 8080 (HTTP):** Running SimpleHTTPServer 0.6 (Python 3.8.10), which is a basic web server often used for file hosting.

With multiple web services available, the next logical step was to investigate ports 8000 and 8080.

---

> To respect the [HTB rules](https://help.hackthebox.com/en/articles/5188925-streaming-writeups-walkthrough-guidelines), I’m only sharing the enumeration phase for now.
> ️Full writeup will be released after the machine’s retirement.