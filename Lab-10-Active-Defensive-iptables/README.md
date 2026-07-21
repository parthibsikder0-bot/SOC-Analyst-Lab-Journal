# Lab 10: Active Defense and Firewall Configuration (`iptables`)

## Objective
Translate threat intelligence (identified malicious IP addresses) into actionable active defense measures by configuring host-based firewall rules to drop malicious traffic.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `iptables`

---

## Execution Steps

### 1. Firewall Audit
Audited the existing host-based firewall configurations using `sudo iptables -L -v -n` to establish a baseline of current traffic filtering rules.

### 2. Rule Implementation
Implemented a custom firewall rule targeting a known malicious IP address identified during previous log analysis (Lab 08). Executed `sudo iptables -A INPUT -s 10.10.10.99 -j DROP` to append a rule to the INPUT chain that silently discards all inbound traffic from the threat actor.

### 3. Verification
Re-audited the firewall chains to verify successful rule injection and ensure active defense measures were properly applied to the system's network interface.

## Key Takeaway
Identifying a threat is only the first step in incident response. Analysts must be capable of rapidly translating Indicators of Compromise (IoCs) into active defense mechanisms, such as firewall rules, to neutralize active threats and secure the perimeter.
