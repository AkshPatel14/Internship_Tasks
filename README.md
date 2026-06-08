# Task 1 - Network Scanning with Nmap

## Objective
Perform basic network reconnaissance using Nmap to discover active hosts,
open ports, and identify potential security risks on a local network.

## Tools Used
- **OS:** Kali Linux
- **Tool:** Nmap 7.99
- **Scan Type:** TCP SYN Scan (-sS), Service Version (-sV), OS Detection (-O)

## Steps Performed
1. Identified local IP range using `ip a` command
2. Ran TCP SYN scan on 192.168.X.0/24
3. Ran detailed scan with service version and OS detection
4. Noted down IP addresses and open ports
5. Researched common services running on open ports
6. Identified potential security risks from open ports

---

## 4. IP Addresses and Open Ports Found

```
IP Address    | Open Ports
--------------|-----------------------------
192.168.X.X   | 23(filtered), 53, 80, 443
192.168.X.Y   | None
192.168.X.Z   | None
192.168.X.A   | None
192.168.X.B   | None (Kali Machine)
```

---

## 6. Common Services Running on Open Ports

```
Port | Service | Description
-----|---------|--------------------------------------------------
23   | Telnet  | Remote terminal. Sends all data in plaintext.
     |         | Older protocol, replaced by SSH.
-----|---------|--------------------------------------------------
53   | DNS     | Domain Name System. Translates domain names to
     |         | IP addresses. Running PowerDNS Recursor 4.8.8
-----|---------|--------------------------------------------------
80   | HTTP    | Web server / Router admin panel. Plaintext
     |         | traffic. Used to access router settings page.
-----|---------|--------------------------------------------------
443  | HTTPS   | Encrypted version of HTTP. Secure router admin
     |         | panel. Uses SSL/TLS encryption.
```

---

## 7. Potential Security Risks from Open Ports

```
Port | Service | Risk Level | Risk Description
-----|---------|------------|--------------------------------------------------
23   | Telnet  | HIGH       | Plaintext protocol. Passwords visible in
     |         |            | network traffic. Should be fully disabled.
     |         |            | State=filtered means firewall blocking it
     |         |            | but port still exists on router.
-----|---------|------------|--------------------------------------------------
53   | DNS     | MEDIUM     | PowerDNS 4.8.8 exposed on LAN. If
     |         |            | misconfigured, can be used for DNS
     |         |            | amplification attacks. Should not be
     |         |            | accessible from outside network.
-----|---------|------------|--------------------------------------------------
80   | HTTP    | MEDIUM     | Router admin panel on plaintext HTTP.
     |         |            | Anyone on LAN can access. No encryption
     |         |            | means credentials sent in plaintext.
     |         |            | Weak password = full router takeover.
-----|---------|------------|--------------------------------------------------
443  | HTTPS   | LOW        | Encrypted admin panel. Safer than port 80.
     |         |            | Risk only if weak password or outdated
     |         |            | SSL certificate used.
```

---

## Outcome
- Learned basic network reconnaissance using Nmap
- Understood network service exposure on local network
- Identified potential security risks from open ports
- Gained hands-on experience with TCP SYN scanning

# Task 2: Phishing Email Analysis

## Overview

The objective was to analyze a phishing email sample and identify common phishing indicators used by attackers to deceive users into revealing sensitive information.

## Objective

To identify phishing characteristics in a suspicious email sample by examining:

* Sender email address
* Email headers
* Embedded links
* Language and content
* Authentication records (SPF, DKIM, DMARC)

## Tools Used

* Sample phishing email (text format)
* Online Email Header Analyzer

## Methodology

### 1. Sender Address Analysis

The sender address was examined for domain spoofing and typosquatting.

**Suspicious Sender:**
[security@paypa1-alerts.com](mailto:security@paypa1-alerts.com)

**Legitimate Domain:**
paypal.com

**Finding:**
The attacker replaced the letter **"l"** with the number **"1"** in "paypa1", a common phishing technique known as typosquatting.

### 2. Email Header Analysis

The email headers were analyzed using an online header analysis tool.

**Findings:**

* SPF Authentication Failed
* DKIM Authentication Failed
* DMARC Authentication Failed
* SPF Alignment Failed
* DKIM Alignment Failed

These failures indicate that the email was not sent from an authorized PayPal mail server.

### 3. Suspicious Link Identification

The email contained verification link:

**Findings:**

* Domain is not owned by PayPal.
* Uses a misleading domain name.
* Uses the **.ru** top-level domain.
* Attempts to impersonate a legitimate PayPal login page.

### 4. Urgent and Threatening Language

The email attempted to create panic and pressure the recipient into acting quickly.

Examples:

* "Your account will be permanently suspended within 24 hours."
* "Verify your identity immediately."
* "Loss of all your funds."

Such urgency is a common social engineering tactic.

### 5. URL Mismatch Check

Phishing emails often display legitimate-looking text while redirecting users to malicious websites.

