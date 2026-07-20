# Lab 02: Network Reconnaissance & Port Scanning

## Objective
Conduct external network reconnaissance to identify exposed services and verify local host perimeter security.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `nmap`

---

## Execution Steps

### 1. Localhost Perimeter Baseline
Executed a standard scan against the local loopback address to verify no unauthorized listening ports were exposed.
`nmap localhost`
**Result:** Verified 100% of the top 1,000 TCP ports are closed/filtered. The local perimeter is secure.

### 2. Live Target Reconnaissance (Unoptimized)
Initiated a default scan against an authorized external testing target (`scanme.nmap.org`). The scan experienced significant delays due to packet retransmission caps and network rate-limiting.

### 3. Live Target Reconnaissance (Optimized)
Force-quit the slow scan and re-initiated an aggressive, fast-mode scan to bypass network delays:
`nmap -F -T4 scanme.nmap.org`
* `-F`: Restricted the scan to the top 100 most common ports.
* `-T4`: Applied aggressive timing to speed up packet transmission.

---

## Findings: scanme.nmap.org

The optimized scan completed in **5.66 seconds** and successfully mapped the attack surface, identifying two open entry points:

1. **Port 22/tcp (ssh):** Open. Remote administrative access point.
2. **Port 80/tcp (http):** Open. Unencrypted web server traffic.
3. **Filtered/Closed:** 98 ports were identified as closed or filtered by a firewall.

## Key Takeaway
Network reconnaissance requires balancing thoroughness with speed. Blindly running tools can lead to massive delays, but understanding tool flags (like timing and port ranges) allows an analyst to bypass network friction and map an attack surface in seconds.
