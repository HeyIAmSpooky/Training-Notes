## What is Hydra?

**THC-Hydra** (commonly called Hydra) is a fast, parallelized login cracker that supports numerous protocols. Developed by The Hacker's Choice (THC), it's one of the most versatile password testing tools available, supporting over 50 different protocols including SSH, FTP, HTTP, HTTPS, SMB, databases, and many more.

Hydra is pre-installed on Kali Linux and other security-focused distributions. Source code is available on [GitHub](https://github.com/vanhauser-thc/thc-hydra).

## 📦 Installation

Debian/Ubuntu/Kali

```
sudo apt install hydra
```

RHEL/CentOS/Fedora

```
sudo dnf install hydra
```

macOS (Homebrew)

```
brew install hydra
```

From Source

```
git clone https://github.com/vanhauser-thc/thc-hydra
cd thc-hydra && ./configure && make && sudo make install
```

## 🎯 Basic Syntax

```
hydra
```

|Flag|Description|Example|
|---|---|---|
|-l|Single username|-l admin|
|-L|Username list file|-L users.txt|
|-p|Single password|-p password123|
|-P|Password list file|-P rockyou.txt|
|-C|Colon-separated user:pass file|-C creds.txt|
|-s|Port number|-s 2222|
|-t|Parallel tasks (threads)|-t 16|
|-f|Stop on first valid pair|-f|
|-F|Stop on first valid pair (all hosts)|-F|
|-v / -V|Verbose / show login attempts|-V|
|-o|Output file|-o results.txt|
|-e nsr|Try null/same/reversed passwords|-e nsr|
|-M|Target list file|-M hosts.txt|

## 📡 Supported Protocols

Run `hydra -h` to see all available protocols. Common ones include:

sshftptelnethttp-gethttp-post-formhttps-gethttps-post-formsmbrdpvncmysqlmssqlpostgresoraclemongodbldap2smtppop3imapsnmpredismemcached

## 🔐 SSH Attacks

```
# Single username, password list
```

💡 Pro Tip

SSH typically has rate limiting. Use `-t 4` (4 threads) to avoid triggering account lockouts and connection bans.

## 📁 FTP Attacks

```
# Basic FTP attack
```

## 🌐 HTTP Form Attacks

HTTP form attacks require understanding the login form structure. You need: the form path, POST parameters, and a failure indicator.

### Syntax

```
hydra -l <user> -P <wordlist> <target> http-post-form "/path:user=^USER^&pass=^PASS^:F=failure_string"
```

|Placeholder|Description|
|---|---|
|^USER^|Replaced with username|
|^PASS^|Replaced with password|
|F=string|Failure condition (string present on failed login)|
|S=string|Success condition (string present on successful login)|

### Examples

```
# Basic login form
```

⚠️ Finding Form Parameters

Use browser DevTools (Network tab) or Burp Suite to capture the actual POST request. Look for the form action URL and input field names.

## 🔒 HTTP Basic Authentication

```
# HTTP Basic Auth
```

## 💼 SMB/Windows Attacks

```
# SMB attack
```

## 🗄️ Database Attacks

```
# MySQL
```

## 📧 Email Protocols

```
# SMTP
```

## ⚡ Performance Tuning

|Flag|Description|Default|
|---|---|---|
|-t N|Number of parallel tasks (threads)|16|
|-w N|Wait time for responses (seconds)|32|
|-c TIME|Wait time per connection attempt|-|
|-W N|Wait between reconnects|0|
|-T N|Threads per target (when using -M)|-|

### Recommended Thread Settings

SSH

4 threads

HTTP/HTTPS

16-32 threads

FTP

8-16 threads

RDP

1-4 threads

## 💾 Session Management

Hydra can save and restore sessions for long-running attacks:

```
# Sessions are auto-saved to ~/.hydra/hydra.restore
```

|   |   |
|---|---|
|-R|Restore previous session|
|-I|Ignore existing restore file (start fresh)|

## 📚 Common Wordlists

On Kali Linux, wordlists are typically located in `/usr/share/wordlists/`

|Wordlist|Path|Size|
|---|---|---|
|RockYou|/usr/share/wordlists/rockyou.txt|14M passwords|
|SecLists Common|/usr/share/seclists/Passwords/Common-Credentials/|Various|
|Top 10000|/usr/share/seclists/Passwords/xato-net-10-million-passwords-10000.txt|10K passwords|
|Default Creds|/usr/share/seclists/Passwords/Default-Credentials/|Various|

💡 Pro Tip

Start with smaller, targeted wordlists before using massive ones like rockyou.txt. Try common defaults first: `admin:admin`, `root:root`, `user:password`.

## 🔥 Common Attack Scenarios

```
# Quick default credential check
```

## 📚 Additional Resources

- [Official GitHub Repository](https://github.com/vanhauser-thc/thc-hydra) — Source code and documentation
- [SecLists](https://github.com/danielmiessler/SecLists) — Collection of usernames, passwords, and wordlists
- [Kali Hydra Documentation](https://www.kali.org/tools/hydra/) — Official Kali tool page