**Finding:**
The email referenced PayPal but linked users to a completely different domain, indicating a phishing attempt.

### 6. Grammar and Content Review

Several writing issues were identified:

* "confirm your informations" (incorrect grammar)
* Generic greeting: "Dear Valued Customer"
* Copyright year displayed as 2024 while the email date was 2026

These inconsistencies are common indicators of fraudulent emails.

## Phishing Indicators Identified

1. Spoofed sender domain (paypa1-alerts.com)
2. Reply-To address mismatch
3. SPF authentication failure
4. DKIM authentication failure
5. DMARC authentication failure
6. Suspicious originating IP address
7. Malicious verification link
8. Fake PayPal impersonation
9. Urgency and fear-based language
10. Generic greeting
11. Grammar mistakes
12. Incorrect copyright information

## Conclusion

The analyzed email exhibits multiple characteristics of a phishing attack. By examining the sender information, email headers, embedded URLs, language patterns, and authentication records, the email was determined to be fraudulent. This exercise improved understanding of phishing tactics and strengthened email threat analysis skills.

## Learning Outcome

* Understanding of phishing techniques
* Ability to analyze email headers
* Identification of spoofed domains
* Recognition of malicious URLs
* Awareness of social engineering tactics
* Improved email security analysis skills
* 
# Task 3 - Basic Vulnerability Scan Using Nessus Essentials

## Objective
The objective of this task was to perform a basic vulnerability assessment on a local machine using Nessus Essentials and identify potential security risks, vulnerabilities, and recommended mitigations.

## Tool Used
- Nessus Essentials
- Ubuntu Linux
- Web Browser (for Nessus interface)

## Scan Configuration

### Target
- Local Machine (localhost / local IP address)

### Scan Type
- Basic Network Scan

### Vulnerability Scanner
- Nessus Essentials

## Procedure

1. Installed Nessus Essentials on Ubuntu.
2. Started the Nessus service.
3. Accessed the Nessus web interface through the browser.
4. Created a new scan policy using Basic Network Scan.
5. Configured the target as the local machine.
6. Launched the vulnerability scan.
7. Waited for the scan to complete.
8. Reviewed identified vulnerabilities and their severity levels.
9. Documented findings and recommended mitigations.
10. Captured screenshots of scan results.

## Vulnerability Severity Levels

Nessus categorizes vulnerabilities into:

- Critical
- High
- Medium
- Low
- Informational

These ratings help prioritize remediation efforts.

## Key Concepts Learned

- Vulnerability Scanning
- Risk Assessment
- CVSS (Common Vulnerability Scoring System)
- Vulnerability Management
- Security Hardening
- Remediation Planning

## Outcome

Successfully performed a vulnerability scan using Nessus Essentials, analyzed the results, understood vulnerability severity ratings, and learned basic vulnerability management practices.

# Task 4: Setup and Use a Firewall on Linux Using UFW
## Objective

The objective of this task is to configure and test basic firewall rules using UFW (Uncomplicated Firewall) on Ubuntu Linux. The task demonstrates how to allow and block network traffic, verify firewall functionality, and understand how firewalls improve system security.

## Tools Used
Ubuntu Linux
UFW (Uncomplicated Firewall)
Telnet (for testing blocked ports)
Terminal
## Task Overview
## Step 1: Check Firewall Status

Verified the current status of the UFW firewall.

sudo ufw status verbose
## Step 2: Enable UFW Firewall

Activated the firewall service.

sudo ufw enable

Verified status:

sudo ufw status numbered
## Step 3: Block Inbound Traffic on Port 23 (Telnet)

Created a firewall rule to deny incoming Telnet connections.

sudo ufw deny 23/tcp

Reloaded and verified the rule:

sudo ufw reload
sudo ufw status
## Step 4: Test the Firewall Rule

Attempted to connect to port 23 using Telnet.

telnet localhost 23

Result:

Unable to connect to remote host: Connection refused

This confirmed that the firewall successfully blocked Telnet traffic.

## Step 5: Allow SSH Traffic (Port 22)

Configured the firewall to allow SSH connections.

sudo ufw allow 22/tcp

Verified the rule:

sudo ufw status
## Step 6: Remove Test Block Rule

Removed the temporary Telnet blocking rule to restore the original configuration.

sudo ufw status numbered
sudo ufw delete <rule_number>

## Example:

sudo ufw delete 2
sudo ufw delete 3
How Firewall Filters Traffic

A firewall acts as a security gatekeeper between a system and the network. Every incoming or outgoing packet is checked against configured rules.

Traffic Filtering Process
Packet Arrives
       ↓
Check Rules (Top to Bottom)
       ↓
First Matching Rule Found
       ↓
Allow / Deny / Reject
       ↓
No Match → Apply Default Policy

## Rule Components
Direction (Inbound / Outbound)
Protocol (TCP / UDP / ICMP)
Port Number
Source Address
Destination Address
Action (Allow / Deny / Reject)

