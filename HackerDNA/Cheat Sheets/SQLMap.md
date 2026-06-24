## What is SQLMap?

**SQLMap** is an open-source penetration testing tool that automates the detection and exploitation of SQL injection flaws. It supports a wide range of database management systems including MySQL, Oracle, PostgreSQL, Microsoft SQL Server, SQLite, and many more.

SQLMap comes pre-installed on Kali Linux. Source code available at [github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap).

## 📦 Installation

Kali Linux (Pre-installed)

```
sqlmap --version
```

pip Install

```
pip install sqlmap
```

From Git

```
git clone https://github.com/sqlmapproject/sqlmap.git
cd sqlmap && python sqlmap.py
```

Update

```
sqlmap --update
```

## 🎯 Basic Usage

```
# Basic GET parameter test
```

💡 Pro Tip

Save Burp Suite requests as files and use `-r request.txt` — this preserves all headers, cookies, and POST data automatically.

## 🔍 Detection Options

|Flag|Description|
|---|---|
|--level=LEVEL|Test level (1-5, default 1). Higher = more tests|
|--risk=RISK|Risk level (1-3, default 1). Higher = riskier tests|
|-p PARAM|Test specific parameter only|
|--dbms=DBMS|Force specific DBMS (mysql, mssql, oracle, etc.)|
|--technique=TECH|Specify injection techniques (BEUSTQ)|
|--string=STRING|String that appears on true condition|
|--not-string=STRING|String that appears on false condition|

### Injection Techniques (--technique)

|   |   |
|---|---|
|B|Boolean-based blind|
|E|Error-based|
|U|UNION query-based|
|S|Stacked queries|
|T|Time-based blind|
|Q|Inline queries|

## 📊 Enumeration

|Flag|Description|
|---|---|
|--banner|Retrieve DBMS banner|
|--current-user|Current database user|
|--current-db|Current database name|
|--is-dba|Check if user is DBA|
|--users|Enumerate database users|
|--passwords|Enumerate user password hashes|
|--privileges|Enumerate user privileges|
|--dbs|Enumerate databases|
|--tables|Enumerate tables|
|--columns|Enumerate columns|
|--schema|Enumerate entire schema|
|--count|Count entries in tables|

## 💾 Data Extraction

|Flag|Description|
|---|---|
|-D DB|Specify database name|
|-T TABLE|Specify table name|
|-C COLUMNS|Specify columns (comma-separated)|
|--dump|Dump table contents|
|--dump-all|Dump all databases|
|--start=N|Start from row N|
|--stop=N|Stop at row N|
|--where=COND|WHERE clause for dump|
|--sql-query=QUERY|Execute custom SQL query|
|--sql-shell|Interactive SQL shell|

### Common Extraction Workflow

```
# Step 1: List databases
```

## 🖥️ OS Access

|Flag|Description|
|---|---|
|--os-shell|Interactive OS shell|
|--os-cmd=CMD|Execute OS command|
|--os-pwn|Get OOB shell (Meterpreter/VNC)|
|--file-read=FILE|Read file from server|
|--file-write=LOCAL|Write local file to server|
|--file-dest=PATH|Destination path on server|
|--reg-read|Read Windows registry key|

⚠️ OS Shell Requirements

OS access requires: stacked queries support, DBA privileges, and appropriate DBMS permissions (FILE privilege for MySQL, xp_cmdshell for MSSQL).

## 📤 Request Options

|Flag|Description|
|---|---|
|-r FILE|Load request from file|
|--data=DATA|POST data string|
|--cookie=COOKIE|HTTP cookie value|
|--headers=HEADERS|Extra headers (newline separated)|
|--user-agent=UA|Custom User-Agent|
|--random-agent|Use random User-Agent|
|--referer=REFERER|Custom Referer header|
|--proxy=PROXY|Use proxy (http://host:port)|
|--tor|Use Tor network|
|--method=METHOD|Force HTTP method (GET/POST/PUT)|

## 🛡️ WAF/IDS Bypass

|Flag|Description|
|---|---|
|--tamper=TAMPER|Use tamper script(s)|
|--delay=SECONDS|Delay between requests|
|--timeout=SECONDS|Connection timeout|
|--retries=N|Retries on connection issues|
|--randomize=PARAM|Randomize parameter value|
|--safe-url=URL|URL to visit between tests|
|--safe-freq=N|Visit safe URL every N requests|

### Common Tamper Scripts

```
# Space bypass
```

## ⚡ Optimization

|Flag|Description|
|---|---|
|--threads=N|Max concurrent threads (default 1)|
|--batch|Never ask for user input (use defaults)|
|--flush-session|Flush session files for target|
|--fresh-queries|Ignore cached query results|
|--null-connection|Don't retrieve page body (faster)|
|-o|Turn on optimization flags|
|-v LEVEL|Verbosity (0-6, default 1)|

## 🔥 Common Attack Scenarios

```
# Full automatic scan
```

## 📚 Additional Resources

- [Official SQLMap Wiki](https://github.com/sqlmapproject/sqlmap/wiki)
- [SQLMap GitHub Repository](https://github.com/sqlmapproject/sqlmap)
- [SQLMap Official Website](https://sqlmap.org/)