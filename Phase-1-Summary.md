# Phase 1 Executive Summary: Security Operations & Fundamentals (Labs 01 - 10)

## Overview
This phase establishes a comprehensive foundation in Linux system administration, security operations, and incident response. The completed labs demonstrate a practical progression from setting up secure environments to actively hunting threats and neutralizing them at the network perimeter.

---

## Skill Progression Breakdown

### I. System Administration & Version Control (Labs 01 - 06)
* **Environment Configuration:** Deployed and secured a Kali Linux virtual environment for offensive and defensive operations.
* **Identity & Access Management:** Audited user groups, modified file permissions (`chmod`, `chown`), and enforced principle of least privilege.
* **Version Control:** Established a professional Git workflow to document and push technical writeups to a centralized repository.

### II. Threat Hunting & Persistence Auditing (Lab 07)
* **Adversary Emulation:** Engineered a bash-based beacon script to simulate Command and Control (C2) communication.
* **Persistence Mechanisms:** Manipulated the Linux `cron` daemon to automate malicious execution.
* **Defensive Auditing:** Executed a live hunt using `crontab` to identify and eradicate unauthorized scheduled tasks.

### III. Network Visibility & Data Extraction (Labs 08 - 09)
* **Log Parsing:** Chained Linux text-processing utilities (`grep`, `awk`) to filter massive authentication logs and extract malicious IP addresses from a simulated SSH brute-force attack.
* **Packet Analysis:** Deployed `tcpdump` for raw network traffic capture and utilized Wireshark to dissect PCAP files.
* **Credential Harvesting:** Identified unencrypted HTTP authentication attempts and decoded Base64 payloads to recover compromised cleartext credentials.

### IV. Active Defense & Remediation (Lab 10)
* **Firewall Configuration:** Translated threat intelligence (IoCs) into actionable network defense.
* **Traffic Filtering:** Authored and implemented custom `iptables` rules to actively drop inbound traffic from identified malicious infrastructure, securing the system perimeter.

---
**Status:** Phase 1 Complete. 
**Next Objective:** Phase 2 - Endpoint Threat Hunting (Process Auditing & File Integrity).
