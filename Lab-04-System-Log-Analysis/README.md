# Lab 04: System Log Analysis & Threat Hunting

## Objective
Simulate a local SSH brute-force attack and utilize modern Linux logging utilities to parse system databases and extract Indicators of Compromise (IoCs).

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `systemctl`, `ssh`, `journalctl`, `grep`

---

## Execution Steps

### 1. Service Vulnerability Simulation
By default, the Kali Linux perimeter is secured with all external listening services disabled. To simulate an attack surface, the SSH daemon was manually initialized:
`sudo systemctl start ssh`

### 2. Attack Simulation
A simulated unauthorized access attempt was executed against the local SSH port using a non-existent user credential:
`ssh evilhacker@localhost`
*The connection was intentionally failed via intentional credential mismatch.*

### 3. Log Parsing and Artifact Extraction
Modern Linux distributions utilize `systemd-journald` for centralized logging rather than legacy plain-text files (e.g., `/var/log/auth.log`). The journal database was queried and filtered for the attacker's username:
`sudo journalctl | grep "evilhacker"`

---

## Findings & Event Analysis

The `journalctl` query successfully isolated three distinct event logs mapping the lifecycle of the attack:

1. **User Identification Failure:** `Invalid user evilhacker from ::1 port 38890`
2. **Authentication Rejection:** `Failed password for invalid user evilhacker from ::1 port 38890 ssh2`
3. **Session Termination:** `Connection closed by invalid user evilhacker ::1 port 38890 [preauth]`

## Key Takeaway
Legacy text-based log files are being phased out in modern Linux environments. Security analysts must be proficient in parsing binary logging databases via utilities like `journalctl` to effectively hunt for system anomalies, authentication failures, and brute-force indicators.
