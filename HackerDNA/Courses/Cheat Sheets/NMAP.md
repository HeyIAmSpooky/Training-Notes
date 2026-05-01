## What is Nmap?

**Nmap (Network Mapper)** is a free, open-source tool for network discovery and security auditing. Created by Gordon Lyon (Fyodor) in 1997, it has become the industry standard for network scanning, used by security professionals, system administrators, and penetration testers worldwide.

Nmap uses raw IP packets to determine available hosts, services, operating systems, firewall configurations, and dozens of other characteristics. It runs on all major operating systems and official packages are available from [nmap.org](https://nmap.org/download.html).

## 📦 Installation

Debian/Ubuntu/Kali

```
sudo apt install nmap
```

RHEL/CentOS/Fedora

```
sudo dnf install nmap
```

macOS (Homebrew)

```
brew install nmap
```

Windows

```
Download from nmap.org/download
```

## 🎯 Basic Scanning Commands

|Command|Description|
|---|---|
|nmap <target>|Scan single host (default: top 1000 ports)|
|nmap 192.168.1.1-254|Scan IP range|
|nmap 192.168.1.0/24|Scan entire subnet (CIDR notation)|
|nmap -iL targets.txt|Scan targets from file|
|nmap --exclude 192.168.1.1|Exclude specific hosts from scan|
|nmap --excludefile exclude.txt|Exclude hosts listed in file|

## 🔎 Host Discovery (Ping Scanning)

|Flag|Description|Example|
|---|---|---|
|-sn|Ping scan only (no port scan)|nmap -sn 192.168.1.0/24|
|-Pn|Skip host discovery (treat all as online)|nmap -Pn <target>|
|-PS|TCP SYN ping on specified ports|nmap -PS22,80,443 <target>|
|-PA|TCP ACK ping|nmap -PA80,443 <target>|
|-PU|UDP ping|nmap -PU53 <target>|
|-PE|ICMP echo ping|nmap -PE <target>|
|-PP|ICMP timestamp ping|nmap -PP <target>|
|-PM|ICMP netmask ping|nmap -PM <target>|
|-PR|ARP ping (local network only)|nmap -PR 192.168.1.0/24|

💡 Pro Tip

Use `-sn` for quick network sweeps without triggering port scan detection. Combine with `-PR` on local networks for fastest ARP-based discovery.

## 🔌 Port Scanning Techniques

|Flag|Scan Type|Description|
|---|---|---|
|-sS|TCP SYN (Stealth)|Half-open scan, fast and stealthy (requires root)|
|-sT|TCP Connect|Full TCP connection (no root required)|
|-sU|UDP Scan|Scan UDP ports (slower than TCP)|
|-sA|TCP ACK|Map firewall rules (filtered vs unfiltered)|
|-sW|TCP Window|Like ACK but detects open ports via window size|
|-sN|TCP Null|No flags set (evades some firewalls)|
|-sF|TCP FIN|Only FIN flag set|
|-sX|TCP Xmas|FIN, PSH, URG flags set|
|-sM|TCP Maimon|FIN/ACK probe|
|-sI|Idle/Zombie|Stealth scan using zombie host|

## 🎚️ Port Specification

|Flag|Description|Example|
|---|---|---|
|-p 80|Scan single port|nmap -p 80 <target>|
|-p 80,443,8080|Scan specific ports|nmap -p 80,443,8080 <target>|
|-p 1-1000|Scan port range|nmap -p 1-1000 <target>|
|-p-|Scan all 65535 ports|nmap -p- <target>|
|-p U:53,T:80|Specify UDP and TCP ports|nmap -p U:53,T:80,443 <target>|
|--top-ports N|Scan top N most common ports|nmap --top-ports 100 <target>|
|-F|Fast scan (top 100 ports)|nmap -F <target>|
|-r|Scan ports sequentially|nmap -r <target>|

## 🔍 Service & Version Detection

|Flag|Description|
|---|---|
|-sV|Detect service versions on open ports|
|--version-intensity 0-9|Set version scan intensity (0=light, 9=all probes)|
|--version-light|Light version scan (intensity 2)|
|--version-all|Try all probes (intensity 9)|
|-A|Aggressive scan: -sV -O -sC --traceroute|

📋 Example: Full Service Detection

```
nmap -sV --version-all -p 22,80,443,3306,8080 <target>
```

## 💻 OS Detection

|Flag|Description|
|---|---|
|-O|Enable OS detection|
|--osscan-limit|Only attempt OS detection on promising targets|
|--osscan-guess|Guess OS more aggressively|
|--max-os-tries N|Limit OS detection attempts per target|

📋 Example: OS Detection with Aggressive Guessing

```
sudo nmap -O --osscan-guess <target>
```

## 📜 Nmap Scripting Engine (NSE)

NSE contains hundreds of scripts for vulnerability detection, brute forcing, discovery, and more. Scripts are located in `/usr/share/nmap/scripts/` on most Linux systems.

|Flag|Description|
|---|---|
|-sC|Run default scripts (same as --script=default)|
|--script=<name>|Run specific script(s)|
|--script=<category>|Run all scripts in category|
|--script-args=<args>|Provide arguments to scripts|
|--script-updatedb|Update script database|
|--script-help=<name>|Show help for script|

### Script Categories

vuln

Vulnerability detection

exploit

Active exploitation

brute

Brute force attacks

safe

Non-intrusive scripts

discovery

Service discovery

auth

Authentication checks

default

Standard safe scripts

intrusive

May crash services

### Common NSE Script Examples

```
# Vulnerability scan
```

## ⚡ Timing & Performance

### Timing Templates

|Flag|Name|Use Case|
|---|---|---|
|-T0|Paranoid|IDS evasion, extremely slow|
|-T1|Sneaky|IDS evasion, slow|
|-T2|Polite|Reduce network load|
|-T3|Normal|Default timing|
|-T4|Aggressive|Fast scan on reliable networks|
|-T5|Insane|Very fast, may miss ports|

### Fine-Grained Timing Controls

|Flag|Description|
|---|---|
|--min-rate N|Send at least N packets per second|
|--max-rate N|Send no more than N packets per second|
|--min-parallelism N|Minimum number of parallel probes|
|--max-parallelism N|Maximum number of parallel probes|
|--min-hostgroup N|Minimum hosts to scan in parallel|
|--max-hostgroup N|Maximum hosts to scan in parallel|
|--max-retries N|Limit port scan probe retransmissions|
|--host-timeout TIME|Give up on host after this time|
|--scan-delay TIME|Wait between probes|

## 📄 Output Formats

|Flag|Format|Description|
|---|---|---|
|-oN file.txt|Normal|Human-readable output|
|-oX file.xml|XML|Machine-readable XML|
|-oG file.gnmap|Grepable|Easy to grep and parse|
|-oS file.txt|Script Kiddie|L33t speak output (for fun)|
|-oA basename|All Formats|Output in all formats (.nmap, .xml, .gnmap)|

💡 Pro Tip

Always use `-oA` to save results in all formats. This gives you flexibility for reporting (normal), automation (XML), and quick searches (grepable).

### Verbosity & Debugging

|   |   |
|---|---|
|-v / -vv / -vvv|Increase verbosity level|
|-d / -dd|Increase debugging level|
|--reason|Show reason for port state|
|--open|Only show open ports|
|--packet-trace|Show all packets sent and received|

## 🛡️ Firewall & IDS Evasion

|Flag|Description|
|---|---|
|-f|Fragment packets (8 bytes per fragment)|
|--mtu N|Set custom MTU (must be multiple of 8)|
|-D decoy1,decoy2,ME|Use decoy addresses (ME = your real IP)|
|-S <spoofed_ip>|Spoof source address|
|-g <port>|Use specific source port|
|--source-port <port>|Same as -g|
|--data-length N|Append random data to packets|
|--randomize-hosts|Randomize target host order|
|--spoof-mac <mac>|Spoof MAC address (0 for random)|
|--badsum|Send packets with bad checksums|

📋 Example: Evasion Scan

```
nmap -f -D RND:5 --source-port 53 --data-length 50 -T2 <target>
```

## 🔥 Common Scan Combinations

```
# Quick network sweep
```

## ⚡ Useful One-Liners

```
# Find live hosts and save to file
```

## 📊 Understanding Port States

open

Application actively accepting connections

closed

Port accessible but no application listening

filtered

Firewall blocking, can't determine state

unfiltered

Accessible, but open/closed unknown (ACK scan)

open|filtered

Open or filtered, can't determine (UDP)

closed|filtered

Closed or filtered, can't determine

## 📚 Additional Resources

- [Official Nmap Manual](https://nmap.org/book/man.html) — Complete command reference
- [NSE Script Documentation](https://nmap.org/nsedoc/) — All available scripts
- [Nmap Network Scanning Book](https://nmap.org/book/) — Free online book by Fyodor
- [Nmap GitHub Repository](https://github.com/nmap/nmap) — Source code and issues