## Security Benefits
Prevents unauthorized access.
Blocks insecure services such as Telnet.
Reduces attack surface by closing unnecessary ports.
Controls inbound and outbound traffic.
Provides an additional layer of security.

## Results
UFW firewall was successfully enabled.
Inbound Telnet traffic on port 23 was blocked.
SSH access on port 22 was allowed.
Firewall rules were verified and tested successfully.
Temporary test rules were removed after validation.

## Conclusion
This task demonstrated the practical implementation of firewall security using UFW on Ubuntu Linux. By creating, testing, and removing firewall rules, the functionality of packet filtering and access control was verified. Firewalls are a critical component of network security and help protect systems from unauthorized access and malicious traffic.

# Task 5 - Capture and Analyze Network Traffic Using Wireshark

## Objective
Capture live network packets on Kali Linux using Wireshark, generate traffic using standard tools, and analyze captured packets to identify protocols and traffic types.

## Tools Used
- **Wireshark** – Packet capture and analysis
- **Kali Linux** – Operating system (VirtualBox)
- **Interface** – eth0
- **Traffic Generators** – ping, curl, nslookup

## Steps Performed

1. Opened Wireshark and started live capture on `eth0`
2. Generated traffic using:
```bash
   ping -c 10 8.8.8.8
   curl http://example.com
   nslookup google.com
```
3. Stopped capture after traffic generation (180 packets total)
4. Applied display filters: `http`, `dns`, `tcp`, `icmp`
5. Analyzed packets for each protocol
6. Exported capture as `.pcap` file

## Protocols Identified

| Protocol | Port/Type | Packets | Observation |
|----------|-----------|---------|-------------|
| HTTP | TCP Port 80 | 2 (1.1%) | GET request to example.com, 200 OK response |
| DNS | UDP Port 53 | 8 (4.4%) | A/AAAA queries for example.com and google.com |
| TCP | Port 51056→80 | 14 (7.8%) | Full 3-way handshake (SYN, SYN-ACK, ACK) + FIN teardown |
| ICMP | Type 8/0 | 20 (11.1%) | 10 ping requests + 10 replies to 8.8.8.8, TTL=117 |

## Key Findings

- **HTTP** – Unencrypted traffic; method, host, and response fully visible in plaintext
- **DNS** – Every connection triggers a DNS lookup before data flows; runs unencrypted by default
- **TCP** – Three-way handshake clearly captured; reliable delivery confirmed via ACK flags
- **ICMP** – 0% packet loss on all 10 pings; TTL=117 indicates ~7 network hops to 8.8.8.8

## Files
- `task5.docx` – Detailed analysis report with screenshots

# Task 6 - Password Strength Evaluation

## Objective
Understand what makes a password strong by creating passwords with varying complexity and testing them using an online password strength checker.

---

## Tool Used
- **Bitwarden Password Strength Tester** — https://bitwarden.com/password-strength/

---

## Passwords Tested

| Password | Strength | Crack Time | Character Types |
|----------|----------|------------|-----------------|
| `1234567890` | 🔴 Very Weak | Less Than A Second | Digits only |
| `Bddfgs@1235` | 🟢 Good | 1 Month | Upper + Lower + Digits + Symbol |
| `Ahkgjjhv@1432676` | 🔵 Strong | Centuries | Upper + Lower + Digits + Symbol |

---

## Key Observations

- **Length** is the single biggest factor in password strength
- Adding **uppercase + symbols** jumps crack time from seconds → months
- 16-char mixed password = centuries to crack vs <1 second for numeric-only
- Sequential/numeric passwords (`1234567890`) appear in every wordlist — cracked instantly

---

## Common Password Attacks

**Brute Force** — tries every character combination; defeated by long passwords  
**Dictionary Attack** — uses wordlists of common passwords; defeated by random non-word strings  
**Credential Stuffing** — reuses leaked credentials; defeated by unique password per account  

---

## Best Practices Learned

- Use **minimum 12–16 characters**
- Mix **uppercase, lowercase, numbers, special characters**
- Avoid sequential patterns (`1234`, `abcd`, `qwerty`)
- Avoid personal info (name, DOB, phone)
- **Unique password** for every account
- Use a **password manager** (Bitwarden, KeePass)
- Enable **MFA/2FA** wherever available
- Passphrases work well: `Horse-Lamp-River-42!`

---

## Screenshots

**Password 1 — Very Weak (`1234567890`)**  
![Very Weak](screenshots/6_1.png)

**Password 2 — Good (`Bddfgs@1235`)**  
![Good](screenshots/6_2.png)

**Password 3 — Strong (`Ahkgjjhv@1432676`)**  
![Strong](screenshots/6_3.png)

---

## Conclusion

Password complexity directly determines resistance to attack. A numeric-only password is cracked in under a second. A 16-char mixed-type password would take centuries. Length + character diversity = strong password. Use a password manager to generate and store them.
