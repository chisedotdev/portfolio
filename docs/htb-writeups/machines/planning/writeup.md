# Planning – Writeup

<p align="center">
  <img src="https://htb-mp-prod-public-storage.s3.eu-central-1.amazonaws.com/avatars/c9efb253e7d1d9b407113e11afdaa905.png" alt="logo" width="300">
</p>

## Overview

-   **Machine Name:** Planning
-   **IP Address:** 10.10.11.68
-   **Difficulty:** Easy
-   **OS:** Linux
-   **Provided Credentials:** admin / 0D5oT70Fq13EvB5r

---

## Enumeration

As in a real-world scenario, the engagement began with provided credentials. The initial step was to perform a comprehensive port scan on the target machine.

```bash
sudo nmap -sV -sC -vv -T4 -oA nmap/planning 10.10.11.68
```

The nmap scan revealed two open ports:

* **Port 22 (SSH):** Running OpenSSH 9.6p1. This version is relatively recent and did not appear to have any public exploits.

* **Port 80 (HTTP):** Running nginx 1.24.0. The scan results indicated a redirect to `http://planning.htb/`.

After failing to find a login page on the main site, I performed a virtual host (vhost) fuzzing attack to discover hidden subdomains. This method is often more efficient than a full directory brute-force.

I used bffuf, a custom wrapper script for ffuf. The script is available on [GitHub](https://github.com/chisedotdev/custom-scripts/tree/main/src/bffuf).

```bash
bffuf vhost http://planning.htb /usr/share/wordlists/seclists/Discovery/DNS/services-names.txt -fc 301 -or vhosts.txt
```

The scan quickly identified a new subdomain, **grafana.planning.htb**, which was added to my `/etc/hosts` file to allow access.

---

> To respect the [HTB rules](https://help.hackthebox.com/en/articles/5188925-streaming-writeups-walkthrough-guidelines), I’m only sharing the enumeration phase for now.
> ️Full writeup will be released after the machine’s retirement.