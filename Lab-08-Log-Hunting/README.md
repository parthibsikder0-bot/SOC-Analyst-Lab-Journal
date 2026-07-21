# Lab 08: Log Hunting and Parsing (`grep` & `awk`)

## Objective
Simulate a log analysis workflow to identify an SSH brute-force attack and extract the threat actor's IP address from system authentication logs.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `grep`, `awk`, `cat`

---

## Execution Steps

### 1. Simulating Log Data
Generated a mock `/var/log/auth.log` file containing standard authentication traffic mixed with a simulated SSH brute-force attack originating from an external IP address.

### 2. Hunting for Anomalies
Leveraged `grep` to filter the log file for anomalous authentication events. Executed `grep "Failed" auth.log` to instantly discard legitimate logins and isolate the malicious brute-force attempts.

### 3. Extracting Indicators of Compromise (IoCs)
Utilized command piping (`|`) to feed the filtered output directly into `awk` for data extraction. Executed `grep "Failed" auth.log | awk '{print $11}'` to isolate the 11th column of the log format, successfully extracting the attacker's IP address (`10.10.10.99`) for future firewall blocking.

## Key Takeaway
Manual log review is inefficient during an active incident. Chaining command-line text processing tools like `grep` and `awk` allows analysts to rapidly filter massive datasets and extract actionable Indicators of Compromise (IoCs).
