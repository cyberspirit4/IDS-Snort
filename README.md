# 🛡️ Custom Snort IDS Rules Deployment

A collection of custom lightweight Snort Intrusion Detection System (IDS) signatures designed to detect common network reconnaissance, probing, and Denial of Service (DoS) attack patterns. 

This repository provides the signatures, integration steps, and verification procedures to deploy these rules in a live monitoring environment.

---

## 🔍 Rule Signatures & Logic

The custom signature suite consists of three rules:

| SID | Alert Message | Protocol | Target | Detection Mechanism |
| :--- | :--- | :--- | :--- | :--- |
| *1000001* | ICMP Ping Detected | ICMP | any ➔ any | Triggers on an Echo Request (itype:8). Indicates standard host discovery probing. |
| *1000002* | NMAP SYN Scan | TCP | any ➔ any | Matches packets with only the SYN flag set (flags:S). Detects stealth port scanning. |
| *1000003* | TCP SYN Flood Detected | TCP | any ➔ port 80 | Tracks incoming traffic to HTTP. Triggers if >100 SYN packets arrive at a single destination within 10 seconds. |
