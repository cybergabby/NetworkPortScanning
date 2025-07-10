# 🔎 Network Port Scanning & Reconnaissance Guide

Welcome to my comprehensive guide on **Network Port Scanning and Enumeration** for ethical hacking, penetration testing, and bug bounty reconnaissance.

This project aims to document common techniques, tools, scripts, and knowledge needed to perform effective reconnaissance against networks.  

---

## 📌 Table of Contents

- [Overview](#overview)
- [Why Port Scanning Matters](#why-port-scanning-matters)
- [Popular Scanning Tools](#popular-scanning-tools)
- [TCP vs UDP](#tcp-vs-udp)
- [What to Look for During Scanning](#what-to-look-for-during-scanning)
- [Common Ports and Services](#common-ports-and-services)
- [Banner Grabbing](#banner-grabbing)
- [Example Nmap Commands](#example-nmap-commands)
- [Post-Scanning Actions](#post-scanning-actions)
- [Resources](#resources)

---

## 📖 Overview

Port scanning is a crucial first step in the reconnaissance phase of a network penetration test. It allows you to:

- Discover live hosts
- Identify open ports and services
- Gather version info for vulnerability research
- Understand the target’s attack surface

---

## ❓ Why Port Scanning Matters

Knowing which services are exposed gives attackers (or ethical hackers) the initial foothold. This information leads to:

- Vulnerability matching (e.g., outdated SSH or SMB)
- Password brute-forcing (e.g., FTP, Telnet)
- Misconfiguration discovery
- Exploitation entry points

---

## 🛠️ Popular Scanning Tools

| Tool    | Description                          |
|---------|--------------------------------------|
| `nmap`  | The most popular and powerful scanner |
| `masscan` | Extremely fast network scanner     |
| `netcat` | Manual port checking & banner grabbing |
| `RustScan` | Fast port scanner written in Rust |
| `zmap`    | Internet-wide port scanning        |

---

## 🔄 TCP vs UDP

| Protocol | Use Case | Notes |
|----------|----------|-------|
| **TCP**  | Reliable, connection-based | Easier to detect and scan |
| **UDP**  | Connectionless, used in DNS, SNMP, etc. | Slower and stealthier, often filtered |

Use `-sU` in Nmap for UDP scanning.

---

## 👀 What to Look for During Scanning

When ports are discovered, check for:

| What to Look For         | Why It Matters                            |
|--------------------------|--------------------------------------------|
| Service Version          | Can be vulnerable (e.g., vsFTPd 2.3.4)     |
| Default Credentials      | Services like Telnet, FTP, SSH             |
| Outdated Protocols       | SSLv2, SSLv3, TLS 1.0                      |
| Anonymous Access         | FTP, SMB, RDP                              |
| Misconfigurations        | Open MongoDB, Redis, Elasticsearch         |
| Custom Ports             | Might host admin panels, dev tools         |

---

## 🔌 Common Ports and Services

| Port | Service       | Recon Value                  |
|------|---------------|------------------------------|
| 21   | FTP           | Test for anonymous login     |
| 22   | SSH           | Brute force, version check   |
| 23   | Telnet        | Insecure login, banner grab  |
| 25   | SMTP          | Mail server enumeration      |
| 53   | DNS           | Zone transfers, subdomains   |
| 80   | HTTP          | Web app scanning             |
| 139/445 | SMB/NetBIOS| File share, EternalBlue vuln |
| 3306 | MySQL         | Default creds, misconfig     |
| 3389 | RDP           | Remote access, brute-force   |

---

## 🪪 Banner Grabbing

Banner grabbing is used to identify the service version on an open port. This can be done using:

```bash
# Using Netcat
nc -nv 192.168.0.1 21

# Using Telnet
telnet 192.168.0.1 80

# With Nmap
nmap -sV -p 21,22,80,443 192.168.0.1
```

🧪 **Example Nmap Commands**
# Fast scan of top 1000 TCP ports
nmap -T4 -F 192.168.0.1

# Full TCP port scan with service detection
nmap -sS -sV -p- 192.168.0.1

# Scan + aggressive detection (OS, traceroute, scripts)
nmap -A 192.168.0.1

# UDP scan (slow!)
nmap -sU -p 53,161,123 192.168.0.1

# Script scan on FTP
nmap -p 21 --script=ftp* 192.168.0.1


🎯 Post-Scanning Actions

Once ports are discovered, follow up with:

    📂 Enumeration tools (e.g., enum4linux, smbclient, nikto)

    🔍 Exploit research (search for CVEs)

    🗝️ Brute-force attacks (hydra, medusa, patator, nmap)

    🧬 Vulnerability scanning (nuclei, Metasploit, OpenVAS)

    🧠 Manual testing (e.g., login panels, hidden directories)


📚 Resources

    Nmap Reference Guide

    GTFOBins (for post-exploitation)

    PayloadAllTheThings

    HackTricks

    Exploit Database

🚀 About

This repository was created as part of my learning and practice in network penetration testing. You can follow me on:

    GitHub: @cybergabby

    Medium: @gabbytech01

    X (Twitter): @Gabriel_coder01



