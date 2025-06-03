# 🐱 Meow | Hack The Box

Hello everyone, in this blog post I’ll share how I solved the **Meow** challenge on Hack The Box.

Okay, let’s start…
**Note:** I’m not an expert. I’m writing this blog just to document my learning journey. 🚀

---

### 🔍 Step 1: Scan the Target with Nmap

I started by scanning the target IP using `nmap`.

```bash
nmap -A 10.129.1.17
```

**Output (summary):**

```
PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd
```

So port **23 (telnet)** is open, and it’s running a Linux `telnetd` service.

---

### 📡 Step 2: Connect via Telnet

At first, when I typed the `telnet` command, I got an error:

```
command not found
```

So I installed Telnet:

```bash
apt install telnet
```

Then I connected:

```bash
telnet 10.129.1.17
```

---

### 🔑 Step 3: Try Default Credentials

I tried some default usernames and passwords:

- `admin`
- `administrator`
- and finally... `root`

✅ **Bingo! `root` worked without a password!**

---

### 🎉 Step 4: Capture the Flag

Once I logged in as root, I looked around and found the flag.

```bash
cat flag.txt
```

Hahhh 😅 finally, I captured the flag…

---

### 🎯 Final Thoughts

This was a fun and simple box — perfect for beginners like me who are just starting with Hack The Box. The key takeaway: **check open services, try default logins, and don’t overthink simple challenges**.

Happy hacking! 😄
