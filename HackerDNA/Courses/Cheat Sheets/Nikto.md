## What is Nikto?

**Nikto** is an open-source web server scanner that performs comprehensive tests against web servers for multiple items including over 6,700 potentially dangerous files/programs, outdated versions of over 1,250 servers, and version-specific problems.

Nikto comes pre-installed on Kali Linux. Source at [github.com/sullo/nikto](https://github.com/sullo/nikto).

## 📦 Installation

Kali Linux

```
sudo apt install nikto
```

From Git

```
git clone https://github.com/sullo/nikto
cd nikto/program && perl nikto.pl
```

Update Database

```
nikto -update
```

## 🎯 Basic Usage

```
# Basic scan
```

## ⚙️ Core Options

|Flag|Description|
|---|---|
|-h HOST|Target host (IP, hostname, or URL)|
|-p PORT|Port(s) to scan|
|-ssl|Force SSL mode|
|-nossl|Disable SSL|
|-root PATH|Prepend root value to all requests|
|-id USER:PASS|HTTP authentication|
|-vhost HOSTNAME|Virtual host to scan|
|-timeout SECONDS|Request timeout (default 10)|
|-Pause SECONDS|Delay between tests|

## 🎛️ Tuning Options (-Tuning)

Control which tests to run with `-Tuning` followed by test codes:

|Code|Test Type|
|---|---|
|0|File Upload|
|1|Interesting File / Seen in logs|
|2|Misconfiguration / Default File|
|3|Information Disclosure|
|4|Injection (XSS/Script/HTML)|
|5|Remote File Retrieval (inside web root)|
|6|Denial of Service|
|7|Remote File Retrieval (server wide)|
|8|Command Execution / Remote Shell|
|9|SQL Injection|
|a|Authentication Bypass|
|b|Software Identification|
|c|Remote Source Inclusion|
|x|Reverse Tuning (exclude these tests)|

```
# Only run SQL injection and XSS tests
```

## 📄 Output Options

|Flag|Description|
|---|---|
|-o FILE|Output file|
|-Format FORMAT|Output format (csv, htm, txt, xml, json)|
|-Display OPTIONS|Control display output|

### Display Options (-Display)

|   |   |
|---|---|
|1|Show redirects|
|2|Show cookies received|
|3|Show all 200/OK responses|
|4|Show URLs requiring authentication|
|D|Debug output|
|E|HTTP errors|
|P|Print progress|
|V|Verbose output|

## 🛡️ Evasion Techniques (-evasion)

|Code|Technique|
|---|---|
|1|Random URI encoding (non-UTF8)|
|2|Directory self-reference (/./)|
|3|Premature URL ending|
|4|Prepend long random string|
|5|Fake parameter|
|6|TAB as request spacer|
|7|Change case of URL|
|8|Use Windows directory separator (\)|
|A|Use carriage return (0x0d)|
|B|Use binary value 0x0b|

```
# Use multiple evasion techniques
```

## 🔀 Proxy Options

```
# Use proxy
```

## 🔥 Common Scanning Scenarios

```
# Comprehensive scan with all output
```

## 📚 Additional Resources

- [Nikto GitHub Repository](https://github.com/sullo/nikto)
- [Official Nikto Website](https://cirt.net/Nikto2)