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
