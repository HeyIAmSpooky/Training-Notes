## What is Gobuster?

**Gobuster** is a tool for brute-forcing URIs, DNS subdomains, virtual host names, open Amazon S3 buckets, and more. Written in Go, it's extremely fast and supports concurrent connections for maximum speed.

Gobuster comes pre-installed on Kali Linux. Source code at [github.com/OJ/gobuster](https://github.com/OJ/gobuster).

## 📦 Installation

Kali Linux

```
sudo apt install gobuster
```

Go Install

```
go install github.com/OJ/gobuster/v3@latest
```

macOS (Homebrew)

```
brew install gobuster
```

## 🔧 Modes Overview

|Mode|Purpose|
|---|---|
|dir|Directory/file enumeration|
|dns|DNS subdomain enumeration|
|vhost|Virtual host enumeration|
|fuzz|Fuzzing with FUZZ keyword|
|s3|Amazon S3 bucket enumeration|
|gcs|Google Cloud Storage enumeration|
|tftp|TFTP file enumeration|

## 📁 Dir Mode (Directory Enumeration)

```
# Basic directory scan
```

### Dir Mode Options

|Flag|Description|
|---|---|
|-u URL|Target URL|
|-w WORDLIST|Path to wordlist|
|-x EXTENSIONS|File extensions to search|
|-t THREADS|Number of threads (default 10)|
|-s STATUS|Include status codes|
|-b STATUS|Exclude status codes|
|-c COOKIE|Cookie string|
|-H HEADER|Custom header|
|-a USER-AGENT|Custom User-Agent|
|-r|Follow redirects|
|-k|Skip TLS verification|
|-n|Don't print status codes|
|-e|Print full URLs|
|--timeout DURATION|HTTP timeout|

## 🌐 DNS Mode (Subdomain Enumeration)

```
# Basic subdomain scan
```

### DNS Mode Options

|   |   |
|---|---|
|-d DOMAIN|Target domain|
|-i|Show IP addresses|
|-c|Show CNAME records|
|-r RESOLVER|Use custom DNS resolver|
|--wildcard|Force wildcard detection|

## 🏠 Vhost Mode (Virtual Host Enumeration)

```
# Basic vhost scan
```

💡 Vhost vs DNS Mode

**DNS mode** queries DNS servers for subdomains. **Vhost mode** sends HTTP requests with different Host headers to find virtual hosts on the same IP (useful when subdomains aren't in DNS).

## 🎯 Fuzz Mode

Use the `FUZZ` keyword to specify where to inject wordlist entries.

```
# Fuzz URL parameter
```

## ☁️ S3 Mode (AWS Bucket Enumeration)

```
# Basic S3 bucket scan
```

## ⚙️ Global Options

|Flag|Description|
|---|---|
|-t THREADS|Number of concurrent threads|
|-o FILE|Output file|
|-v|Verbose output|
|-q|Quiet mode (no banner)|
|--no-error|Don't display errors|
|--delay DURATION|Delay between requests|
|-p PATTERN|File with replacement patterns|

## 📚 Recommended Wordlists

|Purpose|Path (SecLists)|
|---|---|
|Directories (Quick)|/usr/share/wordlists/dirb/common.txt|
|Directories (Medium)|/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt|
|Directories (Large)|/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt|
|Subdomains|/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt|
|API Endpoints|/usr/share/seclists/Discovery/Web-Content/api/api-endpoints.txt|
|Raft (Various)|/usr/share/seclists/Discovery/Web-Content/raft-medium-*.txt|

## 🔥 Common Attack Scenarios

```
# Quick directory scan with common extensions
```

## 📚 Additional Resources

- [Gobuster GitHub Repository](https://github.com/OJ/gobuster)
- [SecLists Wordlists](https://github.com/danielmiessler/SecLists)