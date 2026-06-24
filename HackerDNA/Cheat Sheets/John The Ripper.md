## What is John the Ripper?

**John the Ripper** is a free and open-source password cracking tool. Originally developed for Unix, it now runs on many platforms and supports hundreds of hash types. The "Jumbo" version adds even more formats and features.

John comes pre-installed on Kali Linux. Official site: [openwall.com/john](https://www.openwall.com/john/).

## 📦 Installation

Kali Linux

```
sudo apt install john
```

Jumbo Version (recommended)

```
git clone https://github.com/openwall/john
cd john/src && ./configure && make
```

macOS (Homebrew)

```
brew install john-jumbo
```

## 🎯 Basic Usage

```
# Crack with default settings (auto-detect format)
```

## ⚔️ Attack Modes

|Mode|Flag|Description|
|---|---|---|
|Single|--single|Uses login names, GECOS, home dir names|
|Wordlist|--wordlist=FILE|Dictionary attack|
|Incremental|--incremental|Brute force all combinations|
|Mask|--mask=MASK|Pattern-based brute force|
|External|--external=MODE|Custom C-like functions|

```
# Single mode (fastest, uses usernames)
```

## 🎭 Mask Mode Characters

|Placeholder|Character Set|
|---|---|
|?l|Lowercase (a-z)|
|?u|Uppercase (A-Z)|
|?d|Digits (0-9)|
|?s|Special characters|
|?a|All printable ASCII|
|?h|Hex lowercase (0-9, a-f)|
|?H|Hex uppercase (0-9, A-F)|

```
# Password1 pattern
```

## 📋 Common Hash Formats

|Format|Description|
|---|---|
|raw-md5|Raw MD5|
|raw-sha1|Raw SHA1|
|raw-sha256|Raw SHA256|
|raw-sha512|Raw SHA512|
|sha512crypt|Linux shadow file ($6$)|
|sha256crypt|Linux shadow file ($5$)|
|md5crypt|Linux/BSD MD5 crypt ($1$)|
|bcrypt|Blowfish crypt ($2a$, $2b$, $2y$)|
|nt|Windows NTLM|
|lm|Windows LM|
|mscash2|MS Cache 2 (Domain Cached)|
|krb5tgs|Kerberos TGS|

```
# List all formats
```

## 🔧 Hash Extraction Tools (*2john)

John includes many tools to extract hashes from various file types:

```
# Linux shadow file
```

## 📜 Word Mangling Rules

```
# Use default rules
```

### Common Rule Sets

|   |   |
|---|---|
|Single|Default single crack rules|
|Wordlist|Default wordlist rules|
|best64|Top 64 most effective rules|
|jumbo|Comprehensive rule set|
|KoreLogic|Very thorough rules|

## ⚡ Performance Options

|Flag|Description|
|---|---|
|--fork=N|Fork N processes for parallel cracking|
|--node=X/Y|Split work for distributed cracking|
|--devices=N|OpenCL device selection|
|--min-length=N|Minimum password length|
|--max-length=N|Maximum password length|

```
# Use all CPU cores
```

## 💾 Session Management

```
# Name a session
```

## 🔥 Common Cracking Scenarios

```
# Crack Linux shadow file
```

## 📚 Additional Resources

- [Official John the Ripper Website](https://www.openwall.com/john/)
- [John Jumbo GitHub Repository](https://github.com/openwall/john)
- [John Documentation](https://www.openwall.com/john/doc/)