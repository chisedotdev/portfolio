<p align="center">
  <img src="https://htb-mp-prod-public-storage.s3.eu-central-1.amazonaws.com/avatars/992c992925936b399906f2a78a740eea.png" alt="logo" width="300">
</p>

- **Machine Name** CodeTwo 
- **IP Address:** `10.10.11.82`  
- **Difficulty:** Easy  
- **OS:** Linux

---

## 🔎 Enumeration

First, I started with an Nmap scan:

```bash
nmap -sV -sC -vv -T4 -oA nmap/codetwo 10.10.11.82
```

### Nmap Results

```bash title="codetwo.nmap"
...
PORT     STATE SERVICE REASON         VERSION
22/tcp   open  ssh     syn-ack ttl 63 OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
...
8000/tcp open  http    syn-ack ttl 63 Gunicorn 20.0.4
8080/tcp open  http    syn-ack ttl 63 SimpleHTTPServer 0.6 (Python 3.8.10)
...
```

- **Ports open:** `22` (SSH), `8000` (HTTP), `8080` (HTTP)  
- SSH version is recent → no quick exploit. Focus on `8000` and `8080`.  

---

> To respect the [HTB rules](https://help.hackthebox.com/en/articles/5188925-streaming-writeups-walkthrough-guidelines), I’m only sharing the enumeration phase for now.  
> ️Full writeup will be released after the machine’s retirement.