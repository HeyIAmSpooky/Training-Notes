## What is Burp Suite?

**Burp Suite** is an integrated platform for web application security testing, developed by PortSwigger. It's the industry standard for manual testing and automated scanning of web applications. The Community Edition is free, while Professional and Enterprise editions offer advanced scanning and collaboration features.

Download from [portswigger.net/burp](https://portswigger.net/burp). Burp Suite comes pre-installed on Kali Linux.

## ⚙️ Initial Setup

### 1. Configure Browser Proxy

Configure your browser to use Burp's proxy:

|   |   |
|---|---|
|Proxy Address|127.0.0.1|
|Proxy Port|8080|

### 2. Install CA Certificate (for HTTPS)

1. With Burp proxy running, visit `http://burp` in your browser
2. Click "CA Certificate" to download
3. Import into browser's certificate store as a trusted CA

💡 Pro Tip

Use Burp's built-in browser (Proxy → Open Browser) for automatic proxy and certificate configuration. Available in both Community and Pro editions.

## ⌨️ Essential Keyboard Shortcuts

|Shortcut|Action|
|---|---|
|Ctrl+R|Send to Repeater|
|Ctrl+I|Send to Intruder|
|Ctrl+Shift+R|Send request (in Repeater)|
|Ctrl+Space|Send request (in Repeater - alternate)|
|Ctrl+U|URL encode selection|
|Ctrl+Shift+U|URL decode selection|
|Ctrl+B|Base64 encode selection|
|Ctrl+Shift+B|Base64 decode selection|
|Ctrl+F|Search|
|Ctrl+/|Toggle Intercept (Proxy)|

## 🔄 Proxy

The Proxy tool intercepts HTTP/HTTPS traffic between your browser and web applications.

### Intercept Tab

|   |   |
|---|---|
|Intercept is on|All matching requests are held for review|
|Intercept is off|Traffic flows through automatically|
|Forward|Send current request to server|
|Drop|Discard current request|
|Action|Right-click menu for send to Repeater, Intruder, etc.|

### HTTP History

All HTTP requests/responses are logged here even when intercept is off. Filter by:

MIME typeStatus codeSearch termFile extensionAnnotation

### Match and Replace Rules

Auto-modify requests/responses (Proxy → Options → Match and Replace):

- Add custom headers to all requests
- Replace User-Agent
- Modify cookies automatically
- Remove security headers from responses

## 🎯 Target

### Site Map

Visual representation of discovered content. Right-click options:

|   |   |
|---|---|
|Add to scope|Include in target scope|
|Spider this host|Crawl for more content|
|Actively scan this host|Run vulnerability scanner (Pro only)|
|Engagement tools|Discover content, find comments, analyze target|

### Scope Configuration

Define which hosts/URLs are in scope for testing. This affects:

- What gets intercepted by Proxy
- What gets crawled by Spider
- What gets scanned by Scanner
- What appears in filtered views

📋 Scope Example Patterns

```
# Include entire domain
.*\.example\.com$

# Include specific path
^https://example\.com/app/.*

# Exclude specific paths
^https://example\.com/logout.*
```

## 🔁 Repeater

Manually modify and resend individual HTTP requests. Essential for testing vulnerabilities.

### Workflow

1

Send request to Repeater (Ctrl+R)

2

Modify the request

3

Click Send

4

Analyze response

### Testing Techniques

- **SQL Injection:** Add `' OR '1'='1` to parameters
- **XSS:** Inject `<script>alert(1)</script>`
- **Path Traversal:** Try `../../../etc/passwd`
- **IDOR:** Change ID values (1 → 2, admin → user)
- **Method Override:** Change GET to POST, PUT, DELETE
- **Header Injection:** Add malicious headers

## 💥 Intruder

Automated customized attacks. Send request to Intruder (Ctrl+I), define positions, and run attacks with payloads.

### Attack Types

|Type|Description|Use Case|
|---|---|---|
|Sniper|Single payload set, one position at a time|Fuzzing individual parameters|
|Battering Ram|Same payload in all positions simultaneously|Same value in multiple fields|
|Pitchfork|Different payload sets in parallel|Testing user:password pairs|
|Cluster Bomb|All combinations of payload sets|Brute force multiple parameters|

### Payload Types

Simple list

Custom wordlist

Numbers

Sequential/random numbers

Brute forcer

Character set combinations

Runtime file

Read from file during attack

Dates

Date range with format

Null payloads

Repeat request n times

### Payload Processing

Apply rules to payloads before sending:

- Add prefix/suffix
- URL encode
- Base64 encode/decode
- Hash (MD5, SHA1, etc.)
- Match/replace
- Skip if matches condition

⚠️ Community Edition Limitation

Intruder in the free edition is throttled. Professional edition removes speed limits.

## 🔤 Decoder

Encode and decode data in various formats.

### Supported Formats

URL

HTML

Base64

ASCII Hex

Hex

Octal

Binary

Gzip

### Hash Functions

MD2, MD5, SHA, SHA-256, SHA-384, SHA-512

## ⚖️ Comparer

Compare two requests or responses to identify differences. Useful for:

- Identifying authentication bypasses
- Finding parameter pollution effects
- Comparing successful vs failed requests
- Spotting timing differences

## 🎲 Sequencer

Analyze randomness of tokens (session IDs, CSRF tokens, etc.). Useful for:

- Testing session token randomness
- Evaluating CSRF token strength
- Analyzing password reset tokens
- Checking API key generation

Collect at least 100+ samples for accurate analysis.

## 🔍 Scanner (Pro Only)

Automated vulnerability scanning.

### Scan Types

|   |   |
|---|---|
|Passive|Analyzes existing traffic, no additional requests|
|Active|Sends probes to test for vulnerabilities|
|Crawl|Discovers content by following links|
|Audit|Tests discovered content for vulnerabilities|

### Common Findings

SQL InjectionXSSCommand InjectionPath TraversalXXESSRFOpen RedirectInfo Disclosure

## 🧩 Essential Extensions

Install from Extender → BApp Store:

|Extension|Purpose|
|---|---|
|Autorize|Automatic authorization testing|
|Logger++|Enhanced logging with filters|
|Param Miner|Discover hidden parameters|
|JSON Web Tokens|JWT testing and manipulation|
|Turbo Intruder|High-speed attacks with Python|
|Hackvertor|Advanced encoding/decoding|
|Active Scan++|Additional active scan checks|
|Collaborator Everywhere|Inject Collaborator payloads everywhere|

## 📚 Additional Resources

- [Official Burp Suite Documentation](https://portswigger.net/burp/documentation)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) — Free training
- [BApp Store](https://portswigger.net/bappstore) — Extensions