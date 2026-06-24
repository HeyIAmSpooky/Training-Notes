## What is Hashcat?

**Hashcat** is the world's fastest and most advanced password recovery utility, supporting more than 300 highly optimized hashing algorithms. It uses GPU acceleration to achieve billions of password attempts per second.

Hashcat comes pre-installed on Kali Linux. Download from [hashcat.net](https://hashcat.net/hashcat/).

## 📦 Installation

Kali Linux

```
sudo apt install hashcat
```

Download Latest

```
# Download from hashcat.net
wget https://hashcat.net/files/hashcat-6.2.6.7z
```

Check GPU Support

```
hashcat -I
```

## 🎯 Basic Usage

```
hashcat
```

```
# Basic dictionary attack
```

## ⚔️ Attack Modes (-a)

|Mode|Name|Description|
|---|---|---|
|-a 0|Dictionary|Try each word in wordlist|
|-a 1|Combinator|Combine words from two wordlists|
|-a 3|Brute-force (Mask)|Pattern-based brute force|
|-a 6|Hybrid Wordlist+Mask|Wordlist with mask appended|
|-a 7|Hybrid Mask+Wordlist|Mask with wordlist appended|
|-a 9|Association|Word associations|

```
# Dictionary attack
```

## 🎭 Mask Characters

|Placeholder|Character Set|
|---|---|
|?l|abcdefghijklmnopqrstuvwxyz|
|?u|ABCDEFGHIJKLMNOPQRSTUVWXYZ|
|?d|0123456789|
|?h|0123456789abcdef|
|?H|0123456789ABCDEF|
|?s|!"#$%&'()*+,-./:;<=>?@[\]^_`{\|}~|
|?a|?l?u?d?s (all printable)|
|?b|0x00 - 0xff (all bytes)|

```
# 8 lowercase letters
```

## 📋 Common Hash Types (-m)

|Mode|Hash Type|
|---|---|
|0|MD5|
|100|SHA1|
|1400|SHA256|
|1700|SHA512|
|1000|NTLM|
|3000|LM|
|5600|NetNTLMv2|
|13100|Kerberos TGS-REP (etype 23)|
|18200|Kerberos AS-REP (etype 23)|
|500|md5crypt ($1$)|
|1800|sha512crypt ($6$)|
|3200|bcrypt ($2*$)|
|22000|WPA-PBKDF2-PMKID+EAPOL|
|2500|WPA/WPA2|

```
# List all hash modes
```

## 📜 Rules

```
# Use built-in rules
```

### Popular Rule Files

|   |   |
|---|---|
|best64.rule|Most effective 64 rules|
|rockyou-30000.rule|30K rules from rockyou analysis|
|d3ad0ne.rule|Comprehensive rule set|
|dive.rule|Large comprehensive set|
|toggles1-5.rule|Case toggle rules|

## ⚡ Performance Options

|Flag|Description|
|---|---|
|-w 1-4|Workload profile (1=low, 4=nightmare)|
|-O|Optimized kernels (faster, limits password length)|
|-d DEVICES|Select OpenCL devices (comma-separated)|
|-D TYPES|Device types (1=CPU, 2=GPU, 3=FPGA)|
|--force|Ignore warnings|

```
# Maximum performance
```

## 💾 Session Management

```
# Name a session
```

## 🔥 Common Attack Scenarios

```
# Crack NTLM with wordlist
```

## 📚 Additional Resources

- [Official Hashcat Website](https://hashcat.net/hashcat/)
- [Hashcat Wiki](https://hashcat.net/wiki/)
- [Hashcat GitHub Repository](https://github.com/hashcat/hashcat)
- [Example Hashes Reference](https://hashcat.net/wiki/doku.php?id=example_hashes)