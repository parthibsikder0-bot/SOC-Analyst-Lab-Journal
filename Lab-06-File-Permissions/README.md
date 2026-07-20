# Lab 06: File Permissions & Privilege Escalation

## Objective
Identify and remediate file permission vulnerabilities that could lead to system compromise and privilege escalation.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `ls`, `chmod`, `echo`

---

## Execution Steps

### 1. Simulating the Vulnerability
Created a mock sensitive configuration file (`sys_backup.conf`) containing simulated credentials. A misconfiguration was intentionally introduced using `chmod 777`, granting global Read, Write, and Execute permissions (`-rwxrwxrwx`).

### 2. Identifying the Risk
Confirmed the vulnerability using `ls -l`. In a real-world scenario, an attacker with low-level access could read this file to steal the admin password, leading to full system compromise (Privilege Escalation).

### 3. Remediating the Vulnerability
Applied the **Principle of Least Privilege** by restricting access. Executed `chmod 600 sys_backup.conf` to strip all permissions from the public and user groups, leaving only Read and Write access for the file owner (`-rw-------`).

## Key Takeaway
Misconfigured file permissions are a primary vector for privilege escalation. Understanding the numerical and symbolic mapping of Linux permissions (Read/Write/Execute) is critical for locking down sensitive data and auditing system security.
