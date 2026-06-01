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

The email contained the following verification link:

http://paypal-secure-login.ru/verify

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
