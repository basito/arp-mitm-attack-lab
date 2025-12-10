# 🔐 ARP Spoofing & MITM Traffic Interception (Cyber Security Project)

This project demonstrates how an attacker inside a local network can perform an **ARP Spoofing attack** to position themselves as a **Man-in-the-Middle (MITM)** and intercept unencrypted HTTP traffic. The goal is to understand LAN-based attack vectors and highlight the importance of encryption and network-level defenses.

---

## 📌 Project Overview

- **Attacker:** Kali Linux VM (`192.168.0.105`)
- **Victim:** Windows Host OS (`192.168.0.101`)
- **Gateway/Router:** `192.168.0.1`
- **Interface Used:** `eth0`
- **Tools:** `arpspoof`, `Wireshark`

The attacker successfully intercepted HTTP credentials submitted by the victim through a test login page, proving the effectiveness of MITM attacks on unsecured networks.

---
🔍Findings & Results

The ARP spoofing attack successfully redirected the victim’s traffic through the attacker machine. Using Wireshark, I was able to view full HTTP requests and responses in clear text, including login credentials submitted on an unsecured page. The results showed how easily sensitive information can be exposed on a shared network when encryption is not enforced

To prevent ARP spoofing and MITM attacks, networks and applications must enforce strong security controls. The most important defense is using HTTPS for all sensitive communication so intercepted packets remain unreadable. Network protections can also detect or block ARP poisoning attempts.

Recommended Fixes:

Enforce HTTPS + HSTS for all login and data pages

Enable Dynamic ARP Inspection (DAI) / DHCP Snooping

Use Secure and HttpOnly cookies

Avoid sending credentials over HTTP

Use a VPN on untrusted networks

Segment internal networks to limit attacker movement

## 🧩 Commands Used

```bash
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

sudo arpspoof -i eth0 -t 192.168.0.101 192.168.0.1
sudo arpspoof -i eth0 -t 192.168.0.1 192.168.0.101

'

